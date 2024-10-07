# Writing Tests for React Components in SPFx projects with Jest Testing Framework

Reference: [Blog Post](https://titolivio.eu/2024/04/30/testing-sharepoint-framework-spfx-components-with-jest-and-react-testing-library/) by pH7x Systems (10/2024)

The following content is taken from the blog post mentioned above.

## Minimal path to awesome (setup)

### Prerequisites

> [!NOTE]
> In order to have a proper testing setup, please refer to this article: [Testing SPFx projects with Jest](./Testing%20SPFx%20projects%20with%20Jest.md)

### Necessary mode modules (dependencies)

To write tests for React components, make sure you have installed these two node modules in your project scope (on your local dev machine):

```bash
npm install --save-dev @testing-library/react @testing-library/jest-dom
```

## Writing Tests

### React component and common testing capabilities (`@testing-library/react` and `@testing-library/jest-dom`)

Let’s say we have the `HelloWorld` React component in our SPFx project:

```typescript
// src/webparts/helloWorld/components/HelloWorld.tsx

// Define the props for our component
export interface IHelloWorldProps {
  name: string;
}

// Define the component
export const HelloWorld: React.FC<IHelloWorldProps> = (props) => {
  // Render a greeting message
  return <h1>Hello, {props.name}!</h1>;
};
```

We can write a test for this component like so:

```typescript
// src/webparts/helloWorld/components/HelloWorld.test.tsx
// or (recommended): tests/webparts/helloWorld/components/HelloWorld.test.tsx

import { render, screen } from "@testing-library/react";
import "@testing-library/jest-dom/extend-expect";
import { HelloWorld } from "../HelloWorld";

it("renders hello message", () => {
  // Render the component with React Testing Library's render function
  render(<HelloWorld name="SPFx" />);

  // Check if the rendered component includes the text "Hello, SPFx!"
  expect(screen.getByText("Hello, SPFx!")).toBeInTheDocument();
});
```

### Mocking functions & services

When testing components that have dependencies, we can use Jest’s mocking capabilities.

> [!TIP]
> It is always a good idea to use mocks sparingly to keep tests focused and maintainable.

For example, if we have the `HelloWorld` component that uses the `IDataService` service to fetch data, we could mock this service in our test. This allows us to isolate the behavior of the component from its dependencies:

```typescript
// src/webparts/helloWorld/components/HelloWorld.tsx

import { IDataService } from "../../../services/IDataService";

// Define the props for our component
export interface IHelloWorldProps {
  dataService: IDataService;
}

// Define the component
export const HelloWorld: React.FC<IHelloWorldProps> = (props) => {
  // Initialize state for storing the fetched data
  const [data, setData] = React.useState(null);

  // Fetch data when the component mounts
  React.useEffect(() => {
    props.dataService.fetchData().then(setData);
  }, [props.dataService]);

  // Render the fetched data
  return <h1>{data}</h1>;
};
```

In a test, we could create a mock data service and pass it to the `HelloWorld` component:

```typescript
// src/webparts/helloWorld/components/HelloWorld.test.tsx
// or (recommended): tests/webparts/helloWorld/components/HelloWorld.test.tsx

import { render, screen, waitFor } from "@testing-library/react";
import "@testing-library/jest-dom/extend-expect";
import { HelloWorld } from "../HelloWorld";

it("renders data from the service", async () => {
  // Create a mock data service
  const mockDataService = {
    fetchData: jest.fn().mockResolvedValue("Hello, SPFx!"), // 👈 mock the 'fetchData' call and return mocked values
  };

  // Render the component with the mock data service
  render(<HelloWorld dataService={mockDataService} />);

  // Wait for the Promise to resolve and the component to re-render
  await waitFor(() => screen.getByText("Hello, SPFx!"));

  // Check if the rendered component includes the fetched data
  expect(screen.getByText("Hello, SPFx!")).toBeInTheDocument();

  // Check if the fetchData method of the mock data service was called
  expect(mockDataService.fetchData).toHaveBeenCalled();
});
```
