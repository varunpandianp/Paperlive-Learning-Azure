
# Azure Fundamentals – Overview

**Course:** Paperlive Learning – Microsoft Azure  
**Session Date:** 02-11-2026  
**Session:** 01  
**Topic:** Azure Fundamentals and Core Architecture Components

---

## 1. Class Overview

In this session, we explored Microsoft Azure fundamentals and its core architecture components.

### Topics Covered

- Overview of Microsoft Azure
- Azure Core Architecture
- Azure Regions
- Availability Zones
- Azure Resources
- Resource Groups
- Azure Resource Manager (ARM)
- Azure Subscriptions
- Azure Management Groups

---

## 2. What is Microsoft Azure?

Microsoft Azure is a cloud computing platform provided by Microsoft.

It provides cloud services to build, deploy, manage and scale applications through Microsoft's global data center infrastructure.

Instead of purchasing and maintaining physical servers, organizations can use Azure to access computing resources over the internet.

### Examples of Azure Services

- Compute: Azure Virtual Machines
- Networking: Azure Virtual Network
- Storage: Azure Blob Storage
- Database: Azure SQL Database
- Containers: Azure Kubernetes Service (AKS)
- Identity: Microsoft Entra ID
- Monitoring: Azure Monitor

### Benefits of Azure

- Scalability
- High Availability
- Global Infrastructure
- Security
- Disaster Recovery
- Pay-as-you-go Pricing
- Resource Management

---

## 3. Azure Core Architecture

Azure infrastructure is organized using a hierarchy.

The main components are:

1. Management Groups
2. Subscriptions
3. Resource Groups
4. Resources

### Azure Resource Hierarchy

```text
Microsoft Entra ID Tenant
          |
          v
    Management Groups
          |
          v
      Subscriptions
          |
          v
     Resource Groups
          |
          v
       Resources
          |
    +-----+------+
    |     |      |
   VM    VNet   Storage
```

Each component has a different responsibility.

---

## 4. What is an Azure Region?

An Azure Region is a geographical area containing one or more Azure data centers connected through a dedicated, low-latency network.

Microsoft operates Azure Regions across different geographical locations around the world.

### Examples of Azure Regions

- Central India
- South India
- West India
- East US
- West Europe
- Southeast Asia

### Why do we use Regions?

1. To deploy resources closer to users.
2. To reduce network latency.
3. To meet data residency and compliance requirements.
4. To support disaster recovery.
5. To improve application availability through geographical distribution.

### Example

Suppose an application serves users in India.

Deploying application infrastructure in Central India or South India can help reduce latency for Indian users.

**Important:** Not every Azure service is available in every region.

---

## 5. What is an Availability Zone?

An Availability Zone (AZ) is a physically separate location within an Azure Region.

Each Availability Zone has independent infrastructure, including:

- Power
- Cooling
- Networking
- Data center facilities

Availability Zones help protect applications against failures affecting an individual zone.

### Example

Consider an Azure Region with three Availability Zones.

```text
          Azure Region
          Central India
               |
       +-------+-------+
       |       |       |
       v       v       v
     AZ 1    AZ 2    AZ 3
       |       |       |
      VM1     VM2     VM3
```

If AZ 1 experiences a failure, workloads deployed across other zones may continue operating.

### Why use Availability Zones?

- High Availability
- Fault Tolerance
- Reduced downtime
- Application resilience
- Protection against zone-level failures

### Region vs Availability Zone

| Region | Availability Zone |
|---|---|
| Geographical area | Physically separate location within a region |
| Contains one or more data centers | Contains one or more data centers |
| Used for geographical deployment | Used for zone-level resiliency |
| Example: Central India | Example: Zone 1, Zone 2, Zone 3 |

**Remember:**
Region = Geographical location.

Availability Zone = Isolated infrastructure location within a region.

---

## 6. What is an Azure Resource?

An Azure Resource is an individual service or infrastructure component that you create and manage in Azure.

### Examples

| Azure Resource | Purpose |
|---|---|
| Virtual Machine | Compute |
| Virtual Network | Networking |
| Network Security Group | Network security |
| Storage Account | Storage |
| Azure SQL Database | Database |
| Public IP Address | Internet connectivity |
| Load Balancer | Traffic distribution |

### Example

When we create a Virtual Machine in Azure, that VM is an Azure Resource.

Similarly, when we create a VNet, it is another Azure Resource.

---

## 7. What is an Azure Resource Group?

A Resource Group is a logical container used to organize and manage related Azure resources.

Instead of managing every resource separately, we can group resources belonging to the same application, project or environment.

### Example

Suppose we deploy an E-commerce application.

It requires:

- Virtual Machine
- Virtual Network
- Network Security Group
- Public IP
- Storage Account
- Azure SQL Database

We can organize these resources inside one Resource Group.

