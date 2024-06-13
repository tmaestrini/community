# Introduction to Git Flow

Reference: [https://github.com/kasuken/git-flow-cheatsheet](https://github.com/kasuken/git-flow-cheatsheet) by Emanuele Bartolesi (2023)

## Foundations of Git
### Overview
GitFlow is a workflow that defines a strict branching structure and a set of rules for merging changes between branches. It is based on two main branches: main and develop.

- **main**: This branch contains the _production-ready_ code. It is updated only when a new release is ready to be deployed.
- **develop**: This branch contains the _latest features and bug fixes_ that are being worked on. It is updated regularly by merging feature branches into it.

In addition to these two main branches, GitFlow uses four types of supporting branches: **feature**, **release**, **hotfix** and **support**.

<table>
  <tr>
    <td valign="top"><strong>Feature</strong></td>
    <td>These branches are created from develop and merged back into develop when a feature is completed. They are used to implement new functionality or enhancements. They have names like feature/xxx, where xxx is a descriptive name of the feature.</td>
    <td>Develop → Feature → Develop</td>
  </tr>
  <tr>
    <td valign="top"><strong>Release</strong></td>
    <td>These branches are created from develop and merged into main and develop when a release is ready to be deployed. They are used to prepare the code for production, such as fixing bugs, updating documentation, and changing configuration. They have names like <code>release/x.y.z</code>, where <code>x.y.z</code> is the version number of the release.</td>
    <td>Develop → Release → Develop & Main</td>
  </tr>
  <tr>
    <td valign="top"><strong>Hotfix</strong></td>
    <td>These branches are created from main and merged into main and develop when a critical bug needs to be fixed in production. They are used to patch the code without affecting the ongoing development. They have names like <code>hotfix/x.y.z</code>, where <code>x.y.z</code> is the version number of the hotfix.</td>
    <td>Main → Hotfix → Develop & Main</td>
  </tr>
</table>

We will not cover the **support** flow / branch in these topic.


### Commands
The following commands are examples of how to use GitFlow. You can also use a graphical tool or a plugin to manage GitFlow.

#### Initialize GitFlow
To start using GitFlow, you need to initialize it in your repository. This will create the main and develop branches and set some configuration options.

```
git flow init
```
You can use the `-d` option to accept the default branch names.

#### Start a feature branch
To start working on a new feature, you need to create a feature branch from `develop`.
```
git flow feature start <name>
```
This will create a branch called `feature/name` and switch to it.

#### Finish a feature branch
When you are done with your feature, you need to merge it back into `develop` and delete the feature branch.
```
git flow feature finish <name>
```
This will merge `feature/name` into `develop`, switch to `develop`, and delete `feature/name`.

#### Start a release branch
When you are ready to prepare a new release, you need to create a release branch from ``develop``.
```
git flow release start <version>
```
This will create a branch called `release/version` and switch to it.

#### Finish a release branch
When you have finished testing and fixing your release, you need to merge it into main and `develop` and tag it with the version number.
```
git flow release finish <version>
```
This will merge `release/version` into main and `develop`, switch to main, tag it with, switch back to `develop`, and delete ``release/version``.

Important: if you want to tag the release directly from the command, add the parameter `-m` at the end of the command.

```
git flow release finish <version> -m <yourtag>
```

#### Start a hotfix branch
When you need to fix a critical bug in production, you need to create a hotfix branch from main.
```
git flow hotfix start <version>
```
This will create a branch called `hotfix/version` and switch to it.

#### Finish a hotfix branch
When you have fixed the bug, you need to merge it into main and develop and tag it with the version number.
```
git flow hotfix finish <version>
```
This will merge `hotfix/version` into main and develop, switch to main, tag it with, switch back to develop, and delete `hotfix/version`.

