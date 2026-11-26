# Chart Funnel

> Purpose: funnel chart: series from --chart-* tokens, axis/grid/legend from surface/text/border tokens, tooltip per point, table alternative, dark/light palette swap, print as labeled list.
> Section: data-display | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: chart-funnel. Section: data-display. funnel chart: series from --chart-* tokens, axis/grid/legend from surface/text/border tokens, tooltip per point, table alternative, dark/light palette swap, print as labeled list.

## 2. Anatomy (parts, ASCII diagram ok)

```
+-----------------------------+
| legend  [swatch] series a   |
+-----------------------------+
|                             |
|   funnel plot area          |
|   series from --chart-*     |
|                             |
+-----------------------------+
axis ticks --text-xs  tooltip on hover
```

- **plot**: the funnel area, series colors --chart-1..--chart-12, baseline zero unless token says otherwise
- **axis**: category + value axes, ticks --text-xs --color-text-tertiary, grid hairlines --color-border Stages top to bottom, width from value token, stage label --text-sm outside.
- **legend**: series key, Lucide swatch + text, toggleable, --text-sm
- **tooltip**: per-point panel at --z-popover, --color-surface-overlay, --shadow-md
- **state**: loading skeleton frame, empty illustration + action, error panel + retry

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hovered-click | --cursor-pointer | --color-surface-sunken + --opacity-pressed overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| pressed/active | N/A: chart-funnel has no press phase, it commits on click | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no hover fill |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no press |
| selected/checked | --cursor-default | --color-brand-soft | hairline --color-border-strong | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=true |
| unselected | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=false |
| expanded/collapsed | N/A: chart-funnel has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: chart-funnel is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | N/A: chart-funnel is not a menu, it has no item activation | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | N/A: chart-funnel does not navigate, no current-page concept | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no navigation semantics |
| visited | N/A: chart-funnel is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: chart-funnel holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: chart-funnel is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: chart-funnel takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide inbox, --color-text-tertiary | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=status 'No items' |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-*, --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |
| success | --cursor-default | --color-surface-raised | hairline --color-success | --color-text-primary | Lucide check-*, --color-success | none at --duration-instant | --sound-success token if user enabled | role=status announced once |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for chart-funnel are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-lg | rest |
| hover-point | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-lg | tooltip open |
| selected-series | --color-brand-soft | --color-text-primary | hairline --color-border-strong | --radius-lg | series toggled on |
| hidden-series | --color-surface-raised | --color-text-tertiary | hairline --color-border | --radius-lg | series toggled off |
| error | --color-surface-raised | --color-error | hairline --color-error | --radius-lg | load failed |

Sizes: plot min height --space-* tokens; legend rows >= --touch-target-min when toggleable; axis text --text-xs; tooltip max --measure-reading; width fluid via clamp. 

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab reaches legend toggles and chart controls; Enter toggles series; arrows move point focus where declared; Escape closes tooltip; no keyboard path into plot pixels; table alternative linked.
- Mouse: hover point shows tooltip at --z-popover; click toggles series from legend; drag pan/zoom only where declared with button alternative; wheel zoom optional with buttons; right-click native menu.
- Touch: legend rows >= --touch-target-min; tap point shows tooltip; pinch zoom optional with buttons; no hover-only data; long-press not used.
- Dismiss: tooltip closes on Escape + outside + scroll; legend popover closes on Escape + outside; focus returns to trigger.
- Offline: last-good data renders with --color-warning marker; queue refreshes, replay on reconnect; never fake data.
- Data: color-by-series from --chart-1..12 only, never by category name; axis, grid, legend, tooltip colors from surface/text/border tokens; animation on data change --duration-normal, off under --motion-reduced. No axis pan; tooltip per slice or cell.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over plot |
| hover | --cursor-crosshair | tooltip open at point | over data point |
| pressed/active | --cursor-pointer | --opacity-pressed fill | during legend toggle |
| disabled | --cursor-not-allowed | pointer-events none | when chart disabled |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus on legend |
| loading | --cursor-progress | frame shimmer --duration-skeleton-shimmer | async data |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Legend toggle -> --sound-toggle, point select -> --sound-click, error load -> --sound-error, at --sound-volume user opt-in. Haptics: --haptic-light on point select. No sound on hover of data points; no autoplay animation sound.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | legend below plot, labels --text-xs, table alternative | width 100% |
| tablet (--bp-sm..--bp-lg) | legend side, labels --text-xs | fluid |
| desktop (>= --bp-lg) | legend top, full labels, tooltip | max --measure-reading |

