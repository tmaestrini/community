---
Conference: ECS24
Date: 16.05.2024 09:00
Speaker: Peter Schmidt (@petsch / https://www.linkedin.com/in/petsch)
Type: Personal Notes
Categories: Microsoft 365
---

# Mastering a Tenant-to-tenant migration

## Why Tenant Migration

Often, migrations are business driven; companies and their tenants get merged, aquired or rebranded.
Microsoft has described a couple of tenant-to-tenant scenarios in their migration guides; the approach differs in the fact what should be achieved:

- Single-event Migration:<br>
  ⊕ less complex («over night»), minimal tranisition<br>
  ⊖ higher risk, not easy when migrating large amount of data, needs mor planning and testing as well as more IT resoureces during the migration itself
- phased migration:<br>
  ⊕ less risk no alternatives in large environments, easier to execute<br>
  ⊖ more complex (in terms of planning and doing), difficult as process, co-existing tenants, often time consuming

## Tenant Migration Scenarios

The general Process: Discovery — Planning — Design — Testing — Migration — Hypercare — Post Migration

Consider these migration decisions:
| Destination tenant | Migration type |
|:----------------|:-----------------------------|
| New environment | Single-event Migration |
| Existing environment | Phased Migration / Co-Existence (balance the risk and business deadlines) |

**Always do assessment with the aim to know your users and data** (spend some time to "dive into" all the [old] data). ANY migration project is time consuming – you can only loose time, and not saving time when not cleaining up the data to be migrated.

### Planning

A good plan is the key to success. Always put into consideration to identifiy these workloads:

- Microsoft Entra (MFA, App Registrations)
- Exchange Online
- OneDrive for Business
- SharePoint Online
- Teams
- Planner

#### Challenges

Data is often hard to migrate (because data locations are [mostly] not stored within your tenant) from:

- Online Services:
  - Intune, Stream, Microsoft Forms, Viva Engage
  - Azure (Entra ID App Registrations and 3rd Party Apps)
  - Microsoft Information Protection (⚠️ always decrypt data **before** migration – and encrypt afterwords); Encrypted Data, Sensitivity Labels, Retention Policies, DLP Policies, Audit Logs (question: what are you going to do with these)
  - Exchange Online:; Mail Flows (Partner Connectors, specialized mail flows), Meetings (old meetings sill work, existing meetings need to be deleted by users [cannot be recheduled], new meetings will need to be re-created by all users [replacing existing meetings])
  - Teams & SharePoint: External Guests (how do we handle the invited users?)
- Power Platform: Power BI, PowerApps, Power Automate, Dataverse, Dynamics App
- What about on-premises legacy systems
  👉 manual migration processes are necessary regarding these migration sources; consider to check for appropriate tooling support

It's highly recommended that you put migration performance and bandwidth throttling into consideration.

#### Licensing and subscription

To avoid high licensing costs, alwasy ask Microsoft for leveraging licenses in both tenants for a defined period of time.

## The Tenant Migration

### Tooling

Check out these **Microsoft Tools**:

- [Cross-tenant Mailbox Migration (PowerShell)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/cross-tenant-mailbox-migration?view=o365-worldwide)
- Cross-tenant OneDrive Migration
- Cross-tenant SharePoint migration (preview)
- [Cross-tenant Identity Mapping (preview / pulled back; at this time not available yet)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/cross-tenant-identity-mapping?view=o365-worldwide)
- Cross-tenant Domain Sharing (preview)

Put into consideration (highly recommended) to use som 3rd party tools (Quest On-Demand Migration, BitTitan MigrationWiz, ShareGate Migration, Skykick Migration Suite, Avepoint Migration Platform, CodeTwo Office 365 Migration).
Every tool has its own benefits and limitations – know the difference and the limitations!

### Specific questionss

E-Mail migration

- Do we need co-existence?
- Mail flows?
- Calendar federation? (fairly easy)
- Email domain? Moving the email domain has to be one of the last parts of the whole migration process (mail domain is often used in the user principal names)
- MX backup?
- What about Mailboxes, Shared Mailboxes, Rooms and Equipment, Groups, Meetings, Permissions and delegations?

OneDrive and SharePoint

- Data & Versioning (do we really need all versions?)
- checked in documents?
- Issues with user settings

Microsoft Teams

- Can be migrated: Teams files, team chats (conversations, 1:1 chats)

End users

- Communicate to the end users!! Tell them about the plan (how and when will be migrated? How will it affect them? What tasks might be required by them before / after the migration?)<br>
  👉 Find your "plan" how often and how detailed you will inform the users
- Remember all stakeholders in the entire organization

### The journey

Migration is complex. The migration journey always contains:

1. Assessment
1. Planning and (pre-) testing
1. Migration
1. Testing (is essential)
1. Hypercare phase
