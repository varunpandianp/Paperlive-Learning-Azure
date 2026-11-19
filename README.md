

> **Track:** 02 – Microsoft Azure Cloud  
> **Curriculum level:** Associate-Level Curriculum  


## Course Overview

This repository documents my learning journey through the **Microsoft Azure Cloud** track offered by Paperlive Learning. It is organized around the 10 modules in the course curriculum.

The curriculum covers Azure fundamentals, Microsoft Entra ID, compute, networking, storage, PaaS container services, data services, application management and security, backup and monitoring, and Azure DevOps.

## Learning Progress

Use the checkboxes to track each topic as it is covered in class and practiced.

- [ ] Module 1 – Getting Started with Microsoft Azure
- [ ] Module 2 – Exploring Microsoft Entra ID
- [ ] Module 3 – Navigate the Compute Services on the Microsoft Azure Platform
- [ ] Module 4 – Azure Networking Services
- [ ] Module 5 – Getting Started with the Azure Storage Services
- [ ] Module 6 – PaaS Container Services on Microsoft Azure
- [ ] Module 7 – Working with the Azure Data Platform
- [ ] Module 8 – Application Management and Security
- [ ] Module 9 – Backup and Monitoring
- [ ] Module 10 – Azure DevOps

---

## Module 1: Getting Started with Microsoft Azure

- [ ] Overview of cloud computing
- [ ] Explore Microsoft Azure
- [ ] IaaS and PaaS services provided by Microsoft Azure
- [ ] Demonstrating the working of the Azure Portal
- [ ] Usage and understanding of Azure Command Line Interface (CLI)
- [ ] Working with Azure PowerShell

## Module 2: Exploring Microsoft Entra ID

- [ ] Introduction to Microsoft Entra ID
- [ ] Compare the difference between Windows AD and Azure AD
- [ ] Identity and access management in Azure
- [ ] Users
- [ ] Group creation
- [ ] Azure AD domains
- [ ] Microsoft Entra tenant
- [ ] Authentication options
- [ ] Azure AD Connect
- [ ] Self-service password reset (SSPR)
- [ ] Microsoft Entra Multi-factor authentication (MFA)
- [ ] Different Multi-factor Authentication verification methods
- [ ] Azure Resources
- [ ] Subscription
- [ ] Management Group
- [ ] Conditional Policies

## Module 3: Navigate the Compute Services on the Microsoft Azure Platform

- [ ] Navigating to the Azure virtual machines
- [ ] Data disks in Azure
- [ ] Azure VMs and Interfaces
- [ ] Examine the ways to create a virtual hard disk template
- [ ] Creating and launching the Custom images of Azure VM
- [ ] Virtual machine scale sets
- [ ] Availability sets
- [ ] Availability zones
- [ ] Resource Locks
- [ ] Resource Tags
- [ ] IIS role
- [ ] NSG
- [ ] RBAC Roles
- [ ] Azure Policies

## Module 4: Azure Networking Services

### Part 1

- [ ] Overview of Azure virtual networks
- [ ] Azure VNet component
- [ ] Public and Private IPs
- [ ] Azure VNet subnets
- [ ] Manage the Azure network interface cards (NIC)
- [ ] Network Security Group (NSG)
- [ ] Routing
- [ ] Managing Route tables
- [ ] Service tags
- [ ] Azure DNS
- [ ] Manage and resolve the Private DNS

### Part 2

- [ ] Hub and Spoke Topology
- [ ] VNet Peering
- [ ] VPN – Site-to-Site
- [ ] Point-to-Site
- [ ] Express Route
- [ ] Azure Bastion
- [ ] Azure load balancers
- [ ] Azure Firewall Configuration

### Part 3

- [ ] Application gateway configuration
- [ ] Application Security Groups
- [ ] Azure Front Door service
- [ ] Azure Traffic Manager
- [ ] Network Watcher

## Module 5: Getting Started with the Azure Storage Services

