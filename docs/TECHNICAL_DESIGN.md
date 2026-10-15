# Technical Design: International Dinner Dice

## 1. Technology Stack

International Dinner Dice is a client-side web application built with React and TypeScript, using Vite for development and production builds.

The project uses npm for dependency management, CSS or CSS Modules for styling, Vitest for unit testing, and React Testing Library for interface testing.

Dependencies are kept minimal to reduce maintenance overhead. The npm lockfile records the resolved dependency versions for reproducible installations.

## 2. Architecture

The application has three main areas of responsibility:

- **Country data:** A bundled dataset of countries and culinary regions available for assignment.
- **Application logic:** The rules governing component configuration, country assignment, validation, and state transitions.
- **User interface and persistence:** The React interface, user interactions, and browser-based storage.

Keeping application logic separate from the interface makes assignment behavior easier to test and reduces the amount of business logic embedded in UI components.

A possible source layout is:

```text
src/
  components/
  data/
  logic/
  storage/
  types/
  App.tsx
  main.tsx
  styles.css
tests/
```

This layout is illustrative rather than prescriptive. The final organization may differ according to the needs of the implementation.

## 3. Data Model

The application represents countries or culinary regions, meal components, and persisted application state using TypeScript types.

A country or region has a stable identifier and a human-readable display name. A meal component has a stable identifier, a user-editable name, and an assignment referencing a country or region.

For example:

```ts
type Country = {
  id: string;
  name: string;
};

type MealComponent = {
  id: string;
  name: string;
  countryId: string | null;
};
```

The application state contains the configured meal components and any metadata needed to manage persistence.

Component identity is independent of its display name, allowing users to rename or reorder components without losing their assignments.

## 4. Assignment and Configuration Logic

Assignment logic is independent of React and operates on the application data model.

### Roll All

Roll All assigns a country or region to every configured component. Assignments are unique within the meal, and each invocation replaces the existing assignments.

A shuffle or sampling-without-replacement algorithm can provide the required uniqueness.

### Reroll One Component

A single-component reroll selects from entries not assigned to other components. The current assignment is excluded when another valid option exists.

Only the selected component changes. If no alternative is available, the existing assignment is preserved and the interface can explain why it did not change.

### Component Management

Adding a component validates its name and assigns an unused country or region. Existing assignments remain unchanged.

Renaming and reordering affect component presentation but not assignments. Removing a component makes its previous assignment available for later use.

Restoring defaults returns the component configuration to its initial state and produces valid, unique assignments.

### Validation

Validation covers component names, component identifiers, assignment identifiers, and assignment uniqueness. It also accounts for configurations with more components than available countries or regions.

These checks protect the application from invalid user input and inconsistent persisted state.

## 5. Country and Region Data

The country and region dataset is bundled with the application, so assignment does not depend on an external service or network request.

The dataset is intended to reflect the countries and culinary regions represented in large U.S. international grocery markets. Published country and region guides from Jungle Jim's International Market provide a starting reference for selecting entries.

Each entry has a consistent display name and stable identifier. The dataset avoids duplicate entries caused by alternate spellings or overlapping labels.

The dataset's scope and inclusion criteria are defined in `PRODUCT_SPEC.md`; its completeness and consistency are verified through automated tests.

## 6. Persistence

The application stores its configuration and assignments in the browser's `localStorage`.

Persisted state includes the configured components and their assignments. A version marker allows the application to recognize changes to the saved data format.

When the application starts, it loads and validates stored state before using it. Missing, malformed, or incompatible data is handled gracefully, with a valid default configuration used when recovery is not possible.

Storage errors should not make the main interface unusable. The application requires neither a backend nor a user account.

## 7. User Interface

The React interface presents the configured meal components, their current assignments, and controls for changing them.

The main interactions are Roll All, rerolling an individual component, editing the component list, and restoring defaults.

Reusable interface components may include a component card or list item, component editing controls, a component creation form, and a country or region display.

Application state changes are handled predictably, and stable component identifiers are used for React list keys. User-visible errors and unavailable actions are communicated clearly.

## 8. Styling and Responsive Behavior

The interface uses CSS or CSS Modules rather than requiring a UI framework.

The layout supports both mobile and desktop screens, with particular attention to usability on a phone while shopping. Interactive elements have visible focus indicators, accessible names, and usable target sizes.

Keyboard navigation and accessible feedback are part of the interface design.

## 9. Testing Strategy

Vitest covers application logic, including assignment uniqueness, reroll behavior, component management, validation, and persistence-related logic.

React Testing Library covers user-visible behavior and important interaction workflows.

Tests verify properties of random assignment rather than relying on particular random outcomes. Where necessary, randomness can be controlled to make edge cases reproducible.

The actual bundled country and region dataset is tested for its required size, identifier uniqueness, normalized display-name uniqueness, and valid assignment references.

## 10. Build and Verification

Vite provides the development server and production build. npm scripts expose the project's development, testing, and build workflows.

The project is verified through its automated tests and production build, along with type checking and linting where configured. Verification results are reported based on checks actually executed.
