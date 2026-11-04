# AQUABOOM — independent car-wash website concept

Buildless HTML/CSS/JS, designed for GitHub Pages. Serve this directory over HTTP; there is no dependency installation or build step. Parent project owns Git repository creation and publication.

## Files

- `company.js`: business contact configuration and four service panels.
- `index.html`: semantic and no-JavaScript baseline, SEO metadata and SVG UI/scene symbols.
- `style.css`: responsive layout, visual system, pointer / scroll compositions and reduced-motion states.
- `app.js`: service tabs, local form validation and OS reduced-motion handling. No storage or network requests.
- `wash-game.js` / `wash-game.css`: procedural Canvas car wash, interpolated foam/water strokes, silhouette coverage, droplets, keyboard controls and replay.
- `interface.js`: accessible custom service picker backed by the native select, plus a fixed-target magnetic Contacts label.
- `water-scenes.js`: original layered SVG water, continuously reshaped by native scroll progress. No image sequence, video or animation dependency.
- `car-scene.js` and local `vendor/`: procedural Three.js hero car supplied by the parent task; geometry, paint, glass, wheels and lights are code, without image/model assets. The smaller cars are inline SVG.
- Local fonts are licensed by `assets/OFL-Manrope.txt`. The previous generated hero image is no longer referenced by the page.
- `SOURCE.json`: company source references and limits.
- `DESIGN.md`: visual decisions and interaction behavior.

## Preparing a later copy

Duplicate into a new directory and repository. Change `company.js` first. Update the static title, meta description, logo fallback and factual copy in `index.html` to match the target company. Review every service, do not merely replace the name. Replace source provenance, actual map link and image assets as appropriate. Keep the explicit concept/demo labeling until a real business handler is connected with authorization. Do not imply a submitted appointment exists without one.

Avoid copying `.git` or deployment credentials. All application links are relative, and `.nojekyll` supports root GitHub Pages publication.

## Browser verification targets

- Service tabs: `[data-service]`, expected `aria-selected`; arrow keys, Home and End supported. `#service` carries current choice into the demo form.
- Game: `#wash-stage` / `#wash-canvas`. Sweep the car with three broad horizontal strokes over roof, body and wheels. `data-phase` on `.wash-play` changes from `foam` to `foam-ready`; choose `[data-wash-tool="water"]`, repeat until `complete`. `#wash-percent` and `.wash-meter` give progress; `#wash-reset` restores the dirty car. Outside-silhouette strokes do not score. Keyboard: focus the stage; arrows move the nozzle, hold Space/Enter to spray. The instructions are screen-reader-only.
- Picker: `#service-picker`, `#service-options`, native hidden `#service`. Supports arrows, Home/End, typing, Enter/Space, Escape, Tab dismissal, pointer selection, outside dismissal and form reset.
- Form: `#booking-form`, `#name`, `#phone`, `#service`. Empty/short name and malformed phone show associated errors. Successful validation shows `#booking-success`, clears personal fields and explicitly says there was no sending or appointment. `#form-retry` restores the form.
- Motion: follows OS reduced motion, without a visible settings control. With motion on, `.hero-art` and `.ritual-scene` expose `data-water-progress` and `data-water-phase` (`arrive`, `wrap`, `drain`). Scroll forward/backward to verify different SVG path geometry and reflection positions; the car mount itself stays still. Water frames settle after scrolling and stop when the scene is outside the viewport or the tab is hidden. All essential content remains visible.
- Header: visible “Контакты” on desktop and 320 px mobile, sticky; target `#contacts` remains below header.

JavaScript syntax checks run with Node. Parent performs real desktop/mobile browser playthrough, form checks, screenshots and published-site verification before delivery.


### Updated procedural car

The hero now imports the shared four-door model from `car-geometry.js` through `car-scene.js`. Both files and their cache hashes must travel together when updating a company copy. Preserve the company's HTML/branding and update only the module reference and inline fallback; see the propagation notes in `DESIGN.md`. No new package or remote asset is required.
