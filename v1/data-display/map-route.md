# Map Route

> Purpose: Route line map: path polyline from waypoint tokens, start and end pins, segment list, distance readout, table alternative.
> Section: data-display | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: map-route. Section: data-display. Route line map: path polyline from waypoint tokens, start and end pins, segment list, distance readout, table alternative.

## 2. Anatomy (parts, ASCII diagram ok)

```
+-----------------------------+
|  o---.                      |
|      \---.                |
|          \---o            |
|  segments: 3 rows           |
+-----------------------------+
table alt link
```

- **map**: base map, regions from --chart-* tokens
- **route**: path polyline, stroke --color-accent, --icon-stroke-regular
- **pins**: start and end pins, Lucide map-pin, --icon-size-lg
- **segments**: segment list with distances, --text-xs --font-mono
- **table alt**: data table alternative, --radius-none

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hovered-click | --cursor-pointer | --color-surface-sunken + --opacity-pressed overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| pressed/active | N/A: map-route has no press phase, it commits on click | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no hover fill |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no press |
| selected/checked | --cursor-default | --color-brand-soft | hairline --color-border-strong | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=true |
| unselected | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=false |
| expanded/collapsed | N/A: map-route has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: map-route is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | N/A: map-route is not a menu, it has no item activation | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | N/A: map-route does not navigate, no current-page concept | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no navigation semantics |
| visited | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-secondary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | history visited, no style-only meaning |
| invalid + disabled | N/A: map-route holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: map-route is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: map-route takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide inbox, --color-text-tertiary | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=status 'No items' |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-*, --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |
| success | --cursor-default | --color-surface-raised | hairline --color-success | --color-text-primary | Lucide check-*, --color-success | none at --duration-instant | --sound-success token if user enabled | role=status announced once |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for map-route are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-lg | rest |
| hover-segment | --color-surface-raised | --color-text-primary | hairline --color-accent | --radius-lg | segment hover |
| selected | --color-brand-soft | --color-text-primary | hairline --color-border-strong | --radius-lg | route chosen |
| error | --color-surface-raised | --color-error | hairline --color-error | --radius-lg | load failed |

Sizes: map min height --space-* tokens; route stroke --icon-stroke-regular; pins --icon-size-lg; segment rows >= --touch-target-min; distances --text-xs --font-mono.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab reaches segment links and table alt; Enter selects segment; arrows move segment focus; Escape closes tooltip; no keyboard path into map pixels.
- Mouse: hover segment highlights --color-brand-soft; click selects; scroll zooms with button alternative; drag pans; right-click native menu.
- Touch: pinch zoom optional with buttons; tap segment shows tooltip; pan with drag; targets >= --touch-target-min.
- Dismiss: tooltip closes on Escape + outside + scroll; focus returns to segment.
- Offline: cached route renders, --color-warning marker, queue refreshes, replay on reconnect.
- Debounce: segment select debounces --duration-debounce-input; async route load shows skeleton map.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over map |
| hover | --cursor-pointer | segment wash --color-brand-soft | over segment |
| pressed/active | --cursor-pointer | --opacity-pressed fill | during select |
| disabled | --cursor-not-allowed | pointer-events none | when disabled |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus |
| loading | --cursor-progress | frame shimmer --duration-skeleton-shimmer | async data |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Segment select -> --sound-click, route load error -> --sound-error, at --sound-volume user opt-in. Haptics: --haptic-light on select. No sound on hover of route.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | map full width, controls stack, legend below | width 100% minus --space-4 gutters |
| tablet (--bp-sm..--bp-lg) | map full width, controls inline, legend side | fluid minmax tokens |
| desktop (>= --bp-lg) | map max --measure-reading, controls inline, legend top | same scale |

Fluid rules: no fixed px; all widths from --space-* / --measure-* / --bp-* tokens; text wraps, never truncates without ellipsis policy; horizontal scroll only inside scroll-region; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Route runs inline-start to inline-end; pins stay put; segment list follows DOM order and mirrors in RTL; distances stay LTR; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-raised, --color-surface-sunken, --color-surface-overlay, --color-brand-soft, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-text-disabled, --color-accent, --color-error, --color-warning, --color-success, --color-border, --color-border-strong, --color-border-focus, --color-skeleton-base, --color-skeleton-shine, --chart-1.--chart-12, --opacity-hover, --opacity-pressed, --opacity-selected, --opacity-disabled, --radius-lg, --radius-sm, --shadow-md, --shadow-focus-glow, --space-1.--space-6, --text-xs/sm/base, --weight-medium, --font-ui, --font-mono, --leading-normal, --duration-fast, --duration-normal, --duration-debounce-input, --duration-skeleton-shimmer, --ease-standard, --icon-size-sm/lg, --icon-stroke-thin/regular, --touch-target-min, --cursor-default/pointer/not-allowed/progress, --sound-click/error, --sound-volume, --motion-reduced, --bp-sm/md/lg, --measure-reading, --z-popover.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; ship all 26 states; route stroke from --color-accent only; keep tooltip inside viewport; announce select via aria; hold 40% expansion; print as labeled list.
Do not: hardcode a segment distance; use color alone; hide the ring; trap focus; autoplay sound; ship without frame skeleton; let tooltip overflow; use a rainbow ramp.
Premium treatment: calm map at rest, refined hover as segment wash, tactile select press, crisp ring, graceful disabled, loading frame matching final map height with zero shift.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- map: role=img, aria-label route map title + summary, table alt linked
- route: role=img, aria-label route path
- segment: role=button or listitem, aria-label segment name + distance, aria-selected
- tooltip: role=tooltip, aria-hidden when closed
- table alt: role=region, aria-label data table

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on segment links and table alt, never outline:none; map pixels never focusable.
Contrast: AA 4:5:1 segment labels, distances, tooltip, table alt both themes; selected --color-brand-soft with --color-text-primary 13.40:1; error AA; focus 3:1; dark/light swap is the token swap.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Segment names, distances, tooltip text: externalized, 40% expansion, ellipsis policy.
- Distances per locale number format; segment counts plural-safe.
- Bidi isolate spans; RTL mirrors segment list order.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: route prints as dashed line, segments print as list with distances, tooltip not printed, no ring, no shimmer, map prints framed.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Map: full-width block at map min height, radius --radius-lg, --color-skeleton-base
- Route: bar width 60% at --space-1 height, --color-skeleton-base
- Pins: 2 squares --icon-size-lg at route ends, --color-skeleton-base
- Segments: 3 bars at --text-xs height, --color-skeleton-base

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced. aria-busy=true while loading, role=status announcement when content lands. Offline/error: skeleton replaced by state panel per section 3.

## 16. Icon usage (Lucide names only)

- map-pin for start and end, navigation for route, alert-circle for error, list for table alt
- Lucide only, --icon-size-lg / --icon-size-sm

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'map-route' component per data-display/map-route.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

