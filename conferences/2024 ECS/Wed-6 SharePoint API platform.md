---
Conference: ECS24
Date: 16.05.2024 14:50
Speaker: Bert Jansen
Type: Personal Notes
Categories: SharePoint, Development
---

# SharePoint API platform: what's new and coming

New Scopes:

- `Lists.SelectedOperations.Selected`
- `ListsItems.SelectedOperations.Selected`
- `Files.SelectedOperations.Selected`

## API Updates

Several new API endpoints for Pages API came with the Update of the Microsoft Graph API in April 2024.
More updates are planned.

One important upcoming update is on `Sites.Create.All`, which allows to create sites.
It returns an `HTTP 202: Accepted` plus a `Location` Header.

### Recently shipped API updates

- Multi-Geo discovery
- Sites subscriptions
- List item delta

# Site provisioning

The recommended site provisioning flow to create new sites:

1. Provisioning app has `Site.Create.All` and `Sites.Selected` permissions
2. Create site collection, provisioning app has full control via `Sites.selected`
3. use /permissions enpdpoint to grant another app accesss via `Sites.selected`
4. Remove the provisionings' app permissions

# Remove Event Receiver Retirement
RERs will definitely stop working on April 2, 2026 (in some cases, extended support is provided until Juli 1, 2027).
Instead, use webhooks (as discussed many times), because: Microsoft makes them even better – they will support rich notificaation, ease the "renewal burden".