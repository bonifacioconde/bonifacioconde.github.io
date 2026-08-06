# Bonifacio Conde Jr — Online CV

Source for my online CV, deployed to GitHub Pages.

**Live:** https://bonifacioconde.github.io/resume/

Built on the [Start Bootstrap Resume](https://startbootstrap.com/theme/resume) theme (Pug + Sass + Bootstrap 5).

---

## Editing the content

All content lives in **`src/pug/index.pug`**. Edit that file, not `dist/index.html` — `dist/` is generated and gets overwritten on every build.

Styling lives in `src/scss/`:

- `src/scss/variables/_colors.scss` — theme colors
- `src/scss/variables/_typography.scss` — fonts
- `src/scss/sections/_resume-section.scss` — section layout
- `src/scss/components/_sidenav.scss` — the fixed sidebar nav

---

## Local development

```bash
npm install
npm start        # builds and serves at http://localhost:3000 with live reload
npm run build    # one-off build into dist/
```

Requires Node 18+.

---

## Deployment

Deployment is automatic. `.github/workflows/deploy.yml` runs on every push to `master`:
it installs dependencies, runs `npm run build`, and publishes `dist/` to GitHub Pages.

**One-time setup in the repo settings:**

1. **Settings → Pages → Build and deployment → Source:** select **GitHub Actions**.
2. Push to `master`. The workflow deploys and the URL appears under **Actions → Deploy to GitHub Pages**.

To deploy manually without pushing: **Actions → Deploy to GitHub Pages → Run workflow**.

---

## Still to fill in

Placeholders in `src/pug/index.pug` marked with square brackets:

- `[professional email]`, `[handle]` — contact and social links
- `[N]`, `[X]`, `[Y]` — metrics in the summary and experience bullets
- `[App Name]` / `[id]` — App Store links in the **Shipped Apps** section
- `assets/img/profile.jpg` — replace with your own photo (same filename, square crop)

---

## License

Theme: MIT (Start Bootstrap). Content: © Bonifacio Conde Jr.
