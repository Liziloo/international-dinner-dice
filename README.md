# International Dinner Dice

A little randomness for a more adventurous home-cooked meal or date-night shopping trip.

International Dinner Dice turns a trip to an international grocery store into a culinary challenge. Assign a different country to each part of your meal, explore the corresponding sections of the store, and see what you come up with.

The app chooses the countries. **You choose what to buy and what to cook.** Unexpected combinations are part of the fun.

## Features

- **Roll All:** Randomly assign a different country to every meal component.
- **Reroll a country:** Try a different country for one component without changing the others.
- **Customize your meal:** Add, rename, remove, and reorder meal components.
- **Unique country assignments:** No country appears twice in the same meal.
- **Save your setup:** Your component configuration persists between visits on the same browser.
- **Responsive design:** Use the app on your computer or phone, including while shopping.

## Example

| Meal component | Assigned country |
|---|---|
| Protein | Japan |
| Starch | Italy |
| Vegetable | Thailand |
| Beverage | Mexico |
| Dessert | Germany |

These assignments are shopping prompts, not recipe suggestions. Find something interesting in each country's section and get creative.

## Technology

Built with React, TypeScript, and Vite. Uses browser local storage to remember your configuration.

## Getting started

### Requirements

- Node.js, with a version supported by the project's Vite dependencies.
- npm.

### Installation

Clone the repository and install its dependencies:

```bash
git clone https://github.com/Liziloo/international-dinner-dice/
cd <repository-directory>
npm install
```

### Run locally

```bash
npm run dev
```

Open the local URL printed by Vite.

### Run tests

```bash
npm test
```

### Build for production

```bash
npm run build
```

The production build is generated in `dist/`.

See `package.json` for the project's actual scripts and dependency requirements.

## Project documentation

- [`PRODUCT_SPEC.md`](PRODUCT_SPEC.md) — application features and behavior.
- [`TECHNICAL_DESIGN.md`](TECHNICAL_DESIGN.md) — technical architecture.
- [`ACCEPTANCE_TESTS.md`](ACCEPTANCE_TESTS.md) — functional and quality requirements.
- [`IMPLEMENTATION_PLAN.md`](IMPLEMENTATION_PLAN.md) — development milestones.

## Scope

International Dinner Dice is a lightweight, local-first web application. It does not require an account, a backend, or an external API. It doesn't select recipes or ingredients, recommend products, or depend on current store inventory.

## License

MIT