- [ ] Azure Storage Account
- [ ] Azure Blob Storage
- [ ] Replication Strategies
- [ ] Azure Table Storage
- [ ] Azure Queue Storage
- [ ] Azure File Storage
- [ ] Azure File Sync
- [ ] Azure Storage Explorer
- [ ] Azure shared access signature (SAS)
- [ ] Azure Databox and its use cases
- [ ] Azure Import/Export service
- [ ] Azure Content Delivery Network Profile with Endpoints
- [ ] ARM Templates

## Module 6: PaaS Container Services on Microsoft Azure

- [ ] Containerized web apps on Windows and Linux
- [ ] App Service Plan
- [ ] Networking for an App Service and its deployment types
- [ ] Deployment slots by using the Azure Portal
- [ ] Azure Container Instance
- [ ] Building and pushing the container images to the Azure Container Registry
- [ ] Azure Kubernetes Service
- [ ] Azure Function App
- [ ] Azure Logic App

## Module 7: Working with the Azure Data Platform

- [ ] Overview of the SQL Databases
- [ ] Azure SQL
- [ ] Elastic Pools
- [ ] Configuration
- [ ] Achieve elastic scale in Azure SQL Database
- [ ] Cosmos DB
- [ ] Multiple APIs and data models
- [ ] Request units
- [ ] Request Unit calculator
- [ ] Partition key
- [ ] Cross-partition queries
- [ ] Replication and consistency levels in Microsoft Azure
- [ ] Triggers
- [ ] User-Defined Functions

## Module 8: Application Management and Security

- [ ] Azure Key Vault
- [ ] Automated Azure AD managed identities in Microsoft Entra ID
- [ ] Azure AD application management

## Module 9: Backup and Monitoring

- [ ] Recovery Services vault
- [ ] Backup of Azure virtual machines
- [ ] VM backup policies
- [ ] Restore Azure virtual machines
- [ ] Azure Monitor
- [ ] Azure metric
- [ ] Log Analytics workspace
- [ ] Creating alerts and actions
- [ ] Application Insights using the Azure Monitor

## Module 10: Azure DevOps

- [ ] Understanding Azure DevOps concepts
- [ ] Azure Boards
- [ ] Azure Repos
- [ ] Azure Pipelines
- [ ] Deploying web applications using Azure Pipelines

---

## Session Learning Log

Create one entry for each class/session. Keep notes, commands, configuration steps, screenshots (where useful), and troubleshooting findings in the relevant module folder.

### Session Template

```markdown
# Session: <session number>

- **Date:**
- **Module:**
- **Topics covered:**

## Concepts learned

## Azure services covered

## Commands and configuration

## Practical work / demonstration

## Errors and troubleshooting

## Interview questions and answers

## Key takeaways

## Next session / pending topics
```

## Suggested Repository Organization

```text
paperlive-learning-azure/
├── README.md
├── 01-azure-fundamentals/
├── 02-microsoft-entra-id/
├── 03-azure-compute/
├── 04-azure-networking/
│   ├── part-1/
│   ├── part-2/
│   └── part-3/
├── 05-azure-storage/
├── 06-azure-paas-containers/
├── 07-azure-data-platform/
├── 08-application-management-security/
├── 09-backup-monitoring/
├── 10-azure-devops/
└── learning-logs/
```

*The folders are an organizational suggestion. Add notes, lab files, scripts, and screenshots as the corresponding sessions progress.*

## Learning Goal

Build a structured record of the Paperlive Learning Azure curriculum, including class notes, practical work, command references, troubleshooting, and interview preparation.

---

**Learning approach:** Understand the concept → practice in Azure → document the steps → record troubleshooting → review interview questions.

**Important:** Check Azure resource usage and clean up lab resources after practice to avoid unnecessary charges. Never commit passwords, access keys, connection strings, service-principal secrets, or other credentials to this repository.
"""

out = Path("/mnt/data/README.md")
pypandoc.convert_text(readme, "md", format="md", outputfile=str(out), extra_args=["--standalone"])
print(f"Created: {out}")
print(f"Size: {out.stat().st_size} bytes")
