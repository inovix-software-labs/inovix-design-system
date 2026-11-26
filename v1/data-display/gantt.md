# Gantt

> Purpose: Project timeline display: task rows, bar spans on a date axis, dependency lines, critical path highlight, today marker.
> Section: data-display | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: gantt. Section: data-display. Project timeline display: task rows, bar spans on a date axis, dependency lines, critical path highlight, today marker.

## 2. Anatomy (parts, ASCII diagram ok)

```
+-----------------------------+
| axis ticks, --text-xs       |
| task a  [===bar===]         |
| task b    [==bar==]-->      |
| task c  [==critical==]      |
| today marker, --color-error |
+-----------------------------+
```

- **axis**: date axis, ticks --text-xs --color-text-tertiary --font-mono
- **rows**: task rows, label --text-sm --color-text-primary, hairline --color-border
- **bar**: task span bar, fill --color-brand-soft, border --color-border-strong
- **dep**: dependency lines, stroke --color-text-tertiary, arrow head
- **critical**: critical path bars, fill --color-error, text --color-text-on-error

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hovered-click | --cursor-pointer | --color-surface-sunken + --opacity-pressed overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| pressed/active | N/A: gantt has no press phase, it commits on click | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no hover fill |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no press |
| selected/checked | --cursor-default | --color-brand-soft | hairline --color-border-strong | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=true |
| unselected | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=false |
| expanded/collapsed | N/A: gantt has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: gantt is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | --cursor-pointer | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=true |
| current page | --cursor-default | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=page |
| visited | N/A: gantt is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: gantt holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: gantt is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: gantt takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide inbox, --color-text-tertiary | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=status 'No items' |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-*, --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |
| success | --cursor-default | --color-surface-raised | hairline --color-success | --color-text-primary | Lucide check-*, --color-success | none at --duration-instant | --sound-success token if user enabled | role=status announced once |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for gantt are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-lg | rest |
| bar-hover | --color-surface-raised | --color-text-primary | hairline --color-border-strong | --radius-lg | bar focus |
| critical | --color-surface-raised | --color-text-on-error | hairline --color-error | --radius-lg | critical path |
| selected | --color-brand-soft | --color-text-primary | hairline --color-border-strong | --radius-lg | chosen task |
| overdue | --color-surface-raised | --color-text-primary | hairline --color-error | --radius-lg | past due |

Sizes: row min height --space-* tokens; bar min height --space-1; axis ticks --text-xs; task label --text-sm; today marker width --space-1; gap --space-1.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab reaches axis then rows then bars; arrows move row focus; Enter selects task; Shift+arrows extend selection; Escape clears selection and closes menu; focus ring on bar.
- Mouse: hover bar washes --opacity-hover with --shadow-xs; click selects task; drag bar moves span with --cursor-move; drag edge resizes with --cursor-cell; right-click opens task menu; dependency line hover shows source + target.
- Touch: rows >= --touch-target-min; tap selects; long-press opens task menu; two-finger pan scrolls axis; pinch zoom optional with button alternative.
- Dismiss: task menu closes on Escape + outside + scroll; bar drag cancels on Escape with span restored.
- Offline: cached tasks render; sync failure marks axis --color-warning; never fake dates.
- Debounce: axis zoom debounces --duration-fast; task load shows skeleton rows; selection commits at --duration-instant.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over empty axis |
| hover | --cursor-pointer | wash --opacity-hover + --shadow-xs | over task bar |
| pressed/active | --cursor-move | span drag, --opacity-pressed fill | during bar move |
| disabled | --cursor-not-allowed | pointer-events none | when plan locked |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus on bar |
| loading | --cursor-progress | row shimmer --duration-skeleton-shimmer | async tasks |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Task select -> --sound-click, span move commit -> --sound-success, dependency cycle error -> --sound-error, at --sound-volume user opt-in. Haptics: --haptic-light on select. No sound on hover of bars.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | axis labels abbreviate, task labels above bars, dependency lines hidden | width 100% minus --space-4 gutters |
| tablet (--bp-sm..--bp-lg) | axis top, labels left, bars full width | fluid minmax tokens |
| desktop (>= --bp-lg) | axis top with ticks, labels left column, full dependency lines | max --measure-reading |

Fluid rules: no fixed px; axis spans --grid-columns; rows keep min height token; bars wrap before axis scrolls; labels clamp to 1 line with ellipsis policy; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Axis dates read in locale order; bar spans anchor to date tokens not edges; dependency arrows mirror in RTL; today marker stays on its date; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-raised, --color-surface-sunken, --color-brand-soft, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-text-on-error, --color-primary, --color-error, --color-success, --color-warning, --color-border, --color-border-strong, --color-border-focus, --color-skeleton-base, --color-skeleton-shine, --opacity-hover, --opacity-pressed, --opacity-selected, --opacity-disabled, --radius-lg, --radius-sm, --shadow-xs, --shadow-focus-glow, --grid-columns, --space-1.--space-4, --text-xs/sm, --weight-medium, --font-ui, --font-mono, --leading-tight, --duration-instant, --duration-fast, --duration-skeleton-shimmer, --ease-standard, --icon-size-sm, --icon-stroke-thin, --touch-target-min, --cursor-default/pointer/move/cell/not-allowed/progress, --sound-click/success/error, --sound-volume, --motion-reduced, --bp-sm/md/lg.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; ship all 26 states; pair critical path with text never color alone; keep today marker distinct from selected bar; hold 40% expansion; announce span changes via aria; axis ticks per locale date format.
Do not: use color alone for critical path; let bars cross row bounds; hide the ring; trap focus in menu; autoplay sound on axis pan; ship without row skeleton; truncate labels without ellipsis policy.
Premium treatment: premium treatment: bar move settles with --ease-standard, today marker pulses once at --duration-slow off under --motion-reduced, selected row lifts --shadow-xs, zero shift when tasks land.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- chart: role=img, aria-label plan title + date range
- row: role=row, aria-label task name + span
- bar: role=button, aria-label task name + start + end, aria-selected
- dep: role=img, aria-label dependency from source to target
- menu: role=menu, closes on Escape

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on bars and menu trigger; axis never focusable; never outline:none.
Contrast: AA 4.5:1 task labels, axis ticks, bar text both themes; critical --color-error with --color-text-on-error verified pair; selected --color-brand-soft with --color-text-primary 13.40:1; focus 3:1.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Task names, axis labels, menu text: externalized, 40% expansion, ellipsis policy, no mid-word break.
- Dates per locale format; duration plural-safe; milestone words per locale.
- Bidi isolate spans; RTL mirrors label column and dependency arrows; dates stay locale-formatted.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: critical bars print solid dark with hatch, dependency lines print dashed, today marker prints as solid column, no shimmer, plan prints framed at --color-border-strong.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- ('Axis', 'row of 6 ticks at --text-xs, --color-skeleton-base')
- ('Rows', '4 rows at --space-* min height, --color-skeleton-base')
- ('Bars', 'width 40% bar at --space-1 height, --color-skeleton-base')
- ('Dep', 'width 30% line at --icon-size-sm, --color-skeleton-base')

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced. No pulse on axis ticks. aria-busy=true while loading, role=status when task list lands, skeleton never read as content. Offline/error: skeleton replaced by state panel per section 3, not by blank.

## 16. Icon usage (Lucide names only)

- calendar for today marker, arrow-right for dependency head, alert-triangle for critical path
- Lucide only, --icon-size-sm

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'gantt' component per data-display/gantt.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

