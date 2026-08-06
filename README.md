# Bonifacio Conde Jr — Online CV

Source for my online CV, deployed to GitHub Pages.

**Live:** https://bonifacioconde.github.io

Built on the [Start Bootstrap Resume](https://startbootstrap.com/theme/resume) theme (Pug + Sass + Bootstrap 5).

---

## Editing the content

All content lives in **`src/pug/index.pug`**. Edit that file, not `docs/index.html` — `docs/` is generated and gets overwritten on every build.

Styling lives in `src/scss/`:

- `src/scss/variables/_colors.scss` — theme colors
- `src/scss/variables/_typography.scss` — fonts
- `src/scss/sections/_resume-section.scss` — section layout
- `src/scss/components/_sidenav.scss` — the fixed sidebar nav

Profile photo: `src/assets/img/profile.jpg` (square, 500×500 or larger). The build copies it into `docs/`.

---

## Local development

```bash
npm install
npm start        # builds and serves at http://localhost:3000 with live reload
npm run build    # one-off build into docs/
```

Requires Node 18+.

---

## Deployment

GitHub Pages serves the site **directly from the committed `docs/` folder** on `master`.
There is no deployment pipeline — pushing the built files *is* the deploy.

Repo setting, once: **Settings → Pages → Build and deployment → Source → Deploy from a
branch → Branch: `master`, Folder: `/docs`**.

**Publishing a change:**

```bash
# edit src/pug/index.pug
npm run build          # regenerates docs/
git add -A
git commit -m "..."
git push               # live in ~30s
```

The one hazard of this setup is pushing a source change without rebuilding, which leaves the
published site stale. `.github/workflows/verify.yml` guards against that: it rebuilds on every
push and fails if `docs/` doesn't match `src/`.

> Previously this used an Actions-based Pages deployment (`actions/deploy-pages`). Deployments
> were accepted by the API but sat in `deployment_queued` indefinitely and never published, on
> two separate repositories, with GitHub Pages reporting Operational. Serving straight from a
> branch avoids the deployment API entirely.

---

## Notes for future me

- **Shipped Apps section** is commented out at the bottom of `src/pug/index.pug`. To bring it
  back, uncomment the block and restore its nav item:
  `li.nav-item > a.nav-link.js-scroll-trigger(href='#shipped') Shipped`
- **Font Awesome** is loaded as the CSS build from cdnjs, not the JS build the theme ships with.
  The JS build silently fails to render icons when the page is opened over `file://`.
- **`scripts/render-pug.js`** uses `htmlWhitespaceSensitivity: 'css'` (the theme default was
  `'ignore'`). With `'ignore'`, Prettier breaks lines after inline tags like `</strong>`, and the
  browser collapses that newline into a visible space before the following punctuation.
- Keep bullets to claims that can be backed up if asked in an interview.

---

## License

Theme: MIT (Start Bootstrap). Content: © Bonifacio Conde Jr.
