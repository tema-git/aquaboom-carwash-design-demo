# AQUABOOM — independent car-wash website concept

Buildless HTML/CSS/JS, designed for GitHub Pages. Serve this directory over HTTP; there is no dependency installation or build step. Parent project owns Git repository creation and publication.

## Files

- `company.js`: business contact configuration and four service panels.
- `index.html`: semantic and no-JavaScript baseline, SEO metadata and SVG UI/scene symbols.
- `style.css`: responsive layout, visual system, pointer / scroll compositions and reduced-motion states.
- `app.js`: service tabs, two-stage wash game, native form validation and motion toggle. No storage or network requests.
- `assets/hero-car.webp`: generated transparent hero artwork supplied by the parent task. `assets/image-provenance.json` records provenance; local fonts are licensed by `assets/OFL-Manrope.txt`.
- `SOURCE.json`: company source references and limits.
- `DESIGN.md`: visual decisions and interaction behavior.

## Preparing a later copy

Duplicate into a new directory and repository. Change `company.js` first. Update the static title, meta description, logo fallback and factual copy in `index.html` to match the target company. Review every service, do not merely replace the name. Replace source provenance, actual map link and image assets as appropriate. Keep the explicit concept/demo labeling until a real business handler is connected with authorization. Do not imply a submitted appointment exists without one.

Avoid copying `.git` or deployment credentials. All application links are relative, and `.nojekyll` supports root GitHub Pages publication.

## Browser verification targets

- Service tabs: `[data-service]`, expected `aria-selected`; arrow keys, Home and End supported. `#service` carries current choice into the demo form.
- Game: click each `[data-zone="0"]` through `5` once for foam. Then click each once again for rinse. `.wash-game[data-phase="complete"]` and full progress indicate victory. `#game-reset` restarts. Rapid repeated clicks cannot increment completed zones twice.
- Form: `#booking-form`, `#name`, `#phone`, `#service`. Empty/short name and malformed phone show associated errors. Successful validation shows `#booking-success`, clears personal fields and explicitly says there was no sending or appointment. `#form-retry` restores the form.
- Motion: footer `#motion-toggle`, `aria-pressed`; default follows OS reduced motion. All essential content remains visible.
- Header: visible “Контакты” on desktop and 320 px mobile, sticky; target `#contacts` remains below header.

JavaScript syntax checks run with Node. Parent performs real desktop/mobile browser playthrough, form checks, screenshots and published-site verification before delivery.