```text
Azure Subscription
       |
       v
Resource Group: rg-ecommerce-dev
       |
       +---- Virtual Machine
       |
       +---- Virtual Network
       |
       +---- Network Security Group
       |
       +---- Public IP
       |
       +---- Storage Account
       |
       +---- Azure SQL Database
```

### Why do we use Resource Groups?

1. Resource Organization
2. Centralized Resource Management
3. Access Management using Azure RBAC
4. Cost Organization using Tags and Cost Management
5. Resource Lifecycle Management

### Resource Group Naming Examples

```text
rg-webapp-dev
rg-webapp-test
rg-webapp-prod
rg-database-prod
rg-network-prod
```

### Important Concept: Resource Group Location

When creating a Resource Group, Azure asks us to select a region.

Why?

The Resource Group has a location where its metadata is stored.

However, the Resource Group can contain resources deployed in different Azure regions, subject to individual service restrictions.

Example:

```text
Resource Group: rg-ecommerce-prod
Location: Central India

Resources:

VM             -> Central India
Azure SQL      -> South India
Storage        -> West India
```

**Remember:**

Resource Group Location != Resource Deployment Location.

### Resource Group Deletion

When we delete a Resource Group, Azure normally deletes the resources inside it as well.

Therefore, always verify the resources before deleting a Resource Group.

---

## 8. What is Azure Resource Manager (ARM)?

ARM stands for Azure Resource Manager.

It is the management and deployment service of Microsoft Azure.

ARM provides a unified management layer to create, update, manage and delete Azure resources.

Whenever we create resources using:

- Azure Portal
- Azure CLI
- Azure PowerShell
- Terraform
- ARM Templates

The management requests are processed through Azure Resource Manager APIs.

### ARM Architecture

```text
       Cloud Engineer
             |
     +-------+-------+
     |       |       |
   Portal   CLI   PowerShell
     |       |       |
     +-------+-------+
             |
             v
    Azure Resource Manager
             |
    +--------+---------+
    |        |         |
  RBAC    Policies   Validation
             |
             v
      Resource Providers
             |
      +------+------+------+
      |      |      |      |
      VM    VNet  Storage  SQL
```

### Responsibilities of ARM

1. Resource Deployment
2. Resource Management
3. Access Control Integration
4. Azure Policy Enforcement
5. Resource Group Management
6. Dependency Management
7. Infrastructure as Code Support

### ARM and Resource Group Relationship

ARM directly manages Resource Groups.

Example:

When we create a Resource Group through Azure Portal or CLI:

1. Azure CLI sends a request to ARM.
2. ARM processes the request.
3. ARM creates the Resource Group under the subscription.
4. We can deploy resources into that Resource Group.

**Remember:**

ARM = Management Layer.

Resource Group = Logical Container.

Resources = Actual Azure Services.

---

## 9. What is an ARM Template?

An ARM Template is a JSON-based Infrastructure as Code (IaC) file.

It defines the Azure infrastructure that needs to be deployed.

Instead of manually creating resources through the portal, we can define infrastructure in a JSON template.

Example use cases:

- Create Virtual Machines.
- Create Virtual Networks.
- Create Storage Accounts.
- Deploy multiple resources together.

### ARM Template vs Terraform

| ARM Template | Terraform |
|---|---|
| Uses JSON | Uses HCL |
| Azure-native IaC | Multi-cloud IaC |
| Primarily for Azure | Supports AWS, Azure, GCP |
| Uses Azure Resource Manager APIs | Uses cloud provider APIs |

Important: Terraform does not replace ARM. Terraform communicates with Azure management APIs to deploy and manage Azure infrastructure.

---

## 10. What is an Azure Subscription?

An Azure Subscription is a logical management and billing boundary used to provision and manage Azure resources.

When we create an Azure resource, it must be associated with a subscription.

### Why do we use Subscriptions?

1. Billing Management
2. Resource Organization
3. Access Control
4. Resource Quotas and Limits
5. Environment Separation
6. Cost Management

### Example

An organization can create separate subscriptions for different environments.

```text
Microsoft Entra ID Tenant
          |
          +----------------------+
          |                      |
          v                      v
    Dev Subscription       Prod Subscription
          |                      |
          v                      v
    Resource Groups        Resource Groups
          |                      |
          v                      v
    Azure Resources        Azure Resources
```

### Subscription Example

```text
Subscription: Ecommerce-Development

Resource Groups:
    rg-webapp-dev
    rg-database-dev
    rg-network-dev
```

Another subscription:

```text
Subscription: Ecommerce-Production

Resource Groups:
    rg-webapp-prod
    rg-database-prod
    rg-network-prod
```

This separation helps organizations manage development and production environments independently.

---

## 11. What is Azure Management Group?

A Management Group is a container used to organize multiple Azure subscriptions.

