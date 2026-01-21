#### Hub VNet → Central network (shared services)

#### Spoke VNet(s) → Application-specific networks

##### Spokes connect only to the Hub, not to each other (by default)

1. create three networks
   
   (hub, spoke1, spoke2)
   
2. create vpn gateway on hub vnet  [sku vpnGw1]
   
3. peer spoke to hub vnet (inside but spoke vnet setting)
   
    > setting > peering > add
    
        + use the remote virtul  network gateway or route server
   
    - virtual network + hub vnet
      
        + use this virtual network gateway or route server
          
  + add
    
4. now go to routing table configuration as of now both spoke  vnet are still not ping to each other
   
> spoke1 > networking > Effective routes > [in this we can check and confirm that the ip of other vm present in another spoke vnet is not listed here so for that we have to create it manually]

5. for that we can search route tables
   
   > create route table (for both spoke vnet)
   
     name:- spokeTB1 /SpokeTB2
   
     propagte gateway routes : yes
   
6. now go to spokeTB1/spokeTB2
   > Routes
   
     +add
   
      name :- spoke2-traffic-to-hub / spoke1-traffic-to-hub
   
      address prefix...:- IP address
   
      ...:- add the vm spoke2 ip address / add the vm spoke1 ip address
   
         :- virtual network gateway
   
   =add
   
   >subnets
   
     +associate
   
       vnet :- spoke1 / spoke2
   
    subnet :- default

   
7. after this check that routes are added or not in the spoke routes table
    
    > spoke1vm > effective routes 
    
