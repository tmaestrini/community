---
Conference: ECS24
Date: 15.05.2024 12:00
Speaker: Andreas Krüger (@andikrueger_de)
Type: Personal Notes
Categories: Microsoft 365
---

# Mastering Microsoft 365 Administration: The checklist

Following settings are considered to be checked / validated:

## 1. Entra ID Settings

- dmin Accounts<br>
  👉 Use named accounts or at least know who is (single person) using the account<br>
  👉 Use break glass admin accouts (BGA); they're the last resort to get access to a tnenant. BGA are ecluded from any DA plicies and are only used in case of emergency; create alerts for usage of high privilege accounts<br>
  👉 restrict guest invite settings to moset restrictive setting<br>
  👉 make sure that you have «Terms of use» (properly) set up

- Users Settings<br>
  👉 Use privileged administrative workstations (PWA) for administrative access to Microsoft 365<br>
  👉 enforce MFA for all users<br>
  👉 disable the ability for users to register applicationsy<br>
  👉 restrict guest users access to the most restrictive setting

- CA for Admin Accounts, User Accounts, Zero Trust
  👉 restrict acceess to suggested personas for CA: Internals, Externals, Admins, Developers, Guests, Guest Admins, Services Accounts, Workload Identities

- Applications (Enterprise Apps, App Registrations)<br>
  👉 Document the usage of your application (ownership, lifecycle, description)<br>

## 2. Microsoft 365 Admin Center

- Integrated Apps<br>
  👉 Make sure that you enable only approved apps within the tenant, block any other app and nay future app

- Org Settings<br>
  👉 Disallow these settings: Excahnge Calendar Sharing, User Owned Apps, Bookings, Forms, Graph Data Connect, Microsoft 365 Groups, Modern Authentication, Microsoft 365 Web, Viva Learning, Whiteboard

- Collaboration Settings (SPO, OD4B, Teams)<br>
  👉 Restrict: Sharing Settings, Device Restrictions, App Store, Policies

## 3. Power Platform Settings

  - On-premises Data Gageway
  - Environment Management
  - Self Service Licensing<br>
    👉 Disable the 'trial' experience to the end user by using `Get-AllowedContestPlans` from PowerApps PowerShell
  - Connectors
    👉 consider a Data Loss rpevention policy level to restrict data using

# Slides / Resources
[Tue-3.1.pdf](./assets/Tue-3.1 Mastering Microsoft 365 Administration - the checklist.pdf)