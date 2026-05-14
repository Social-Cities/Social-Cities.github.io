# Social Cities Website

Static marketing website for Social Cities, a startup building technology that helps people find their people and gather in real life.

The site is designed to be hosted directly with GitHub Pages from the repository root. It does not require a build step, framework, package manager, or server-side runtime.

## Project Structure

```text
.
├── index.html
├── styles.css
├── script.js
└── assets/
    └── social-cities-hero.jpg
```

- `index.html` contains the page content and section structure.
- `styles.css` contains all layout, responsive, and visual styling.
- `script.js` handles the mobile navigation state, sticky header state, and footer year.
- `assets/social-cities-hero.jpg` is the homepage hero image.

## Run Locally

From the repo root:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000/
```

You can stop the server with `Ctrl+C`.

Because this is a static site, you can also open `index.html` directly in a browser, but the local server is closer to how GitHub Pages will serve it.

## Test

There is no automated test suite yet. For now, use these checks before publishing changes:

1. Start the local server.

   ```bash
   python3 -m http.server 8000
   ```

2. Confirm the homepage responds.

   ```bash
   curl -I http://localhost:8000/
   ```

3. Confirm the hero image responds.

   ```bash
   curl -I http://localhost:8000/assets/social-cities-hero.jpg
   ```

4. Check the page in desktop and mobile browser widths.

   Recommended viewports:

   - Desktop: `1440 x 1000`
   - Mobile: `390 x 844`

5. If Playwright is available, capture quick screenshots:

   ```bash
   npx playwright screenshot --viewport-size=1440,1000 http://localhost:8000/ /tmp/social-cities-desktop.png
   npx playwright screenshot --viewport-size=390,844 http://localhost:8000/ /tmp/social-cities-mobile.png
   ```

   If Playwright says browsers are missing, install Chromium once:

   ```bash
   npx playwright install chromium
   ```

## Development Notes

- Keep the site static and dependency-free unless there is a clear reason to add tooling.
- Prefer editing the existing `index.html`, `styles.css`, and `script.js` files instead of introducing a build system.
- Keep images in `assets/`.
- Use compressed web-friendly images. Large source files should be converted before committing.
- Check mobile layout after any major copy, spacing, or image change.
- The contact email in `index.html` is currently `hello@socialcities.com`; update it if the company uses a different address.

## Deploy With GitHub Pages

This repository is named `Social-Cities.github.io`, so GitHub Pages can serve it as an organization or user site.

Typical deployment flow:

```bash
git add index.html styles.css script.js assets README.md
git commit -m "Add Social Cities website"
git push origin main
```

After pushing, GitHub Pages should serve the site from:

```text
https://social-cities.github.io/
```

If Pages is not already enabled, open the repository settings on GitHub and enable Pages from the `main` branch root.
