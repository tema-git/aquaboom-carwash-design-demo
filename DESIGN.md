> Current model, approved 2026-11-07: Porsche 911 Carrera 4S by Karol Miklas / Lionsharp Studios (CC BY-SA 4.0), with approved runtime adaptations. Transfer all model/decoder assets and retain the attribution. The earlier Panamera design and propagation notes below are historical and superseded. Smaller car scenes and the wash game now reuse the same approved 3D geometry.

# AQUABOOM — a clean city reset

Independent Russian-language website concept for the car wash at Moscow, Kronshtadtskiy Boulevard, 35B. The main visitor task is to choose a service, find the business and call. The form is explicitly a demonstration and creates no appointment.

## Direction and critique

The memorable object is a large pearl car wrapped in clear water, against an icy canvas. The composition comes from the subject: a vehicle arriving from the city and leaving clean. The initial generic idea of four equal service cards was replaced with a large interactive care panel, an immersive blue wash scene and a continuous hose-controlled wash interaction. Headings remain readable HTML rather than text painted into images. No decorative crosshairs, ornamental plus signs, fake metrics or invented testimonials.

The hero pairs the short, oversized “Чистый кайф.” headline with the approved licensed 911 Carrera 4S. The GLB geometry retains its headlights, glass, wheels and body surfaces; water is a separate pair of SVG layers surrounding it. The section sequence alternates pale blue, white, full cobalt, white and deep navy; this is a progression in the wash experience rather than a repeated card layout. Rounded form and game surfaces differ from circular bubbles, pill buttons and unboxed text.

## Tokens

- Ink `#092554`: main text, final contact section.
- Cobalt `#165dff`: primary actions and selected water objects.
- Ice `#eaf5ff`: hero and care panel canvas.
- Pale `#f4f9ff`: game section and fields.
- Lime `#d7f76b`: the real phone action on navy and text selection on dark surfaces.
- Muted `#536b8c`: secondary text on light surfaces.

Manrope, locally hosted under SIL OFL, provides Cyrillic display and reading type. Display letter-spacing is intentionally tight; body and controls retain normal reading rhythm. Body is about 18 px, interactive labels at least 16 px, support copy at least 14 px. Fluid display headings scale down to 320 px.

The wide container is 1320 px; desktop margins are 56 px, mobile margins 18 px (14 px at 320 px). Sticky header height is exposed through `--header`, and native anchor scrolling accounts for it.

## References and adaptations

These sources informed original CSS/JS implementation; no library code was copied and no preview assets were reused.

