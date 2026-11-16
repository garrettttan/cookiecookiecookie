# 🍪 Cookie Exchange 2026

A tiny, phone-friendly page for tracking who's bringing which cookie, drink or other item (and what allergens it contains).

- **Frontend:** `index.html`, a single static file with no build step, hosted on GitHub Pages.
- **Data:** one Supabase table, `public.cookie_exchange_entries`, in the Fantasy Survivor project.
  Anyone with the link can add, edit and delete entries. That's intentional, because it's low stakes.
  The key in `index.html` is Supabase's *publishable* key, which is meant to be public.

## Turning on GitHub Pages

1. Merge this branch into `main`.
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, then select `main` and `/ (root)`, and save.
4. After a minute or so the site is live at `https://garrettttan.github.io/cookiecookiecookie/`.

## Changing things

- **Allergen choices:** edit the `ALLERGENS` list near the top of the `<script>` in `index.html`.
  People can also type in their own under the chips.
- **Title:** search `index.html` for `Cookie Exchange`.
- **Item types:** the `KINDS` list in `index.html` (cookie, drink, other). Adding a new type also needs the `kind` check constraint on the table updated.

## Cleaning up after the event

Run this in the Supabase SQL editor for the Fantasy Survivor project:

```sql
drop table public.cookie_exchange_entries;
```

That removes the table, its four access rules and its live-update subscription. Nothing else was added to the project
(no functions, triggers, edge functions or storage).

If you want to keep a record first, use the Table Editor's **Export → CSV** before dropping the table.
