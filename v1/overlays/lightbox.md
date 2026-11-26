# Lightbox

> Purpose: Image viewer at --z-modal over scrim dim, main image with caption, zoom and close, arrow navigation between items.
> Section: overlays | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: lightbox. Section: overlays. Image viewer at --z-modal over scrim dim, main image with caption, zoom and close, arrow navigation between items.

## 2. Anatomy (parts, ASCII diagram ok)

```
+-----------------------------------------+
| x                                         |
|   [ image centers here ]                  |
|                                           |
| caption text                              |
| <   image nav   >                         |
+-----------------------------------------+
```

- **container**: --color-surface-overlay at --z-modal, dark surround
- **image**: main image, max width --measure-reading, zoom where declared
- **close**: Lucide x, --touch-target-min, dismisses on press
- **caption**: --text-sm --color-text-secondary, describedby on image
- **nav**: Lucide chevron-left / chevron-right, --touch-target-min

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hovered-click | --cursor-pointer | --color-surface-sunken + --opacity-pressed overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| pressed/active | N/A: lightbox has no press phase, it commits on click | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no hover fill |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no press |
| selected/checked | N/A: lightbox carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| unselected | N/A: lightbox carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| expanded/collapsed | N/A: lightbox has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | --cursor-default | --color-surface-overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | enter --motion-enter, exit --motion-exit | silent (sound events only via --sound-* tokens, user opt-in) | aria-hidden when closed, role=dialog when open |
| active menu item | N/A: lightbox is not a menu, it has no item activation | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | N/A: lightbox does not navigate, no current-page concept | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no navigation semantics |
| visited | N/A: lightbox is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: lightbox holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: lightbox is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: lightbox takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | N/A: lightbox renders fixed content, an empty data set cannot occur | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no data semantics |
| error | N/A: lightbox fetches nothing, no error state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no error semantics |
| success | N/A: lightbox completes no async work, no success state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no success semantics |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for lightbox are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-overlay | --color-text-primary | hairline --color-border-strong | --radius-lg | standard lightbox |
| caption | --color-surface-overlay | --color-text-primary | hairline --color-border-strong | --radius-lg | lightbox with caption |
| compact | --color-surface-overlay | --color-text-primary | hairline --color-border | --radius-md | small lightbox |

Sizes: image max width --measure-reading, close target >= --touch-target-min, nav target >= --touch-target-min, caption --text-sm.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Escape closes and returns focus to trigger, arrows navigate items, Tab cycles close and nav.
- Mouse: click image toggles zoom where declared, click close dismisses, click scrim dismisses where declared, arrows navigate.
- Touch: pinch to zoom with button alternative, swipe between items, targets >= --touch-target-min, outside tap dismisses where declared.
- Dismiss: Escape + close + scrim tap where declared, focus returns to trigger, change announced politely.
- Offline: images cached, navigation queued, replayed on reconnect.
- Debounce: zoom and nav debounce --duration-fast, async image skeleton lightbox.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over image |
| hover | --cursor-zoom-in | zoom affordance | over image |
| hover | --cursor-pointer | --opacity-hover fill | over close or nav |
| pressed/active | --cursor-pointer | --opacity-pressed fill | during press |
| disabled | --cursor-not-allowed | pointer-events none | when disabled |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | on focused control |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Close -> --sound-click; image change -> none; error -> --sound-error. Haptics: --haptic-light on navigation. No sound on hover.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | image fills stage minus --space-safe-top/bottom, chrome collapses to one row | width 100% minus --space-4 gutters |
| tablet (--bp-sm..--bp-lg) | image max width --measure-reading centered, side chrome hidden | fluid minmax tokens |
| desktop (>= --bp-lg) | image fluid to --grid-max-width, full chrome visible | same scale, no layout shift |

Fluid rules: no fixed px; image from --measure-* tokens, chrome from --space-* tokens, collapse then stack then hide.

## 9. RTL mirror behavior (what flips, what stays)

Image stays directionless, chevrons swap inline edges in RTL, caption follows bidi, no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-overlay, --color-scrim, --opacity-scrim, --color-text-primary, --color-text-secondary, --color-border, --color-border-strong, --color-border-focus, --radius-lg, --radius-md, --shadow-lg, --shadow-scrim, --shadow-focus-glow, --space-4.--space-8, --space-safe-top/bottom, --text-sm/base, --weight-medium, --font-ui, --leading-normal, --duration-fast, --duration-skeleton-shimmer, --ease-standard, --cursor-default/zoom-in/pointer/not-allowed/progress, --sound-click/error, --sound-volume, --motion-reduced, --bp-sm, --bp-lg, --touch-target-min, --z-modal.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; label image via aria; return focus to trigger; announce item index; hold 40% expansion.
Do not: hardcode image size; use color alone for state; hide the ring; trap focus without escape path; autoplay sound; ship without scrim; let content overflow viewport.
Premium treatment: premium zoom press via --ease-standard, crisp ring, zero layout shift on open.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- container: role=dialog, aria-modal=true, aria-label lightbox
- image: role=img, aria-label image, aria-describedby caption
- close: role=button, aria-label close lightbox, --touch-target-min
- nav: role=button, aria-label previous or next image, --touch-target-min
- caption: id referenced by aria-describedby on image

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on the focused control inside the lightbox, never outline:none.
Contrast: AA 4.5:1 caption on overlay both themes; controls 3:1; focus ring 3:1; --color-text-primary on --color-surface-overlay verified.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Caption, close label, nav labels: externalized, 40% expansion, ellipsis policy, no mid-word break.
- Lightbox open and image change announcements per locale token.
- Bidi isolate spans; RTL mirrors nav edges and caption alignment.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Prints grayscale image placeholder, caption text, no ring or controls, page breaks avoided inside image.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Panel: full-width block at --radius-lg, --color-skeleton-base
- Image: block max width --measure-reading, --color-skeleton-base
- Close: square --touch-target-min at inline-end, --color-skeleton-base
- Caption: width 60% bar at --text-sm, --color-skeleton-base
- Nav: squares --touch-target-min at row ends, --color-skeleton-base

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced static gray. aria-busy=true while loading, role=status announcement when content lands, skeleton never read as content.

## 16. Icon usage (Lucide names only)

- x for close at --icon-size-md
- chevron-left and chevron-right for nav at --icon-size-md
- Lucide only, --icon-size-md

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'lightbox' component per overlays/lightbox.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

