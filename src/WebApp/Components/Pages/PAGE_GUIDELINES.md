# WebApp/Components/Pages Structure and Best Practices

## Overview
The `WebApp/Components/Pages` folder contains Blazor components that represent the main pages of the web application. Each page is typically implemented as a `.razor` file and may include associated code, markup, and styles. Pages are the entry points for navigation and user interaction within the app.

## Structure
- **Page Components**: Each page is a `.razor` file decorated with the `@page` directive, specifying its route.
- **Dependency Injection**: Pages commonly use `@inject` to access services such as navigation, data, or business logic.
- **Parameters**: Query parameters are handled using `[SupplyParameterFromQuery]` attributes, allowing pages to react to URL changes.
- **UI Composition**: Pages use reusable components (e.g., `CatalogListItem`, `CatalogSearch`) to build their UI, promoting modularity and maintainability.
- **Code Sections**: The `@code` block contains C# logic, including properties, methods, and lifecycle hooks like `OnInitializedAsync`.
- **Styling**: Pages may include a `<style>` section for scoped CSS, ensuring styles do not leak between components.

## How Pages Work
- **Routing**: The `@page` directive defines the URL route for the page. Navigation to this route renders the page component.
- **Lifecycle**: Pages use Blazor lifecycle methods (e.g., `OnInitializedAsync`) to load data or perform setup when the page is rendered.
- **Data Binding**: Pages bind data to UI elements using Razor syntax (`@variable`).
- **Navigation**: The `NavigationManager` service is used for programmatic navigation and URL manipulation.
- **Pagination Example**: The `Catalog` page demonstrates a paginator that dynamically generates page links and handles navigation via query parameters.

## Best Practices for New Pages
1. **Use the `@page` Directive**: Always specify a route for the page.
2. **Leverage Dependency Injection**: Use `@inject` for required services instead of creating them manually.
3. **Parameterize with `[SupplyParameterFromQuery]`**: Support query parameters for stateful navigation and deep linking.
4. **Componentize UI**: Break down complex UIs into reusable components.
5. **Follow Lifecycle Patterns**: Use `OnInitializedAsync` or other lifecycle methods for data loading and setup.
6. **Add XML Documentation**: Document all public methods and properties using XML comments for maintainability and IntelliSense support.
7. **Scoped Styling**: Place CSS in a `<style>` block within the `.razor` file to avoid style conflicts.
8. **Accessibility**: Use semantic HTML and ARIA attributes where appropriate.
9. **Error Handling**: Gracefully handle loading and error states (e.g., show a loading message or error alert).
10. **Consistent Naming**: Name files and components clearly to reflect their purpose (e.g., `Catalog.razor` for the catalog page).

## Example: Catalog Page
- **Route**: `@page "/"`
- **Services**: Injects `NavigationManager` and `CatalogService`.
- **Parameters**: Supports `page`, `brand`, and `type` as query parameters.
- **UI**: Renders a search bar, item list, and a paginator.
- **Pagination**: Uses a helper method to generate visible page links and ellipsis for large page sets.
- **Styling**: Includes a `<style>` block for paginator and layout styles.

---

By following these guidelines, new pages will be consistent, maintainable, and user-friendly, ensuring a high-quality user experience throughout the application.
