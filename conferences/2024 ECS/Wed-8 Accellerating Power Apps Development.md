---
Conference: ECS24
Date: 16.05.2024 15:50
Speaker: Gilles Pommier
Type: Personal Notes
Categories: Microsoft 365
---

# Accellerating Power Apps Development with Automated Testing

## Automated Testing

The baseline for automated testing is to have a solution.
Reasons for automated testing are repetitive testing tasks, functionality tests with high business impacts, features thate are stable and not undergoing sgnificant changes, features taht require multiple data sets, manual testing that takes significant time and effort.

## Test Studio

Test Studio – which is an app that works for the moment only with Canvas Apps – can be opened from the Canvas App Studio.

You define:

- test steps: several expressions
  Manipulation an majority of - test cases: cares are made up of as eries of instructions or actions
- test suites: group multiple test cases
- test assertions

![Wed-8.1.png](assets/Wed-8.1.png)

You can also record your test cases; this is nice for an outline of the tests along the discussions with the stakeholders.
Keep in mind that you always have to publish the app before running the tests.

### Known limitations

Not working on:

- Components
- Neyted galleries
- Media controls
- person-type columns

Upon the limitations, Test Studio is fairly slow.

## Test Engine

Test Engine is an open [source github project](https://github.com/microsoft/PowerApps-TestEngine).
It will create a local executable that you can use to run test, using the power Fx language. It currently only runs on Canvas app.
Under the hood, test engine uses **Playwright** to orchestrate the tests.

Just clone the GH repo and build it locally:

```powershell
# Clone GitHub repo
git clone https://github.com/microsoft/PowerApps-TestEngine.git

# Change to the PowerAppsTestEngine folder
cd PowerApps-TestEngine\src\PowerAppsTestEngine

# Build
dotnet build

# Install browsers required by Playwright
.\bin\Debug\PowerAppsTestEngine\playwright.ps1 install
```

### How to use it

What to do next:

1. Author your own test plan in Test Studio and download the created YAML file afterwards.
2. Import the yml file
3. Run the test
