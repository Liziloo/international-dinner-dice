# Product Specification: International Dinner Dice

## 1. Purpose

International Dinner Dice assigns a unique country or culinary region to each component of a meal, providing a playful way to explore an international market.

The assignment is a shopping prompt, not a recipe recommendation. Users choose their own products, ingredients, and recipes.

## 2. Product Principles

- **Country assignments are random; meal components are not.**
- Every active component has a different assignment.
- Users retain control over what they buy and cook.
- Unexpected combinations are intentional.
- The app should be straightforward to use while shopping, including on a phone.
- The core experience must work without accounts, a backend, or external services.

## 3. Meal Components

The initial configuration contains these components:

- Protein
- Starch
- Vegetable
- Beverage
- Dessert

Users can add, rename, remove, and reorder components.

Component names must not be empty or duplicate another component's name, ignoring case and surrounding whitespace.

Renaming or reordering a component must preserve its assignment. Removing a component frees its assignment for future use. Adding a component must assign an unused country or region without changing existing assignments.

Users must be able to restore the default component configuration.

## 4. Country Assignments

Each active component receives exactly one country or culinary region. No two active components may have the same assignment.

### Roll All

Assign a new country or region to every active component. All assignments must be unique, and existing assignments are replaced.

### Reroll One Component

Users can reroll an individual component.

- Only the selected component's assignment changes.
- All other assignments remain unchanged.
- The new assignment cannot already belong to another component.
- If an unused alternative exists, the new assignment must differ from the previous one.
- If no valid alternative exists, the existing assignment remains unchanged and the user is informed.

### Adding a Component

A newly added component receives an unused assignment without changing existing assignments. If no assignment is available, the app explains the limitation and does not create an invalid assignment.

## 5. Country and Culinary Region Selection

The app must include a comprehensive, locally available collection of countries and culinary regions that shoppers could realistically encounter in a large U.S. international grocery market.

Use the published country and region guides for Jungle Jim's International Market as a starting reference. Prioritize entries represented by actual international grocery products or identifiable shopping sections, rather than attempting to include every country in the world.

The collection should provide broad geographic and culinary diversity, including representation from Africa, Asia, Europe, North America, South America, the Caribbean, and Oceania.

The collection must be large enough to support substantially more than the five default meal components. It should not be limited to a small list of familiar countries or cuisines.

Countries and regions must be presented with clear, recognizable names. Distinct culinary regions may be included when they represent meaningful identities in international food retail. Avoid confusing users with duplicate or near-identical entries.

The app must not require an internet connection to obtain assignments.

## 6. Persistence

Users' component configurations and valid country or region assignments must survive page refreshes and subsequent visits in the same browser.

Users should not have to recreate their component list every time they open the app.

If saved information is missing or unusable, the app must recover gracefully and provide a valid default configuration rather than leaving the application unusable.

## 7. User Interface and Accessibility

The interface must:

- Clearly display each component and its assigned country or region.
- Provide an obvious Roll All action.
- Provide a reroll action for each component.
- Allow users to add, rename, remove, and reorder components.
- Provide a way to restore the default configuration.
- Explain when an assignment cannot be changed because no alternative is available.
- Remain usable on both mobile and desktop screens.
- Support keyboard navigation and provide visible focus indicators.
- Use clear labels for interactive controls.
- Communicate errors and important action results in text, not color alone.

The interface should remain practical on a small phone screen while shopping.

## 8. Out of Scope

The app must not:

- Choose recipes or dishes.
- Recommend ingredients, brands, or specific products.
- Attempt to make assignments fit a coherent cuisine or meal.
- Require user accounts.
- Depend on a backend or external API.
- Require location tracking.
- Add social networking, shopping-cart, or unrelated meal-planning features.

## 9. Success Criteria

A user can open the app, receive unique country or region assignments, reroll one assignment without disturbing the others, customize meal components, refresh the page without losing valid saved configuration, and use the interface comfortably on a phone.

The resulting assignments provide useful prompts for exploring an international grocery market while leaving all food and recipe decisions to the user.
