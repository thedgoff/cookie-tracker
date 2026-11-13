# Christmas Cookie Tracker

A single-file HTML app for planning a holiday baking season: a recipe book, a bake plan with a suggested order, and a shopping list that totals ingredients and rounds up to store packages.

**The app ships with an empty recipe book.** You add your own recipes.

## What it does
- Recipe book with batch scaling, year tags, notes and an edit mode
- Bake plan with a suggested order (freezable first, long chills next, then grouped by oven temperature and shared ingredients) and drag-to-reorder
- Gram weights in parentheses next to every cup, spoon and "each" amount, from a standard baking chart and editable per ingredient
- Optional cost estimates on the shopping list and recipe pages, once store prices are saved (see `prompt.md`)
- Shopping list that adds up ingredients across the year's recipes, with Buy / Have it toggles and a checklist view
- A starter pantry catalog (ingredients, units, package sizes, grams per unit)

## Using it
Open `cookie-tracker.html` in a browser. Add recipes with the "Add a recipe" tab, or edit `<script type="application/json" id="library">` in the file directly. The format is described in `PROMPT.md`.

If you use Claude, `PROMPT.md` has a prompt for loading your recipes into the file.

## Where your data is saved
- Opened as a normal web page, the app saves to your browser's local storage, on that device only. Clearing site data erases it.
- Photo uploads and the "Fill in with Claude" button depend on Claude's artifact environment and are not available when the file is opened on its own. This is based on how the code checks for them, so test it in your own browser.

## Your recipes and content
- You are responsible for making sure you have the right to use any recipe text, photos or other content you add.
- This project does not include or distribute third-party recipes.
- Recipe names, brand names and trademarks mentioned in the pantry catalog belong to their respective owners and are used only to describe ingredients.

## Third-party resources
The page loads fonts from Google Fonts. Delete the three `<link>` tags near the top of the file if you don't want that.

## License
All rights reserved"

## Disclaimer
Provided as is, with no warranty. This README is not legal advice.