- [SuperHi Plus / Refero](https://styles.refero.design/style/a1f9e844-c4b6-4526-9cfc-81208c50aee1): bold blue / ice panel rhythm and scale of typography. Adapted to clear water and automotive forms; omitted decorative emoji.
- [Pravah / Refero](https://styles.refero.design/style/30a8b128-a5bb-4d86-85eb-743b78091596): purposeful product diagrams and tonal section changes. Not its exact palette or small uppercase labels.
- [21st Spotlight](https://21st.dev/@ibelick/components/spotlight/border-only), [MIT source reviewed](https://raw.githubusercontent.com/ibelick/motion-primitives/main/components/core/spotlight.tsx): local pointer coordinate mapping to a decorative light. Reimplemented in vanilla JS with frame-coalesced updates; buttons and fields stay stationary.
- [Dice UI compare slider](https://diceui.com/docs/components/base/compare-slider): useful keyboard-controllable visual transformations. The site uses an original button-based wash interaction instead of importing React or slider dependencies.
- [MotionSites scroll lesson](https://motionsites.ai/lesson/build-scroll-animated-website-with-ai): separable scene and text, scroll progress controlling a visual transition. Implemented with lightweight CSS/SVG and a single requested animation frame rather than video-frame extraction.
- [21st Animated Feature Spotlight 3D](https://21st.dev/@ruixen.ui/components/animated-feature-spotlight3d): layered parallax and a separate shadow. The independently moving front/back water planes adapt this principle without copying the React component.
- [MotionSites 3D scroll](https://motionsites.ai/lesson/build-3d-scroll-animated-website-with-ai): develop a scene through scroll rather than playing a decorative loop. The water has three reversible phases, and the procedural car keeps its own camera and lighting. The page is never pinned or hijacked.

## Section interaction map

| Section | Input | Response / bounds | Touch and keyboard | Reduced motion |
| --- | --- | --- | --- | --- |
| Hero | Pointer and native scroll | Stable 3D mount; separate front/back water curves deform, highlights move, droplets converge then fall; water parallax ±9/5 px | Scroll also drives the scene on touch; anchor actions remain normal | Fixed car and assembled water |
| Care | Pointer; service tab | Light follows pointer, service object ±26/16 px; four service diagrams | Native tabs, Left/Right/Home/End, touch selection; selected service passes to form | Selection still changes; no travel |
| Wash ritual | Scroll from first viewport entry | Three phases: dispersed jets, wrapping translucent ribbons, then moving shine and draining droplets; stable SVG car | Native scrolling; prose is always visible | Fully assembled scene |
| Game | Hose strokes across the car | Detailed procedural car, foam coating, progressive rinse, dripping foam/water, attainable progress and replay | Pointer capture on scene only; focus scene and hold Space/Enter with arrows; tool buttons remain native | Static spray and paint feedback; no moving droplets |
| Questions | Pointer and native details | Decorative droplet ±20/8 px; answer expansion | Native summary controls; no hover dependency | Fixed droplet, instant state |
| Contacts | Pointer / focus | Decorative bubble rings ±25/20 px; no field movement | Actual contact links; demo form is keyboard/touch usable | Static bubble rings |

Entry progress is `(scrollY + viewportHeight - sectionTop) / (viewportHeight * 0.82)`, clamped. This starts as the section first enters the bottom of the viewport, assembles before it fills the screen, and reverses with native scroll. No whole-page pinning or scroll hijacking. Pointer geometry is measured outside the hot move handler. Animation frames run only for requested scroll/pointer updates, with intersection visibility filtering for pointer effects.

Water uses its own longer progress interval, spanning the scene's entrance and exit. `water-scenes.js` computes cubic Bézier ribbon geometry, gradient transforms, short traveling reflections, drain streaks and twelve deterministic droplets. Forward and backward scrolling restore the same shapes; there is no random frame loop. An 85 ms response smooths scroll samples and stops requesting frames once settled. Offscreen scenes skip SVG writes, and hidden tabs cancel pending frames. No large raster layer, video file, frame sequence or GPU filter is involved in the water. Foreground water remains below readable HTML and does not intercept input. The smaller ritual/game cars remain scalable inline vector artwork.

Motion follows `prefers-reduced-motion` without a visible settings control. The water stays assembled and the game remains playable with static spray feedback. A hose cursor appears only over the hero artwork and inside the wash scene; normal text, links and fields keep their ordinary cursor. Contacts has a fixed clickable rectangle with its inner label moving at most 4 px. Text selection changes letter color with a transparent background and no text shadow. Directional actions use the same SVG arrow, up-right at rest and right on hover/focus. The footer carries the Spoki Studio signature.

## Interactive block

“Смойте городской шум” is an original Canvas scene, not an image or video. The pearl-blue car is drawn from Bézier bodywork, separate glass, panel seams, lamps and ten-spoke wheels. Three in-memory procedural layers hold the clean car, road dirt and foam. Pointer strokes are interpolated at 18 world-pixel intervals so fast movement leaves continuous coverage. Foam coats the clipped silhouette; water erases the foam and dirt with a feathered brush. Only impacts whose centers lie inside the exact vehicle silhouette count. A grid sampled from that same path tracks unique covered/cleaned surface, so overspray and repeated strokes never inflate progress. At 94% physical coverage, the final fine residue clears and the meter reaches 100%, keeping both steps comfortably attainable.

The two visible tools are “Пена” and “Вода”. Water becomes available after the foam stage; the rinse reveals the original clean body. Soft foam drips, spray particles and a moving reflection give immediate physical feedback. There are at most 96 particles, no imported textures/models and no perpetual game loop. Frames stop when settled, offscreen or hidden; reduced motion keeps the actual painting and removes falling particles. Mouse and touch share Pointer Events; touch-action is disabled only on the game stage. The focused stage also supports arrows for nozzle position and held Space/Enter for spray, described through visually hidden accessible text. Progress is exposed through a progressbar, milestones and phase announcements. Replay resets layers, coverage, tools and particles.

The service field is enhanced from a native select into a styled select-only combobox. The native control remains the form value and no-JavaScript fallback. The popup supports pointer/touch selection, arrows, Home/End, type-ahead, Enter/Space, Escape, Tab, outside dismissal and reset. Its fixed portal lives under body, outside decorative overflow clipping. Visual viewport bounds, the sticky header and available space decide upward/downward placement and scrollable maximum height.

## Content and demo safety

Only published business contact data and broad service categories are used. No current tariff, rating, staff identity, guarantee, number of customers or years in business is claimed. The procedural cars are conceptual illustrations, not photographs of AQUABOOM premises or customers. The footer identifies this as an independent, unofficial concept. `noindex,nofollow` and robots disallow indexing.

The form validates a name and Russian phone number locally, exposes field errors with `aria-describedby` and `aria-invalid`, and clears personal fields before displaying success. Success explicitly states no data was sent and no appointment was created. A real phone link is provided. No fetch, analytics, cookies, localStorage or sessionStorage is used.


### Coupe geometry and resilience — voice audit, 4 November 2026
The hero car is now a compact fastback coupe, inspired by the low bonnet, oval lamps and wide rear shoulders of the [official 911 reference](https://www.porsche.com/international/models/911/carrera-models/911-carrera/). It is an original, unbranded procedural model; no photograph, imported model, video or texture is used. Body panels, conforming lamp lenses, roof arc, intakes, wheels, brake discs and fixed calipers are generated in JavaScript. Static meshes are merged by material, reducing the observed desktop renderer from 239 to 75 draw calls (including the shadow pass). Rendering remains event-driven and pauses offscreen.

The procedural PMREM lighting environment is regenerated after WebGL context restoration. Local UI tests explicitly lost and restored the context on both sites: SVG fallback appeared during loss, and the 3D model and metallic reflections returned after restoration. System prefers-reduced-motion still controls decorative motion; no manual toggle is exposed.


## Four-door sports saloon — 4 November 2026

Replaced the short coupé with an original procedural four-door fastback in `car-geometry.js`. The dimensional reference is the Panamera technical sheet: length 5.052 m, body width 1.937 m, height 1.423 m, wheelbase 2.950 m, tracks 1.680/1.651 m. Wheel centres and tyre diameter follow those proportions; overhang split, body surfaces and details are original visual approximations, not factory CAD.

Official visual references (reference only; no photography or manufacturer model is shipped):
- https://newsroom.porsche.com/dam/jcr:f70ca2d1-f5a5-4d16-a497-82d83f717aae/pag-panamera-td-en.pdf.PDF
- https://newsroom.porsche.com/en/press-kits/panamera/exterior-design.html
- https://newsroom.porsche.com/en/2023/products/porsche-panamera-world-premiere-shanghai-34450.html

The new body has a longer cabin, four separate doors, surface-conforming seams, distinct B-pillars and quarter-lights, a panoramic roof, swept four-module lamps, a continuous rear light bar, recessed intake panels, shaped tyre sidewalls, drilled brake discs and ten alloy spokes. Upper and side skin share boundary normals. Side window edging uses separate open curves to avoid folded triangles at sharp ends. No marque badge or affiliation claim is added.

`car-scene.js` preserves the existing cursor/scroll camera response, automatic viewport fitting, local Three.js 0.187.0 dependency, system reduced motion, offscreen suspension, context-loss fallback/recovery and disposal. The procedural studio lighting uses narrower reflections. Static meshes are batched by material: measured 59 draw calls and 319,046 submitted triangles including the shadow pass. There is no continuous idle render loop. The new four-door SVG fallback is embedded in the HTML and the runtime scene.

Visual QA inspected front three-quarter, side, rear three-quarter and front views, desktop 1440 and narrow 390 screenshots, and widths 320/800/1024. No horizontal page overflow was observed. Forms, service selection and interactive blocks were exercised after the change. Tests use browser viewports; physical iOS/Android devices and the live OS reduced-motion setting were not tested.

### Propagation to company copies

Copy `car-geometry.js` and `car-scene.js` together, retaining their relative paths and the hashed geometry import. In each company HTML, update only the `car-scene.js?v=…` query and the inline SVG inside `[data-car-scene]`. Preserve `data-car-scene="service"` or `"wash"`, `company.js`, contacts, brand text, palette and all company-specific content. Do not replace a copy's entire HTML. Three.js/vendor has not changed. Water and foam-game modules are independent and remain untouched. Verify the new module returns HTTP 200 and the host reaches `data-render-state="ready"`; fallback alone does not prove the model loaded.
