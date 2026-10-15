# Agent Instructions

## Objective

Implement the complete International Dinner Dice application described in `PRODUCT_SPEC.md`, following `TECHNICAL_DESIGN.md` and the project conventions in `README.md`.

Deliver a working application, not just a plan, mockup, or partial implementation.

## Workflow

- Inspect the repository and read the project documentation before making changes.
- Work autonomously from initial inspection through implementation, integration, and verification.
- Do not pause for approval between routine development phases.
- Delegate implementation or testing tasks to subagents when useful and available. As coordinator, integrate and verify all contributions. If delegation is unavailable, do the work directly.
- Resolve ordinary implementation questions using the documented requirements and sound engineering judgment.
- Ask the user only if a genuinely blocking ambiguity cannot be resolved from the repository or specifications.

## Product Requirements

Follow `PRODUCT_SPEC.md` as the authority on product behavior and scope.

In particular:

- Randomize country and region assignments, not meal components.
- Never assign the same entry to multiple components in one meal.
- Ensure a single-component reroll does not alter other assignments.
- Preserve assignments when components are renamed or reordered.
- Include a comprehensive local dataset appropriate to large U.S. international grocery markets, using the specified market guides as a reference. Do not substitute a tiny hand-written sample.
- Persist valid configuration and assignments in the browser.
- Keep the application responsive, accessible, and free of unnecessary features.

Do not introduce recipe recommendations, ingredient selection, backend services, external APIs, accounts, or unrelated features.

## Engineering

- Use the documented React, TypeScript, Vite, npm, Vitest, and React Testing Library stack unless the repository already has a justified compatible setup.
- Preserve useful existing work.
- Keep assignment logic testable independently of the interface.
- Avoid unnecessary dependencies.
- Add or update tests when implementing behavior.
- Handle invalid saved state and ordinary storage failures gracefully.

## Verification and Completion

Before declaring completion:

1. Run the test suite.
2. Run the production build.
3. Run configured type-checking and linting.
4. Fix implementation failures and rerun relevant checks.
5. Confirm that the product requirements are implemented.
6. Update the README if the actual setup or commands differ from its documentation.

Report what was implemented, which checks were run, their actual results, and any remaining limitations. Never claim a check passed unless it was executed successfully.
