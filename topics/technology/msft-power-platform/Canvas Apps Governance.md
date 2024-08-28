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
[2024 Power Apps Coding Standards For Canvas Apps - Matthew Devaney ](https://www.matthewdevaney.com/power-apps-coding-standards-for-canvas-apps/)

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

## Storing code resources in code repository

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
