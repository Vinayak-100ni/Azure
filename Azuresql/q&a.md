```md
# Azure SQL Interview Questions & Answers

Azure SQL is a managed cloud-based database service by Microsoft that provides scalable, secure, and high-performance database solutions. It eliminates the need for hardware management and offers built-in capabilities like automated backups, high availability, and advanced security.

---

# 🟢 Basic Azure SQL Interview Questions

### 1. What is Azure SQL Database?
Azure SQL Database is a fully managed relational database service in the cloud. It provides built-in high availability, security, and automated backups without requiring hardware management.

---

### 2. How does Azure SQL differ from SQL Server?
- Azure SQL: Cloud-based, automated backups, scaling, managed service  
- SQL Server: On-premises, manual setup required  

---

### 3. What are DTUs?
DTU (Database Transaction Unit) is a blended measure of CPU, memory, and I/O used to estimate database performance.

---

### 4. What is an SQL Pool in Azure?
SQL Pool is part of Azure Synapse Analytics used for querying large datasets using distributed computing.

---

### 5. What is Geo-replication?
Geo-replication creates readable secondary databases in different regions for disaster recovery and load balancing.

---

### 6. What is Azure SQL Data Sync?
It synchronizes data across multiple Azure SQL and on-prem databases for hybrid applications.

---

### 7. How does Azure SQL scale?
- Vertical scaling → Increase DTUs/vCores  
- Horizontal scaling → Sharding (splitting data)

---

### 8. What is an Elastic Pool?
A cost-effective solution where multiple databases share a pool of resources.

---

### 9. What is TDE (Transparent Data Encryption)?
Encrypts data at rest automatically without requiring application changes.

---

### 10. What are Failover Groups?
Provide high availability by automatically switching to a secondary database during failures.

---

# 🟡 Intermediate Azure SQL Interview Questions

### 1. What is Azure SQL Managed Instance?
A fully managed SQL Server instance in Azure with near 100% compatibility, including features like stored procedures, triggers, and views.

---

### 2. How do you migrate data to Azure SQL?
Common tools:
- Data Migration Assistant (DMA)
- Azure Data Factory
- Bulk Copy Program (BCP)

---

### 3. What is Azure Synapse Analytics?
Formerly Azure SQL Data Warehouse, it combines big data analytics and data warehousing.

---

### 4. Explain Elastic Pools in detail
- Multiple databases share resources
- Cost-efficient for unpredictable workloads
- Configurable min/max limits per DB

---

### 5. How do you secure Azure SQL?
- Firewalls (IP restrictions)
- Virtual Network Endpoints
- Azure Active Directory Authentication
- TDE encryption

---

### 6. What are Azure SQL limitations?
- Size limits per pricing tier
- Limited SQL Server features (e.g., SQL Agent)
- Restricted cross-database queries

---

### 7. What is Azure SQL Database Advisor?
A performance tuning tool that uses ML to recommend:
- Index creation/removal
- Query optimization

---

# 🔴 Advanced Azure SQL Interview Questions

### 1. What is Point-in-Time Restore?
Allows restoring a database to a specific timestamp using automated backups.

---

### 2. What is Columnstore Index?
- Stores data in columns instead of rows
- Improves performance for analytical queries
- Ideal for data warehousing

---

### 3. How is Azure Active Directory used?
- Authentication & authorization
- Single Sign-On (SSO)
- Multi-factor authentication
- Role-based access control (RBAC)

---

### 4. How do automated backups work?
- Automatically scheduled
- Configurable retention policies
- Geo-redundant backup support

---

### 5. What is Resource Governor (Managed Instance)?
Controls CPU, memory, and I/O allocation for workloads to prevent resource monopolization.

---

### 6. How to optimize query performance?
- Analyze execution plans
- Optimize indexes
- Use Query Store
- Monitor with Azure tools

---

### 7. Role of Azure Automation?
Automates tasks like:
- Backups
- Scaling
- Maintenance using Runbooks (PowerShell/Python)

---

# 🟣 Scenario-based Azure SQL Interview Questions

### 1. Handling traffic spikes
- Enable auto-scaling
- Monitor DTUs
- Optimize queries

---

### 2. High latency troubleshooting
- Check query plans
- Analyze DTU usage
- Optimize indexing

---

### 3. Migrating large databases
- Use DMA
- Choose correct pricing tier
- Use BCP/Data Factory
- Test in staging

---

### 4. Slow database troubleshooting
- Identify bottlenecks
- Optimize queries
- Scale resources
- Check locking/blocking

---

### 5. High availability & disaster recovery
- Geo-replication
- Failover groups
- Geo-redundant backups

---

### 6. Handling security threats
- Enable Advanced Threat Protection
- Use data masking
- Restrict access via firewall
- Enable MFA

---

# ✅ Conclusion

Azure SQL provides:
- Easy scalability
- Built-in security
- High availability
- Automated management

It is an ideal solution for modern cloud-based applications requiring reliability, performance, and minimal operational overhead.

---
```

---

