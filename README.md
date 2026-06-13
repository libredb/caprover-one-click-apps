# LibreDB — CapRover One-Click Apps

LibreDB's own [CapRover](https://caprover.com) one-click-app repository. Add it
as a **3rd-party repository** in CapRover to install LibreDB apps in one click —
available immediately, independent of the official `caprover/one-click-apps`
review queue.

## Add this repository to CapRover

1. Open your CapRover dashboard → **Apps** → **One-Click Apps/Databases**.
2. Scroll to the bottom, to **3rd party repositories**.
3. Paste this URL and click **Connect New Repository**:

   ```
   https://libredb.github.io/caprover-one-click-apps
   ```

4. Search for **LibreDB Studio** and install.

## Apps

| App | Description |
|-----|-------------|
| **LibreDB Studio** | Open-source web-based SQL IDE — query PostgreSQL, MySQL, SQLite, Oracle, SQL Server, MongoDB & Redis from the browser, with AI-powered query assistance. |

## How it works

- App definitions live under `public/v4/apps/*.yml` with logos in
  `public/v4/logos/*.png` — the same `captainVersion: 4` format as the official
  repo. The source of truth for LibreDB Studio is maintained in
  [`libredb/libredb-studio` → `deploy/caprover/`](https://github.com/libredb/libredb-studio/tree/main/deploy/caprover).
- On every push to `main`, the GitHub Actions workflow validates the templates,
  builds the static catalog into `dist/`, and deploys it to GitHub Pages. CapRover
  then reads `…/v4/list`, `…/v4/apps/<name>` and `…/v4/logos/<name>.png` from the
  published site.

## Local development

```bash
npm install
npm run validate_apps   # validate every app template + logo
npm run formatter       # prettier check (use formatter-write to fix)
npm run build           # build the static catalog into ./dist
```

## Adding / updating an app

1. Add or edit `public/v4/apps/<name>.yml` and add `public/v4/logos/<name>.png`.
2. Run `npm run validate_apps && npm run formatter`.
3. Commit to `main` — GitHub Actions publishes automatically.

---

Looking for the manual install or the official-repo submission? See
[`libredb/libredb-studio` → `deploy/caprover/`](https://github.com/libredb/libredb-studio/tree/main/deploy/caprover).
