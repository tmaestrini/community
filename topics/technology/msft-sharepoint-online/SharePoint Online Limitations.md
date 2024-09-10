# SharePoint Online – Service limitations and boundaries

Reference: [Linkedin Post](https://www.linkedin.com/posts/ami-diamond-mvp-70a798b_sharepoint-office365-microsoft365-activity-7235199542466367488-aisE/) by Ami Diamond (08/2024)

> [!TIP]
> Service boundaries and limits are subject to change. Therefore, this overview should be considered carefully.<br>
> 👉 Check the [official resource documentation](https://learn.microsoft.com/en-us/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits) as well as [Restrictions and limitations in OneDrive and SharePoint](https://support.microsoft.com/en-us/office/restrictions-and-limitations-in-onedrive-and-sharepoint-64883a5d-228e-48f5-b3d2-eb39e07630fa).

## SharePoint limits (general)

- Total storage per organization: 1 TB plus 10 GB per license purchased
- Max storage per site (site collection); 25 TB
- Sites (site collections) per organization: 2 million (Not including the OneDrive created for each licensed user)
- Number of licensed users?: 1 - 500'000

## Sites

- Subsites: 2'000 per site (site collection). We recommend creating sites and organizing them into hubs instead of creating subsites.
- Hub Sites: Your organization is limited to 2'000 hub sites.

## Lists and libraries

- Items in lists and libraries: 30 million <br>
  👉 Having more than 100'000 items, you can't break permissions inheritance on the list, library, or folder anymore.
- Lists and libraries: 2'000 lists and libraries combined per site collection (including main site and any subsites).
- Unique security scopes per list or library: The supported limit of unique permissions for items in a list or library is 50'000. <br>
  👉 However, the recommended general limit is 5'000.
- Versions: 50'000 major versions and 511 minor versions.

## Files and folders

### File size and file path length

- Individual file uploaded: 250 GB
- File attached to a list item: 250 MB
- Max. decoded file path including the file name: Can't contain more than 400 characters (OneDrive and SharePoint).
- For each segment of the path in OneDrive Sync: 255 characters due to operating system limitations.

### Invalid characters
- Characters that aren't allowed in file and folder names: `" * # % : < > ? / \ |` <br/>
  👉 The chars `#` and `%` can be allowed by a Tenant Administrator

### File handling across sites

#### Syncing

- Max. amount of files across the tenant: No more than 300'000 files across all libraries.
- Max. length of the OneDrive root folder (e.g. C:\users\meganb\OneDrive - Contoso) + the relative path of the file (up to 400 chars) cannot be more than 520 characters (on MacOS and Windows).

#### Moving & copying

- Total file size: No more than 100 GB total file size.
- Max. amount of files: No more than 30'000 files.
- File size limits: 2 GB limit for OneNote files; 15 GB file size limit for **cross-geo copy or move**.

## Users & groups

- Users: 2 million per site collection

### SharePoint groups

- Max. amout of groups per site: you can have up to 10'000 groups per site (site collection).
- Max. amount of groups per user: a user can belong to 5'000 groups per site (site collection)
- Users per group: each group can have up to 5'000 users.

## Account synchronization

- Max. amount of synced OneDrive accounts: `1` home account and `9` work or school accounts
