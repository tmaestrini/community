# Testing SharePoint Framework (SPFx) projects with Jest

Reference: [Blog Post](https://titolivio.eu/2024/04/30/testing-sharepoint-framework-spfx-components-with-jest-and-react-testing-library/) by pH7x Systems (10/2024)

> [!TIP]
> At the time writing this article, I've recently had to update an [existing sample]() from the PnP SPFx web part samples repo (Page Navigator web part) to the latest version of SPFx (1.20.0).<br>
> 👉 The official issue is described [here](https://github.com/pnp/sp-dev-fx-webparts/issues/).

## Testing a Typescript SPFX project with the Jest framework

In order tests for a SharePoint Framework (SPFx) project in TypeScript using the [Jest testing framework](https://jestjs.io/) (no matter whether web parts or extensions are targeted), several basic adjustments are needed. Following recommendations worked like a charm for me (tested with SPFx version ≥ 1.19).

## Minimal path to awesome (setup)

1. Install Jest and related packages

   First, you need to install Jest and some additional packages that help with testing in a TypeScript environment. Run the following command in your SPFx project directory:

   ```bash
   npm install --save-dev jest ts-jest @types/jest
   ```

   Optionally, to _test React components_, you also could install these two libraries to write more concise and readable tests by providing additional assertions for common testing scenarios:

   ```bash
   npm install --save-dev @testing-library/react @testing-library/jest-dom
   ```

2. Configure Jest

   Create a Jest configuration file named `jest.config.json` in the `config` folder of your project. This basic configuration is recommended:

   ```json
   {
     /**
      * Setup based on this resource:
      * https://titolivio.eu/2024/04/30/testing-sharepoint-framework-spfx-components-with-jest-and-react-testing-library/
      */

     // Test root(s)
     "roots": ["../src", "../tests"],
     "testPathIgnorePatterns": ["/node_modules/", "/lib/"], // Ignore certain directories
     // used within ts-jest for transpiling
     "transform": {
       "^.+\\.tsx?$": "ts-jest"
     },
     // find test files matching this pattern
     "testRegex": "(/__tests__/.*|(\\.|/)(test|spec))\\.tsx?$",
     "moduleFileExtensions": ["ts", "tsx", "js", "jsx", "json", "node"],
     // Map CSS imports to identity-obj-proxy for mocking
     "moduleNameMapper": {
       "\\.(css|less|scss|sass)$": "identity-obj-proxy" // Mock CSS imports
     },
     // set output to erbose mode
     "verbose": true,
     // handle coverage report
     "collectCoverage": false
   }
   ```

3. Adjust `tsconfig.json`

   Add the `tests` folder to the `tsconfig.json` file to find all type definitions even for any test files in the `tests` folder:

   ```json
    "include": [
      "src/**/*.ts",
      "src/**/*.tsx",
      "tests/**/*" // 👈 adjust this
    ]
   ```

4. Update `package.json`

   Add a test script to `package.json` to run Jest easily:

   ```json
    "scripts": {
        "test": "./node_modules/.bin/jest --config ./config/jest.config.json",
        "test:watch": "./node_modules/.bin/jest --config ./config/jest.config.json --watchAll"
    }
   ```

## Write and run tests

As the setup is complete, you will be ready to write tests and run them on your local dev machine:

1. Create (a) test file(s)

   Create a test file for your component or module. For example, if you have a component named `My Component.ts`, you can create a test file named `MyComponent.test.ts` in the same directory.

   > [!TIP]
   > Depending on your testing concept, I would recommend to store all test specifications in a dedicated `tests` folder.

   For it to work, an extension on the `jest.config.json` file is required to make the test files in the `tests` folder retrievable (which is already reflected in the above Jest configuration):

   ```json
    "roots": ["../src", "../tests"], // 👈 add the 'tests' folder to the root
   ```

6. Write tests

   In the test file(s), tests can be written using Jest's syntax in Typescript.
   Example:

   ```typescript
   import { MyComponent } from "./MyComponent";

   describe("MyComponent", () => {
     it("should do something", () => {
       const component = new MyComponent();
       expect(component.someMethod()).toBe(someExpectedValue);
     });
   });
   ```

7. Run the tests

   The tests can be run using the following command:

   ```bash
   npm run test
   ```
