---
Conference: ECS24
Date: 15.05.2024 15:00
Speaker: Paolo Pialorsi
Type: Personal Notes
---

# Architecting and building end-to-end Microsoft 365 Solutions

## Architecting and Building M365 solutions

### Single-tenant vs multi-tenant solutions

Single tenant solution

- building a solution for your company
- or a custom, tailr-mad solution fo ra single customer
- will not be reuse on any other tenants
- one deployment / hosting infrastructure (no need for data isolation, data security)

Multi tenant

- you plan to reues the same app across multiple customers / tenants
- you plan to sell a services via SaaS model
- one dployment / hosting infrastructure (with data isolation and security)

### Isolating content for multi-tenancy

- Content: Files, Items, Settings
- Consider using SPO for documents and getting the data via MS Graph

Isolating data for multi-tenancy:

- For relational data:

  - one DB for each customer
  - unique DB with partitioned data (by `TenantId`)

- For No-SQL data
  - one Cosmos DB for each customer
  - unique Cosmos DB wieth one container for each tenant (👉ind the service limits)

You will need a configuuation repository with settings about all the tnenants.
If you need to support _Search capabilitiies_, consider using Microsoft Azure AI Search

### Data privacy and security

- Encrypt data at rest (symmetric key to encrypt, asymmetric keys to protect data keys)
- use different keys for different customers / tenant swhen in multi-tenant scenario
- rely on Azure Key Vault to store, manage and rotate keys

### REST APIs

- implement a back-end of REST APIs (reusable in mutliple scenario); ✋ no direct access to the APIs of the implmeented services!
- support OpenAPI with your APIS (consider using Kiota to geneerate fluent client libraries)
- provide governance APIs, not only functional APIs

### Building UI components / layers

Pro Code:

- SharePoint Online: Web Parts, Extensions
  - Microsoft Teams: Tabs, Bots, Messaging Extensions
- Microsoft Viva Connections: Adaptive Card Extensions (ACEs)

Low Code:

- Microsoft Power Apps
- Microsoft Copilot: Plugins or Graph Connectors as well as Custom Copilots wit Microsoft Copilot Studio
- Rely on reusable UI components (Graph Toolkit, PnP React Reusable Components)

### M365 extensibility points of attention

Teams Message Extensions:

- to extend the Search experience
- to imporve the message composition experience
- to easily extend M365 Chat

### Supporting Multiple environments

- Microsoft Azure deployment slotes for web apps ore Azure functions, ...
- mulitple Entra ID appplication registration (for DEV, TEST, PROD)
- maintainable list of allowed tenants for DEV, TEST, PROD
- shared secure storage (Azure Key Vault) with security keays / certs / credentials

### Running background processe

- quick background processes: Azure Function Apps, Containers
- for long running processes: Azure Logic Apps

### Asynchronous processing

Defining back-end APIs and services:

- Azure Functions in Azure Function Apps are one of the best options (easily work on schedule, can be executed upon triggers, can be easily monitored and instrumented)
- consider creating Azure Logic Apps (more low-code oriented approach or if you need to run long-running processes)

Rely on asynchronous communication channels: Azure Blob Queue (quick and dirty), Azure Services Bus (scales better than the Blob queue)

### Authentication and Authorization

- Register one Entra ID application for every environment (keep into account the consent flow, especially in multi-tenant apps); mind permission updates during solution lifecycle (👉 additaional consents required)
- Rely on OAuth 2.0 for authorization (👉 think carefully about delegated vs Application permission)
- Use the On-Behalf-Of flow to securely access back-end APIs / Services on behalf of a user
- in case of the need of external identity providers, consider using AAD B2C (👉 mind MS Graph and M365 APIs permission limits for external users)

### Security across services and architectural layers

Single tenant solution

- Rely on Azure Managd Identities for crosss-services securitya
- Creds of Managed Identities are managed, rotated and protected by Azure
- no one can access the credetials (the global Admin neigher – you don't need an longer to rely on passwords, secrets, ...)

Multi tenant solution

- Rely on OAuth 2.0

### Managing Settings
Application Settings

- Single tenant: consider using Azure Settings (App Service, Function Apps, Logic Apps, ..), store settings with Azure Key Vault
- Multi-tenant: rely on a config repository
  – SPO solution: consider using Tenant Settings

User Settings

- consider using a per-tenant configuration repository
- or rely on OD4B and the applications's personal folder (you can store any file, including JSON settings or other stuff; use MS Graph to read / write / manage user's settings)


## Some thoughts on Governance
### Logging, monitoring, backups
- At least use Application Insights for monitoring an logging; consider using Azure Log Analytics 8for quering and alyzing log data, for creating charts on log data
- Consider using Azure Monitor (alerts, Auto scale, dashboards, Power BI integration)
- provide PoSh / CLI command line management toolsl or scripts
- provide reporting for monitoring and measuring usage
- rely as much as you can cn bloud-based services for backup / restore


