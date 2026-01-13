🎯 Goal

Access Azure Blob Storage from local PC using:

✔ Private Endpoint (Private Link)

✔ Point-to-Site VPN

✔ Private DNS

✔ Azure Portal UI only

🧱 Final Architecture
Local PC (On-prem)
   ↓ P2S VPN
Azure VNet
   ↓
Private Endpoint
   ↓
Azure Blob Storage

STEP 1️⃣ Create Virtual Network

Azure Portal → Virtual Networks → Create

Basics

Resource Group: storage-rg

Name: storage-vnet

Region: same as storage account

IP Addresses

Address space: 10.20.0.0/16

Subnet:

Name: default

Range: 10.20.1.0/24

✔ Create

STEP 2️⃣ Create Storage Account (Blob)

Azure Portal → Storage accounts → Create

Basics

Name: mystorage123

Region: same as VNet

Performance: Standard

Networking (IMPORTANT)

Connectivity method: Private endpoint

Public network access: Disabled

Private endpoint:

VNet: storage-vnet

Subnet: default

Target sub-resource: blob

✔ Create

STEP 3️⃣ Verify Private Endpoint

Open Storage account

Go to Networking → Private endpoint connections

✔ Status should be Approved

STEP 4️⃣ Create Private DNS Zone (Required)
4.1 Create DNS Zone

Azure Portal → Private DNS zones → Create

Name:

privatelink.blob.core.windows.net

4.2 Link DNS Zone to VNet

Open DNS zone

Virtual network links → Add

Select:

VNet: storage-vnet

Auto-registration: ❌ No

✔ Save

4.3 Verify A Record

Inside DNS zone:

You should see an A record

mystorage123 → 10.20.x.x

STEP 5️⃣ Create Gateway Subnet

Open storage-vnet

Go to Subnets → + Gateway subnet

CIDR:

10.20.255.0/27


✔ Save

STEP 6️⃣ Create Point-to-Site VPN Gateway

Azure Portal → Virtual network gateways → Create

Basics

Name: storage-vpn-gw

Gateway type: VPN

VPN type: Route-based

SKU: VpnGw1

VNet: storage-vnet

Public IP: Create new

✔ Create (⏳ ~30 mins)

STEP 7️⃣ Configure Point-to-Site VPN (Azure AD Auth)

Open storage-vpn-gw

Go to Point-to-site configuration

Click Configure now

Settings

Address pool:

172.16.10.0/24


Tunnel type: OpenVPN (SSL)

Authentication: Azure Active Directory

Azure AD Values

Tenant:

https://login.microsoftonline.com/<tenant-id>


Audience:

41b23e61-6c1e-4545-b367-cd054e0ed4b4


Issuer:

https://sts.windows.net/<tenant-id>/

##### if Azure VPN Gateway does NOT push DNS settings 
C:\Windows\System32\drivers\etc\hosts

10.20.1.4 mystorage123vinayak.blob.core.windows.net



✔ Save

STEP 8️⃣ Download & Connect VPN (Local PC)

In VPN Gateway → Download VPN client

Install client

Connect using Azure AD login

✔ Status: Connected

STEP 9️⃣ Test Private DNS from Local PC

Open PowerShell / Terminal:

nslookup mystorage123.blob.core.windows.net


✔ Expected:

Address: 10.20.x.x


❌ If public IP → DNS not linked correctly

STEP 🔟 Access Blob Storage from Local PC
Option A: Azure Storage Explorer (Recommended)

Install Azure Storage Explorer

Sign in with Azure AD

Open:

mystorage123 → Blob Containers


✔ Works only when VPN is connected

Option B: Browser Test (Proof)

Open:

https://mystorage123.blob.core.windows.net


✔ Loads (only with VPN)


