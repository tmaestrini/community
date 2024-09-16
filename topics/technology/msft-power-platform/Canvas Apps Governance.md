# Canvas Apps – Governance

> [!TIP]
> Guidelines are often very subjective. Therefore, these guidelines should be considered as suggestions.
> Any suggestion may have corresponding counter-arguments. Nevertheless, they should be adhered to as much as possible, so that each contributor is "speaking the same language", based on a common understanding of "HOW" things are to be implemented.

## Canvas application naming convention and description

Each workflow is always named according to the following **naming convention rule**:

Rule: `{Project}` `-` `{unique name of the application}`

Example: _Employee Onboarding - Record mutation_

> [!WARNING]
> Each application must have a description – in understandable words for the customer or end user! The description points out in very general terms what the app does.

## Coding Standards

Every Power Platform Canvas App must always be implemented according to these coding standards:<br>
[2024 Power Apps Coding Standards For Canvas Apps - Matthew Devaney ](https://www.matthewdevaney.com/power-apps-coding-standards-for-canvas-apps/) as well as the [Microsoft Whitepaper: Canvas Apps Coding Guidelines Standards and Guidelines](https://www.microsoft.com/en-us/power-platform/blog/wp-content/uploads/2024/06/PowerApps-canvas-app-coding-standards-and-guidelines.pdf).

### Scope ("minimum standard")

At a minimum, the following areas from the above source are applicable to these standards ("minimum standard"):

- [Naming Conventions](https://www.matthewdevaney.com/power-apps-standards-naming-conventions/)
- [Variable Types](https://www.matthewdevaney.com/power-apps-coding-standards-for-canvas-apps/power-apps-standards-variable-types/)
- [App Settings](https://www.matthewdevaney.com/power-apps-coding-standards-for-canvas-apps/power-apps-standards-app-settings/)
- [Error Handling](https://www.matthewdevaney.com/power-apps-coding-standards-for-canvas-apps/#:~:text=%F0%9F%90%9E-,Error%2DHandling,-Enable%20Formula%2DLevel)

### Verification

The guidelines set forth in the Coding Standards referenced above also apply:

1. Before rolling out a current release, the developer or development team must confirm that all minimum coding standards ("Minimum Standard") from
   the "scope" section above have been met
2. [Reviewing Canvas Apps](https://www.matthewdevaney.com/power-apps-coding-standards-for-canvas-apps/power-apps-standards-reviewing-canvas-apps)

> [!NOTE]
> An appropriate process for user acceptance testing must be implemented by every customer as part of every project.

### General naming conventions
- **Camel case** for **controls and variables**: Camel case begins with a lowercase prefix, removes all spaces from object or variable names, and capitalizes the first letter of each word after the first. <br>
   *Example*: a text input control might be named `txtUserEmailAddress`.
- **Pascal case** for **data sources**: Pascal case is sometimes referred to as “upper camel case.” Like camel case, it removes all spaces AND capitalizes the first letter of words. <br>
   *Example*: a common data source in PowerApps (Microsoft Office 365 Users connector) `Office365Users`.

### Object naming in your app

For all GUI objects that are created in a Canvas Apps, make sure you use consistent naming conventions for:

- **Screens (screen names):** always end the name with Screen
- **Controls (control names):** always begin with a three-character type descriptor of the control
- **Data sources:** always use a “speaking” name that clearly tells the origin of the data (the so called “data source”)

This approach will make your apps easier to maintain, can help improve accessibility, and will the structure and used objects make easier to read.

### Variables and comments

When adding code and comments to a Canvas App, make sure you’re following these two guidelines:

- **Variables:** utilize clever names for variables. If variables are named correctly, you should be able to quickly discern the type and the purpose.
- **Comment:** be sure to heavily comment code fragments within the app. Comments will help you when you return to your application months later.
  - **Line comments:** Use line comments `//` to explain what happens next
  - **Block comments:** Use block comments `/* ... */` to describe a purpose of a code fragment or to (temporarily) disable multiple lines of code while you’re testing or debugging.

### In-app documentation

Always create (at least) one screen to document the following stuff that was used within the app:

- **data collections**
- **variables**

Make sure the screen name is set `App Documentation Screen`.

## Managing source code from apps 

### Release tagging and notes
Every new released version / release candidate of a Power Platform App must be documented in English.
All notable changes to the release should be documented as a simple **changelog** (changelog = contains a curated, chronologically ordered list of notable changes for each version of a project). 

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) and contains these types of changes:

- new features: `Added`
- changes in existing functionality: `Changed`
- removed features: `Removed` 
- bug fixes or code corrections: `Fixed`

The changelog must always contain the release number (version), which adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html). The changelog text starts with:

```text
<release number (version)> – <Release date>

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).
```

### Storing code resources in code repository

Each Power Platform Canvas App must be stored in a code repository, representing the latest state ("latest release candidate") or the latest change. To do this, the solution always must be exported as an _unmanaged soution_.

The source code of each release must be stored as in its according (git) repository.

> [!NOTE]
> In case of storing the source code of the latest release or change is not possible due to time or cost constraints, alternatively the corresponding `.MSAPP` file can directly be stored in the code repository,

Use this resource (by _Tim Leung_) that documents the usage of `Power Platform VS Code Extension` for the necessary steps:
[http://powerappsguide.com/blog/post/new-easier-way-to-pack-unpack-canvas-app-source-code](http://powerappsguide.com/blog/post/new-easier-way-to-pack-unpack-canvas-app-source-code)

The following command unpacks the .msapp file along the document path (`--msapp`) to the destination folder (`--sources`):

```bash
pac canvas unpack --msapp <path to .msapp file (source file)>
--sources <path to destination of source code (destination folder)>.
```

Source: [https://learn.microsoft.com/en-us/power-platform/developer/cli/reference/canvas#pac-canvas-unpack](https://learn.microsoft.com/en-us/power-platform/developer/cli/reference/canvas#pac-canvas-unpack)
