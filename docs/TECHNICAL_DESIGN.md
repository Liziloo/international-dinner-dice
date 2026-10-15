# Technical Design: International Dinner Dice

## Technology Stack

The application uses:

- **React** for the user interface.
- **TypeScript** for application code and data types.
- **Vite** for development and production builds.
- **npm** for dependency management.
- **CSS or CSS Modules** for styling.
- **Vitest** and **React Testing Library** for automated testing.

Compatible stable dependency versions are used and committed to the npm lockfile. Dependencies are kept minimal.

## Architecture

The application has three main areas of responsibility:

- **Data:** The bundled country and culinary region dataset.
- **Application logic:** Assignment, component management, and validation.
- **Interface and persistence:** React components, user interactions, and browser storage.

Assignment and validation logic are kept independent of React so they can be tested without rendering the interface.

The source directory should separate these concerns clearly. The precise file layout is an implementation choice rather than a fixed requirement.

## Data Model

Each country or culinary region has a stable identifier and a display name.

Each meal component has a stable identifier, an editable name, and a reference to its assigned country or region. An assignment may temporarily be absent while a component is being initialized, but the application should not present an invalid completed meal state.

Application state contains the configured components and any metadata needed for persistence.

Component identity is independent of its display name, so renaming a component does not affect its assignment or identity.

## Assignment Logic

Assignment operations are implemented as independently testable functions.

- **Roll All:** Selects unique entries for all configured components.
- **Reroll:** Selects an unused entry other than the component's current assignment, changing no other component.
- **Add:** Validates the component name and assigns an unused entry.
- **Rename and reorder:** Modify component configuration without changing assignments.
- **Remove:** Deletes a component and releases its assignment.
- **Restore defaults:** Restores the initial component configuration and valid assignments.

Random selection must not depend on a particular ordering of the dataset. If there are insufficient unused entries, the operation must fail gracefully rather than produce duplicate assignments.

## Dataset

The dataset is stored locally and requires no runtime network requests.

Its selection criteria are defined in `PRODUCT_SPEC.md`. The implementation should use a documented source, consistent identifiers and names, and a deliberate policy for duplicate or overlapping entries.

Automated tests validate the actual bundled dataset, including its size, identifier uniqueness, normalized display-name uniqueness, and compatibility with assignment logic.

## Persistence

Browser `localStorage` stores component configuration and assignments.

Persisted data uses a versioned format to support future changes. On startup, the application parses and validates saved data before using it.

Malformed, incompatible, or invalid state is handled gracefully. If recovery is not possible, the application initializes a valid default configuration. Storage failures should not make the main interface unusable.

## Interface and Styling

The React interface presents the component list, country or region assignments, assignment controls, and component-management controls.

Reusable components should be introduced where they improve clarity and maintainability. Application state changes should remain predictable, and list rendering should use stable component identifiers.

Plain CSS or CSS Modules provide responsive styling without requiring a UI framework. Accessibility includes semantic controls, keyboard operation, visible focus indicators, and understandable feedback.

## Testing and Build

Vitest covers application logic and edge cases. React Testing Library covers important user interactions and visible behavior.

Tests cover assignment uniqueness, reroll isolation, component management, persistence, invalid data, and error handling. Randomness should be controlled when deterministic test outcomes are necessary.

The project provides npm scripts for development, testing, and production builds. Type checking and linting should also be included where configured. Verification reports must reflect commands actually executed and their observed results.
