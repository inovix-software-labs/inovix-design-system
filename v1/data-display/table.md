# Table

> Purpose: Sortable, filterable, paginated data grid with sticky header, row states, selection, inline edit and print-first layout.
> Section: data-display | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: table. Section: data-display. Sortable, filterable, paginated data grid with sticky header, row states, selection, inline edit and print-first layout.

## 2. Anatomy (parts, ASCII diagram ok)

```
+------+----------------+----------------+------+
| []   | Name      v  | Count          | ...  |
+------+----------------+----------------+------+
| []   | row data     | tabular mono   |      |
+------+----------------+----------------+------+
| footer: count + pagination                |
+-------------------------------------------+
```

- **header**: column labels, sortable via Lucide arrow-up-down, sticky at --z-sticky-content
- **row**: data row, hover --opacity-hover, selected --color-brand-soft
- **cell**: text --text-sm, numeric --font-mono tabular
- **footer**: pagination + count, --text-xs
- **skeleton**: row bars per sub-shape

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hovered-click | --cursor-pointer | --color-surface-sunken + --opacity-pressed overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| pressed/active | N/A: table has no press phase, it commits on click | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no hover fill |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no press |
| selected/checked | --cursor-default | --color-brand-soft | hairline --color-border-strong | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=true |
| unselected | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=false |
| expanded/collapsed | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | chevron rotate --duration-normal on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded per state |
| open/closed | N/A: table is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | --cursor-pointer | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=true |
| current page | N/A: table does not navigate, no current-page concept | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no navigation semantics |
| visited | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-secondary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | history visited, no style-only meaning |
| invalid + disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-error | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-invalid=true + aria-disabled=true |
| readonly | --cursor-default | --color-surface-sunken | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-readonly=true |
| required + filled | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-required=true, value present |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide inbox, --color-text-tertiary | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=status 'No items' |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-*, --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |
| success | --cursor-default | --color-surface-raised | hairline --color-success | --color-text-primary | Lucide check-*, --color-success | none at --duration-instant | --sound-success token if user enabled | role=status announced once |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for table are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-none | rest |
| selected | --color-brand-soft | --color-text-primary | hairline --color-border-strong | --radius-none | row chosen |
| striped | --color-surface-sunken alt rows | --color-text-primary | hairline --color-border | --radius-none | density calm |
| compact | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-none | high density |
| invalid | --color-surface-raised | --color-error | hairline --color-error | --radius-none | row validation failed |

Sizes: sm / md / lg row heights from --space-* + --text-* tokens; header never below --text-xs; hit area for row actions >= --touch-target-min; width fluid, horizontal scroll inside scroll-region only.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab enters header controls; arrows move cell focus; Enter opens row detail; Space toggles selection; Escape exits edit; sort via header button; page up/down in pagination.
- Mouse: hover row --opacity-hover; click row selects; double-click inline edit; drag column resize with grip; right-click row context menu; scroll sticky header.
- Touch: row targets >= --touch-target-min; swipe row reveals actions; long-press context menu; pinch zoom not used.
- Dismiss: edit cancels on Escape; context menu closes on Escape + outside; pagination scrolls to top of table.
- Offline: cached rows render, queue edits, replay on reconnect, conflict note --color-warning.
- Debounce: filter input debounces --duration-debounce-input; sort commits at --duration-fast; inline edit saves on blur.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over data cells |
| hover | --cursor-pointer | row wash --opacity-hover | over row action |
| pressed/active | --cursor-pointer | --opacity-pressed fill | during select |
| disabled | --cursor-not-allowed | pointer-events none | on disabled rows |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus |
| loading | --cursor-progress | row shimmer --duration-skeleton-shimmer | async data |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Sort commit -> --sound-click, row select -> --sound-click, save -> --sound-success, error -> --sound-error. Haptics: --haptic-light on select. No sound on hover or scroll.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | stack to single column, hide secondary meta | width 100% minus --space-4 gutters |
| tablet (--bp-sm..--bp-lg) | two-column grid where listed, meta inline | fluid minmax tokens |
| desktop (>= --bp-lg) | full grid, meta inline, max --measure-reading | same scale, no fixed widths |

Fluid rules: no fixed px; all widths from --space-* / --measure-* / --bp-* tokens; text wraps, never truncates without ellipsis policy; horizontal scroll only inside scroll-region; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Column order mirrors; sort arrows flip; selection checkbox stays inline-start; numeric stays LTR; context menu anchors to row edge; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-base, --color-surface-raised, --color-surface-sunken, --color-brand-soft, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-text-disabled, --color-primary, --color-primary-content, --color-error, --color-success, --color-warning, --color-info, --color-border, --color-border-strong, --color-border-focus, --color-selection, --color-selection-text, --color-skeleton-base, --color-skeleton-shine, --opacity-hover, --opacity-pressed, --opacity-selected, --opacity-disabled, --radius-none, --radius-sm, --shadow-sm, --shadow-md, --shadow-focus-glow, --space-1.--space-8, --text-xs/sm/base, --weight-medium/semibold, --font-ui, --font-mono, --leading-normal, --tracking-tight, --duration-fast, --duration-normal, --duration-debounce-input, --duration-skeleton-shimmer, --ease-standard, --icon-size-sm/md, --icon-stroke-thin/regular, --touch-target-min, --cursor-default/pointer/not-allowed/progress/grab, --sound-click/success/error, --sound-volume, --motion-reduced, --bp-sm/md/lg, --measure-reading, --z-sticky-content.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; ship all 26 states; keep sticky header below --z-sticky-content; pair every status with icon + text; hold 40% expansion; print with repeated header.
Do not: hardcode row height; use color alone for status; hide the ring; trap focus in edit; autoplay sound; ship without row skeletons; let numeric overflow the cell.
Premium treatment: calm hairline grid, refined hover as wash never a fill jump, tactile press, crisp ring, graceful disabled rows, loading that matches final row heights exactly with zero shift.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- table: role=table or native table, aria-label from caption
- row: role=row, aria-selected when selectable
- cell: role=cell, aria-describedby for error
- sort: aria-sort on header button
- pagination: aria-label, aria-current on page

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on every interactive cell control, never outline:none.
Contrast: AA 4:5:1 cell text both themes; selected row --color-brand-soft with --color-text-primary verified 13.40:1; status colors pair with icon + text; focus 3:1.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Caption, headers, cells, footer: externalized, 40% expansion, ellipsis policy, no mid-word break.
- Numeric and date cells per locale format tokens; column order follows locale, never code-point.
- Plural-safe counts; bidi isolate spans; RTL mirrors column order.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: header repeats on every page, zebra fills drop, status prints icon + text, no ring, no shimmer, numeric prints --font-mono, page breaks inside rows forbidden.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Header row: bars at --text-sm height, --color-skeleton-base
- Data rows: 5 bars per row at cell height, --color-skeleton-base
- Numeric cells: narrow bars at 60% width, --color-skeleton-base
- Footer: bar at --text-xs height, --color-skeleton-base

Fill --color-skeleton-base, shimmer --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced. aria-busy=true while loading, role=status when content lands. Offline/error: skeleton replaced by state panel per section 3, not by blank.

## 16. Icon usage (Lucide names only)

- arrow-up-down for sortable headers, chevron-up/down for sort direction
- alert-circle for row error, check-circle for saved row, inbox for empty table
- grip-vertical for resize, Lucide only, --icon-size-sm

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'table' component per data-display/table.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

