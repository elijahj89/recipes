# 🍲 Family Recipes

A simple, free website for storing our family recipes and sharing them with a link.

## How it works

There is **no database**. This is a static website:

- **`recipes.json`** — where all the recipes are stored (this is the "data").
- **`index.html`** — the web page that reads `recipes.json` and displays it (search, categories, printable recipe view).

GitHub Pages serves these files for free. Anyone with the link can view; no login needed.

## Adding a recipe

Just ask Claude Code: *"Add this recipe: …"* and it will append a new entry to `recipes.json` and push it. Each recipe looks like this:

```json
{
  "id": "unique-name",
  "title": "Recipe Name",
  "category": "Dinner",
  "servings": "4",
  "time": "45 min",
  "author": "Grandma",
  "description": "Short description.",
  "ingredients": ["1 cup flour", "2 eggs"],
  "steps": ["Do this.", "Then this."],
  "notes": "Optional tip."
}
```

## Turning on the website (one-time setup)

1. Go to this repo on GitHub → **Settings** → **Pages**.
2. Under **Build and deployment**, set **Source** to *Deploy from a branch*.
3. Choose branch `main` (or your published branch) and folder `/ (root)`, then **Save**.
4. After a minute, GitHub gives you a public URL like `https://<username>.github.io/recipes/` — that's the link to share with family.

## Viewing locally

Open a terminal in this folder and run:

```bash
python3 -m http.server 8000
```

Then visit http://localhost:8000
