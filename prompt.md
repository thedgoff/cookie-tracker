# Christmas Cookie Tracker: setup prompt

Attach `cookie-tracker.html` to a new Claude chat, along with your recipes (spreadsheets, a list of links, or pasted recipes). Then paste everything below the line.

Only use recipes you have the right to use: your own, ones shared with you, or ones you are adding for personal reference. The tracker ships with an empty recipe book.

---

I've attached `cookie-tracker.html`, a finished Christmas cookie tracker app. Please don't rebuild it. Your job is to put MY recipes into it and publish it as an artifact I can keep using.

## What the app already does
- **Recipe book:** sidebar index and full recipe pages with batch scaling, year tags, notes, photo upload and an edit mode.
- **Bake plan:** pick cookies for a year, get a suggested bake order (freezable first, long-chill doughs next, then grouped by oven temp and shared ingredients, no-bake and icing last), drag to reorder, and track status.
- **Weights:** every volume amount also shows its weight in grams, editable per ingredient.
- **Shopping list:** adds up ingredients for the year at each batch size and rounds up to packages, with Buy / Have it toggles and a clean checklist view that crosses items out.
- **Add a recipe:** paste recipe text and Claude fills in the details.

## Your task
1. **Read my recipes** from what I attached. [OPTIONAL: describe your spreadsheet layout, e.g. "one sheet per year, row 1 = cookie names linked to the recipe, green fill = made that year, rows below = ingredient amounts with the unit in column A in parentheses".] Ask me if anything is unclear.
2. **Fill in the `recipes` array** inside `<script type="application/json" id="library">` in the HTML, using the format below. The library ships with an empty `recipes` array. Keep the existing `catalog` entries and add any pantry items my recipes need. Don't change the rest of the code unless something is broken.
3. **Publish it** as an artifact.
   - If your artifact tools support saved data, declare these capabilities so changes persist and sync: `db` and `user` (saved data), `assets` (photo uploads) and `sample` (the "Fill in with Claude" button).
   - If they don't, publish it anyway. It falls back to saving in my browser.
4. **Check that it loads.** Then tell me anything you weren't sure about (unclear years, odd amounts, recipe sites you couldn't open).

## Library format

```json
{
  "catalog": {
    "flour": {"label": "Flour (all-purpose)", "unit": "C", "cat": "Baking staples", "pkg": 18, "pkgLabel": "5 lb bag", "g": 120}
  },
  "recipes": [
    {
      "id": "chocolate-crinkles",
      "name": "Chocolate Crinkles",
      "url": "",
      "yield": 28,
      "chill": "1",
      "cook": "10-12",
      "temp": 350,
      "freezable": true,
      "kind": "bake",
      "years": {"2024": "m", "2025": "p"},
      "ing": [{"k": "flour", "q": 1.5}, {"k": "eggs", "q": 4}],
      "notes": "",
      "siteYield": "",
      "siteIng": [],
      "steps": ["Whisk the dry ingredients…", "…"]
    }
  ]
}
```

What the fields mean:
- **unit:** one of `C` (cups), `tsp`, `tbsp`, `oz`, `g`, `ea` (each), `pkg`, `can`.
- **pkg:** how many of that unit come in one store package. Use `null` if unknown.
- **cat:** the store section shown in the shopping view.
- **g:** grams in one unit (e.g. 120 for a cup of flour), from a standard baking weight chart. The app shows the weight in parentheses next to volume amounts. Leave it out for items already measured in g or oz.
- **years:** `m` = made that year, `p` = on the list but not made, `h` = unclear (shown in gold).
- **kind:** one of `bake`, `nobake`, `candy`, `icing`.
- **chill:** hours, as text: "1", "1-2", "0.5+0.5", or "1-overnight".
- **cook:** minutes, as text.
- **temp:** a number (°F), or `null` for no-bake recipes.
- **ing:** the shopping ingredients for one batch as I make it, with each `q` in the catalog item's unit. Amounts add up across recipes on the shopping list.
- **steps:** 4–8 short steps. Use steps I provided or ones written in your own words from my notes, keeping temps and times. If I only gave a link and no text, leave the list empty and don't reproduce the linked page's instructions.
- **siteIng / siteYield:** optional reference copies of the original ingredient lines and yield, only if I pasted them. Leave empty otherwise.
- **url:** a link to the original recipe, or an empty string.

## Notes
- Artifacts can't show images from other websites, so photos come from the "Add photo" button.
- Use lowercase-hyphen ids that are unique and never change.
