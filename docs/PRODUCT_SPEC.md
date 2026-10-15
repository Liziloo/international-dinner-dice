# Product Specification: International Dinner Dice

## Purpose

International Dinner Dice assigns a unique country or culinary region to each component of a meal, providing a playful way to explore an international grocery market.

The assignments are shopping prompts, not recipe recommendations. Users choose their own ingredients, products, and recipes. Unexpected combinations are part of the experience.

## Default Meal Components

The initial configuration contains five components:

- Protein
- Starch
- Vegetable
- Beverage
- Dessert

Users can add, rename, remove, and reorder components, or restore the default configuration.

Component names must not be empty or duplicate another component's name, ignoring case and surrounding whitespace.

## Country and Region Assignments

Every active component has one assigned country or culinary region. Assignments must be unique within a meal.

**Roll All** assigns a new set of unique countries or regions to all components, replacing the previous assignments.

**Reroll** changes the assignment of one component while leaving every other assignment unchanged. The replacement must differ from the previous assignment and must not be used by another component. If no valid alternative exists, the assignment remains unchanged and the user is informed.

Adding a component assigns it an unused country or region without changing existing assignments. If no assignment is available, the app explains the limitation and does not add an invalid component.

Renaming and reordering components preserve their assignments. Removing a component makes its assignment available for subsequent use.

## Country and Region Dataset

The app includes a comprehensive local collection of countries and culinary regions that shoppers could realistically encounter in a large U.S. international grocery market.

Published country and region guides from Jungle Jim's International Market are used as a starting reference, prioritizing entries represented by actual international grocery products or identifiable shopping sections rather than attempting to include every country in the world.

The collection offers broad geographic and culinary diversity.

The dataset is bundled with the application and is available without a network connection.

## Persistence

The user's component configuration and assignments persist across page refreshes and subsequent visits in the same browser.

If saved data is missing or unusable, the app recovers gracefully and provides a valid default configuration.

## User Experience

The interface clearly displays each component and its assignment, with an obvious Roll All action and an individual reroll control for each component.

Users can manage their component list and restore defaults without unnecessary complexity.

The application is responsive and usable on phones, tablets, and desktop computers. Interactive controls are keyboard-accessible, have clear labels and visible focus indicators, and communicate errors or limitations in text.

## Out of Scope

The application does not:

- Choose recipes or dishes.
- Recommend ingredients, brands, or specific products.
- Attempt to make assignments fit a coherent cuisine or meal.
- Require user accounts, a backend, or external APIs.
- Require location tracking.
- Include social networking, shopping carts, or unrelated meal-planning features.

## Success Criteria

A user can open the app, receive unique country or region assignments, reroll one assignment without disturbing the others, customize meal components, and return later without losing valid saved configuration.

The result is a practical, playful prompt for exploring an international grocery market, with food and recipe decisions left entirely to the user.
