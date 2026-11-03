# AQUABOOM — a clean city reset

Independent Russian-language website concept for the car wash at Moscow, Kronshtadtskiy Boulevard, 35B. The main visitor task is to choose a service, find the business and call. The form is explicitly a demonstration and creates no appointment.

## Direction and critique

The memorable object is a large pearl car wrapped in clear water, against an icy canvas. The composition comes from the subject: a vehicle arriving from the city and leaving clean. The initial generic idea of four equal service cards was replaced with a large interactive care panel, an immersive blue wash scene and a real two-step mini-game. Headings remain readable HTML rather than text painted into images. No decorative crosshairs, ornamental plus signs, fake metrics or invented testimonials.

The hero pairs the short, oversized “Чистый кайф.” headline with a broad car image. The section sequence alternates pale blue, white, full cobalt, white and deep navy; this is a progression in the wash experience rather than a repeated card layout. Rounded form and game surfaces differ from circular bubbles, pill buttons and unboxed text.

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

## Section interaction map

| Section | Input | Response / bounds | Touch and keyboard | Reduced motion |
| --- | --- | --- | --- | --- |
| Hero | Pointer and entry scroll | Car ±20/10 px, bubbles ±32 px, halo and rings | Static rich composition; anchor actions remain normal | Fixed composition |
| Care | Pointer; service tab | Light follows pointer, service object ±26/16 px; four service diagrams | Native tabs, Left/Right/Home/End, touch selection; selected service passes to form | Selection still changes; no travel |
| Wash ritual | Scroll while section enters viewport | Water streams begin dispersed ±250 px and converge early; car, foam and halo respond within bounds | Native scrolling; prose is always visible | Fully assembled scene |
| Game | Native zone button activation | Six foam zones, then six rinse zones, explicit win and progress | Mouse, touch, Tab + Enter/Space; no drag required | State feedback preserved |
| Questions | Pointer and native details | Decorative droplet ±20/8 px; answer expansion | Native summary controls; no hover dependency | Fixed droplet, instant state |
| Contacts | Pointer / focus | Decorative bubble rings ±25/20 px; no field movement | Actual contact links; demo form is keyboard/touch usable | Static bubble rings |

Entry progress is `(scrollY + viewportHeight - sectionTop) / (viewportHeight * 0.82)`, clamped. This starts as the section first enters the bottom of the viewport, assembles before it fills the screen, and reverses with native scroll. No whole-page pinning or scroll hijacking. Pointer geometry is measured outside the hot move handler. Animation frames run only for requested scroll/pointer updates, with intersection visibility filtering for pointer effects.

The footer “Анимация” control toggles motion at runtime; its initial state follows `prefers-reduced-motion`. There is no custom cursor. Text is selectable: selection changes letter color with a transparent background and no text shadow. Every directional action uses the same SVG arrow, up-right at rest and horizontal right on hover/focus. No scroll rotation is attached to UI arrows.

## Interactive block

“Смойте городской шум” models a deliberately simple, illustrative wash, not professional advice. Six buttons name car zones. In step 1 each receives foam once; after six unique actions the phase changes automatically. In step 2 each is rinsed once; completion yields a visible result. Reset is always available. State changes synchronously, duplicate clicks on completed zones are ignored, and keyboard focus stays on native controls. No timer pressure or pointer dragging is required.

## Content and demo safety

Only published business contact data and broad service categories are used. No current tariff, rating, staff identity, guarantee, number of customers or years in business is claimed. The generated image is a conceptual car visualization, not a photograph of AQUABOOM premises or customers. The footer identifies this as an independent, unofficial concept. `noindex,nofollow` and robots disallow indexing.

The form validates a name and Russian phone number locally, exposes field errors with `aria-describedby` and `aria-invalid`, and clears personal fields before displaying success. Success explicitly states no data was sent and no appointment was created. A real phone link is provided. No fetch, analytics, cookies, localStorage or sessionStorage is used.
