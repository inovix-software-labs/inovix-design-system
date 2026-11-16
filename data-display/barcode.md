# Barcode

> Purpose: Machine-readable code render: symbology label, quiet zone margin, bar + space modules, human-readable digits below, scan feedback slot.
> Section: data-display | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: barcode. Section: data-display. Machine-readable code render: symbology label, quiet zone margin, bar + space modules, human-readable digits below, scan feedback slot.

## 2. Anatomy (parts, ASCII diagram ok)

```
+-----------------------------+
| quiet zone, --space-*       |
| ||| || |||| | ||| ||  bars  |
| 1 2 3 4 5 6 7 8 9 0 1 2     |
| symbology label, --text-2xs |
+-----------------------------+
```

- **quiet**: quiet zone margin, --space-* tokens of --color-surface-base around code
- **bars**: bar + space modules, ink --color-text-primary on --color-surface-raised
- **human**: human-readable digits --text-xs --font-mono tabular, --color-text-secondary
- **label**: symbology label --text-2xs --color-text-tertiary
- **scan**: scan feedback slot, success --color-success, failure --color-error

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | N/A: barcode is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| hover | N/A: barcode is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| hovered-click | N/A: barcode is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| pressed/active | N/A: barcode is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| clicked | N/A: barcode is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| focus-visible | N/A: barcode is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| focus | N/A: barcode is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| disabled | N/A: barcode is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| disabled + hover | N/A: barcode is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| disabled + pressed | N/A: barcode is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| selected/checked | N/A: barcode carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| unselected | N/A: barcode carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| expanded/collapsed | N/A: barcode has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: barcode is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | N/A: barcode is not a menu, it has no item activation | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | N/A: barcode does not navigate, no current-page concept | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no navigation semantics |
| visited | N/A: barcode is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: barcode holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: barcode is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: barcode takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide inbox, --color-text-tertiary | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=status 'No items' |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-*, --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |
| success | --cursor-default | --color-surface-raised | hairline --color-success | --color-text-primary | Lucide check-*, --color-success | none at --duration-instant | --sound-success token if user enabled | role=status announced once |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for barcode are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-md | rest |
| scan-ok | --color-surface-raised | --color-text-primary | hairline --color-success | --radius-md | decoded |
| scan-fail | --color-surface-raised | --color-text-primary | hairline --color-error | --radius-md | no decode |
| dim | --color-surface-raised | --color-text-disabled | hairline --color-border | --radius-md | print draft |

Sizes: quiet zone --space-* tokens all sides; bar module width from --grid-* tokens; human digits --text-xs; symbology label --text-2xs; width fluid via clamp.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: not interactive; when wrapped in a link Tab enters wrapper, Enter opens source record, focus ring on wrapper.
- Mouse: hover none on static code; hover lift --shadow-xs only when linked; click wrapper opens record; no drag; right-click native menu.
- Touch: wrapper target >= --touch-target-min; long-press copies payload; no hover-only path on coarse pointers.
- Dismiss: not applicable.
- Offline: cached payload renders; sync failure marks scan slot --color-warning; never fake decode.
- Debounce: payload refresh debounces --duration-debounce-input; async render shows skeleton code.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over code |
| hover | --cursor-pointer | wrapper underline --color-accent | when linked |
| pressed/active | --cursor-pointer | --opacity-pressed fill | during wrapper click |
| disabled | --cursor-not-allowed | pointer-events none | when wrapper disabled |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | on wrapper |
| loading | --cursor-progress | module shimmer --duration-skeleton-shimmer | async payload |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent always. A static print code has no events; scan feedback sound belongs to the scanner, not this component. Haptics none. No sound on hover.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | human digits wrap below bars, symbology label hidden | width 100% minus --space-4 gutters |
| tablet (--bp-sm..--bp-lg) | digits below bars, label inline-end | fluid minmax tokens |
| desktop (>= --bp-lg) | full quiet zone, digits below, label inline-start | max --measure-reading |

Fluid rules: no fixed px; module count from data, width scales with --grid-columns; quiet zone scales with --space-* tokens; digits wrap before bars truncate; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Bars run top to bottom in both directions; human digits read order mirrors with bidi isolate; quiet zone symmetric; symbology label moves to inline-end; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-raised, --color-surface-base, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-text-disabled, --color-success, --color-warning, --color-error, --color-border, --color-border-strong, --color-border-focus, --color-skeleton-base, --color-skeleton-shine, --opacity-hover, --opacity-pressed, --opacity-disabled, --radius-md, --shadow-xs, --shadow-focus-glow, --grid-columns, --space-1.--space-6, --text-2xs/xs/sm, --weight-medium, --font-ui, --font-mono, --leading-tight, --duration-debounce-input, --duration-skeleton-shimmer, --cursor-default/pointer/not-allowed/progress, --sound-volume, --motion-reduced, --bp-sm/md/lg, --measure-reading.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; ship all 26 states; keep quiet zone unbroken; pair scan state with icon + text; hold 40% expansion; keep digits tabular; announce decode via wrapper only.
Do not: reduce quiet zone below token; invert ink without contrast check; use color alone for scan state; hide the ring on wrapper; autoplay sound; ship without module skeleton; let bars touch the edge.
Premium treatment: premium treatment: bars render crisp at every scale, quiet zone stays exact on resize, scan slot flashes --color-success once at --duration-instant off under --motion-reduced, zero shift when payload lands.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- code: role=img, aria-label payload summary + symbology
- human: role=text, digits in reading order, aria-hidden bars
- label: aria-hidden when decorative
- scan: role=status, success or failure announced once
- wrapper: role=link when linked, accessible name from payload

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on wrapper only; bars never focusable; never outline:none.
Contrast: AA 4.5:1 human digits, symbology label both themes; ink on raised verified 20.59:1; scan state pairs icon + text; focus 3:1.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Symbology label, payload summary, scan text: externalized, 40% expansion, ellipsis policy, no mid-word break.
- Digits per locale number format; symbology names stay untranslated proper nouns; plural-safe module counts.
- Bidi isolate spans; RTL digit order stays numeric left to right; label mirrors to inline-end.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: bars print solid ink, quiet zone prints as frame, scan state prints icon + text, digits print --font-mono, no shimmer, code prints framed at --color-border-strong.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- ('Bars', 'grid of --space-1 width modules, --color-skeleton-base')
- ('Human', 'width 50% bar at --text-xs, --color-skeleton-base')
- ('Label', 'width 30% bar at --text-2xs, --color-skeleton-base')
- ('Scan', 'width 25% bar at --text-xs, --color-skeleton-base')

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced. No pulse on digits. aria-busy=true while loading, role=status when payload lands, skeleton never read as content. Offline/error: skeleton replaced by state panel per section 3, not by blank.

## 16. Icon usage (Lucide names only)

- barcode for the code glyph, scan-line for scan slot, check-circle-2 for decode ok
- Lucide only, --icon-size-sm

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'barcode' component per data-display/barcode.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

