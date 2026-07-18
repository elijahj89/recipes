# 🍲 Snug Family Kitchen

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

## Update prompts (stale-content fix for phones)

The app detects new deploys **automatically** — there is nothing to bump by hand.
On a timer and whenever the app is reopened, it computes a signature of the
deployed files (`index.html` + `recipes.json`) and compares it to what the device
is running. If anything changed, an **"Update available — Reload"** banner slides
up (Reload is the only option, so everyone moves to the latest version). This
matters most for the app added to a phone's home screen, where the browser
otherwise holds onto stale content.

Because detection is content-based, simply pushing any change (a new recipe or a
code edit) is enough — no version file to maintain.

> `version.json` is legacy from the old manual scheme and is no longer used by the
> app; it can be removed once every device has loaded a build from this point on.

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