Fluid rules: no fixed px; all widths from --space-* / --measure-* / --bp-* tokens; text wraps, never truncates without ellipsis policy; horizontal scroll only inside scroll-region; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

X axis mirrors for RTL datasets only where data is directional; legend order mirrors; tooltip anchors to point edge; chart data itself never mirrored; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-raised, --color-surface-sunken, --color-surface-overlay, --color-brand-soft, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-text-disabled, --color-primary, --color-accent, --color-error, --color-success, --color-warning, --color-info, --color-border, --color-border-strong, --color-border-focus, --color-skeleton-base, --color-skeleton-shine, --chart-1.--chart-12, --opacity-hover, --opacity-pressed, --opacity-selected, --opacity-disabled, --radius-lg, --radius-sm, --shadow-md, --shadow-focus-glow, --space-1.--space-8, --text-xs/sm/base, --weight-medium, --font-ui, --font-mono, --leading-normal, --duration-fast, --duration-normal, --duration-skeleton-shimmer, --ease-standard, --icon-size-sm/md, --icon-stroke-thin/regular, --touch-target-min, --cursor-default/pointer/crosshair/not-allowed/progress, --sound-toggle/click/error, --sound-volume, --motion-reduced, --bp-sm/md/lg, --measure-reading, --z-popover.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; ship all 26 states; color-by-series only; keep tooltip inside viewport; announce series toggle via aria; hold 40% expansion; print as labeled list.
Do not: hardcode a series color; use color alone; hide the ring; trap focus; autoplay sound; ship without frame skeleton; let tooltip overflow the viewport; use a rainbow ramp.
Premium treatment: calm plot at rest, refined hover as tooltip elevation never a color jump, tactile legend press, crisp ring, graceful disabled legend, loading frame matching final plot height with zero shift.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- chart: role=img, aria-label chart title + summary, table alternative linked
- legend: role=button or checkbox, aria-pressed for series visibility
- tooltip: role=tooltip, aria-hidden when closed, name from point data
- error: role=alert, announced once
- table alt: role=region, aria-label data table

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on legend toggles and chart controls, never outline:none; plot pixels never focusable.
Contrast: AA 4:5:1 axis, legend, tooltip text both themes; series colors pair with legend text, never color alone; tooltip on overlay verified; focus 3:1; dark/light swap is the token swap.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Title, legend labels, tooltip text, empty/error text: externalized, 40% expansion, ellipsis policy, no mid-word break.
- Number and date formats per locale tokens; axis tick labels per locale; plural-safe series counts.
- Bidi isolate spans; RTL mirrors legend order; numbers stay locale-formatted.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: series print as pattern-filled outlines or direct labels, legend prints with text, tooltip not printed, no ring, no shimmer, chart prints framed; table alternative prints as the data list.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Frame: full-width block at plot min height, radius --radius-lg, --color-skeleton-base
- Axis ticks: 4 bars --text-xs height at bottom, --color-skeleton-base
- Legend rows: 3 bars at --text-sm height, --color-skeleton-base
- Tooltip: width 30% bar at --text-xs, --color-skeleton-base

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced (static gray). No pulse on text. aria-busy=true while loading, role=status announcement when content lands, skeleton never read as content. Offline/error: skeleton replaced by state panel per section 3, not by blank.

## 16. Icon usage (Lucide names only)

- stage sample: trapezoid fill --chart-1, stage label --text-sm
- Lucide only, --icon-size-sm / --icon-size-md

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'chart-funnel' component per data-display/chart-funnel.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