It allows organizations to apply governance, policies and access controls across multiple subscriptions.

### Why do we use Management Groups?

1. Organize multiple subscriptions.
2. Apply Azure Policies at a higher level.
3. Manage access using Azure RBAC.
4. Maintain governance across the organization.
5. Manage subscriptions centrally.

### Example

Imagine an organization has multiple departments.

```text
          Management Group
             Company
                |
       +--------+--------+
       |                 |
       v                 v
   Development         Production
   Management          Management
      Group               Group
       |                   |
   +---+---+           +---+---+
   |       |           |       |
   v       v           v       v
 Dev-01  Dev-02      Prod-01 Prod-02
 Subscription        Subscription
```

Each subscription can contain multiple Resource Groups, and each Resource Group can contain multiple resources.

### Azure Management Hierarchy

```text
       Microsoft Entra ID Tenant
                  |
                  v
          Management Groups
                  |
                  v
             Subscriptions
                  |
                  v
            Resource Groups
                  |
                  v
               Resources
```

**Important:** Management Groups help manage subscriptions at an organizational level.

---

## 12. AWS vs Azure Comparison

Since we are learning Multi-Cloud, understanding equivalent concepts is important.

| Microsoft Azure | AWS Equivalent / Closest Concept |
|---|---|
| Azure Region | AWS Region |
| Availability Zone | Availability Zone |
| Azure Resource | AWS Resource |
| Resource Group | AWS Resource Groups (closest equivalent) |
| Azure Subscription | AWS Account |
| Management Group | AWS Organizations / Organizational Units |
| Azure Resource Manager | AWS management APIs / Control Plane |
| ARM Template | AWS CloudFormation |
| Azure RBAC | AWS IAM |
| Azure Tags | AWS Resource Tags |

### Important Difference

Azure Resource Groups are fundamental resource-management containers.

AWS does not require resources to belong to an AWS Resource Group. AWS uses resource tags and optional Resource Groups to organize supported resources.

---

## 13. Important Interview Questions

### Q1. What is Microsoft Azure?

Microsoft Azure is a cloud computing platform provided by Microsoft that offers computing, networking, storage, databases and other cloud services.

### Q2. What is an Azure Region?

An Azure Region is a geographical area containing one or more data centers connected through a dedicated network.

### Q3. What is an Availability Zone?

An Availability Zone is a physically separate location within an Azure Region that provides isolation and improves application availability.

### Q4. What is an Azure Resource?

An Azure Resource is an individual infrastructure component or service created in Azure, such as a VM, VNet or Storage Account.

### Q5. What is a Resource Group?

A Resource Group is a logical container used to organize and manage related Azure resources.

### Q6. Can one Resource Group contain resources from different regions?

Yes. A Resource Group can contain resources deployed in different Azure regions, subject to service-specific restrictions.

### Q7. What is Azure Resource Manager?

Azure Resource Manager is the deployment and management service that provides a unified management layer for Azure resources.

### Q8. What is an Azure Subscription?

An Azure Subscription is a logical boundary for resource provisioning, billing and access management.

### Q9. What is a Management Group?

A Management Group is a container used to organize multiple subscriptions and apply governance and access controls across them.

### Q10. What happens when we delete a Resource Group?

Deleting a Resource Group normally deletes all resources contained within it.

---

## 14. Quick Revision

| Concept | One-Line Definition |
|---|---|
| Azure | Microsoft's Cloud Computing Platform |
| Region | Geographical area containing Azure data centers |
| Availability Zone | Physically separate location within a region |
| Resource | Individual Azure service or infrastructure component |
| Resource Group | Logical container for related resources |
| ARM | Azure deployment and management service |
| ARM Template | JSON-based infrastructure definition |
| Subscription | Billing and resource management boundary |
| Management Group | Organizes multiple Azure subscriptions |

### Key Takeaways

- Azure provides cloud infrastructure through a global network of regions.
- Availability Zones improve application resiliency.
- Azure Resources represent actual cloud services.
- Resource Groups organize related resources.
- ARM manages resource deployment and lifecycle.
- Subscriptions provide billing and management boundaries.
- Management Groups organize subscriptions and support governance.

---

## 15. Learning Progress

- [ ] Understand Azure Global Infrastructure
- [ ] Understand Regions and Availability Zones
- [ ] Understand Azure Resources
- [ ] Understand Resource Groups
- [ ] Understand Azure Resource Manager
- [ ] Understand ARM Templates
- [ ] Understand Azure Subscriptions
- [ ] Understand Management Groups
- [ ] Compare Azure Architecture with AWS

---

**Next Session:** Continue with the next topic covered in Paperlive Learning Azure classes.

**Learning Method:** Understand Concepts → Hands-on Practice → Document Notes → Interview Preparation.
