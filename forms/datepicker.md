# Datepicker

> Purpose: Calendar date picker: month grid, prev/next month, year jump, selected and range states, keyboard grid navigation, locale calendar token.
> Section: forms | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: datepicker. Section: forms. Calendar date picker: month grid, prev/next month, year jump, selected and range states, keyboard grid navigation, locale calendar token.

## 2. Anatomy (parts, ASCII diagram ok)

```
+-----------------------------------------+
| <  November 2026              >         |
+-----------------------------------------+
| Mo Tu We Th Fr Sa Su                   |
| .  .  .  .  .  .  1                    |
| 2  3  4  5  6  7  8                    |
+-----------------------------------------+
hint / error
```

- **field**: read-only display of the chosen date, --radius-field
- **calendar**: month grid panel at --z-dropdown, weekday header from locale token
- **nav**: Lucide chevron-left / chevron-right + month-year jump
- **hint/error**: --text-xs below

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hovered-click | --cursor-pointer | --color-surface-sunken + --opacity-pressed overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| pressed/active | N/A: datepicker has no press phase, it commits on click | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no hover fill |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no press |
| selected/checked | --cursor-default | --color-brand-soft | hairline --color-border-strong | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=true |
| unselected | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=false |
| expanded/collapsed | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | chevron rotate --duration-normal on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded per state |
| open/closed | --cursor-default | --color-surface-overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | enter --motion-enter, exit --motion-exit | silent (sound events only via --sound-* tokens, user opt-in) | aria-hidden when closed, role=dialog when open |
| active menu item | N/A: datepicker is not a menu, it has no item activation | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | N/A: datepicker does not navigate, no current-page concept | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no navigation semantics |
| visited | N/A: datepicker is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-error | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-invalid=true + aria-disabled=true |
| readonly | --cursor-default | --color-surface-sunken | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-readonly=true |
| required + filled | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-required=true, value present |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide inbox, --color-text-tertiary | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=status 'No items' |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-*, --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |
| success | --cursor-default | --color-surface-raised | hairline --color-success | --color-text-primary | Lucide check-*, --color-success | none at --duration-instant | --sound-success token if user enabled | role=status announced once |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for datepicker are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-field | rest |
| open | --color-surface-overlay | --color-text-primary | hairline --color-border-strong | --radius-field | calendar open |
| selected | --color-primary | --color-primary-content | transparent | --radius-full | chosen day |
| range | --color-brand-soft | --color-text-primary | hairline --color-primary | --radius-none | range span |
| invalid | --color-surface-raised | --color-error | hairline --color-error | --radius-field | validation failed |

Sizes: day cells from --space-* with min --touch-target-min; month grid max --measure-reading; heights fluid via clamp.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab enters, arrows move day focus in the grid; Enter selects; Escape closes and restores focus; PageUp/Down month jump; Home/End row jump; type-ahead jumps to matching day name per locale.
- Mouse: hover day highlights --color-brand-soft; click selects; drag range only where declared with keyboard alternative; right-click native menu.
- Touch: day cells >= --touch-target-min; swipe month change with button alternative; close on outside tap.
- Dismiss: Escape + outside click + scrim tap close; focus returns to the field.
- Offline: cached month renders, selection queued, replayed on reconnect.
- Debounce: month change debounces --duration-fast; async min/max load shows skeleton grid.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over field |
| hover | --cursor-pointer | day wash --color-brand-soft | over day cell |
| pressed/active | --cursor-pointer | --opacity-pressed fill | during select |
| disabled | --cursor-not-allowed | pointer-events none | on disabled day |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus |
| loading | --cursor-progress | skeleton grid --duration-skeleton-shimmer | async month |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Select -> --sound-click, month change -> none, error -> --sound-error. Haptics: --haptic-light on select. No sound on hover or month flip.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | full width, label above control | width 100% minus --space-4 gutters |
| tablet (--bp-sm..--bp-lg) | two-column field grid where listed | fluid minmax tokens |
| desktop (>= --bp-lg) | inline label + control, max --measure-reading | same grid, no fixed widths |

Fluid rules: no fixed px; all widths from --space-* / --measure-* / --bp-* tokens; text wraps, never truncates without ellipsis policy; horizontal scroll only inside scroll-region; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Weekday header order follows locale first-day token; grid mirrors in RTL; prev/next chevrons swap inline edges; selected day stays LTR numeric; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-raised, --color-surface-overlay, --color-brand-soft, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-text-disabled, --color-primary, --color-primary-content, --color-error, --color-border, --color-border-strong, --color-border-focus, --color-skeleton-base, --color-skeleton-shine, --opacity-hover, --opacity-pressed, --opacity-disabled, --radius-field, --radius-full, --shadow-md, --shadow-focus-glow, --space-1.--space-4, --text-xs/sm/base, --weight-medium/semibold, --font-ui, --font-mono, --leading-normal, --duration-fast, --duration-normal, --ease-standard, --cursor-default, --cursor-pointer, --cursor-not-allowed, --cursor-progress, --sound-click, --sound-error, --sound-volume, --motion-reduced, --bp-sm, --bp-lg, --touch-target-min, --z-dropdown.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; ship all 26 states; honor locale calendar and first-day tokens; announce selected date via aria; close on Escape with focus return; hold 40% expansion.
Do not: hardcode cell size; use color alone; hide the ring; trap focus; autoplay sound; ship without grid skeleton; let the calendar overflow the viewport; ship a fixed 7-column layout that breaks on narrow screens.
Premium treatment: calm field at rest, refined hover as day wash, tactile select, crisp ring, graceful disabled days, loading grid matching final cell sizes with zero shift.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- field: role=textbox readonly or native input, aria-required, aria-describedby hint + error
- calendar: role=dialog or grid, aria-label month year per locale
- day: role=gridcell, aria-selected, aria-disabled
- nav: role=button, aria-label prev/next month

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on field and focused day, never outline:none.
Contrast: AA 4:5:1 label, day text, hint both themes; selected day --color-primary with --color-primary-content 19.58:1; error AA; focus 3:1.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Month names, weekday names, hint, error: externalized, 40% expansion, ellipsis policy.
- Calendar system per locale token (gregorian, hijri, persian, etc.); date format per locale.
- First-day-of-week per locale; bidi isolate spans; RTL mirrors nav.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: selected day prints filled with the word selected, range prints outlined, error prints with text, no ring, no shimmer.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Field: full-width block at component height, radius --radius-field, --color-skeleton-base
- Grid: 7 columns x 6 rows of squares at day cell size, --color-skeleton-base
- Nav: 2 squares --icon-size-md at row ends, --color-skeleton-base
- Hint: width 40% bar at --text-xs, --color-skeleton-base

Fill --color-skeleton-base, shimmer --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced. aria-busy=true while loading, role=status when content lands. Offline/error: skeleton replaced by state panel per section 3.

## 16. Icon usage (Lucide names only)

- chevron-left / chevron-right month nav, calendar for field affordance, alert-circle for invalid
- Lucide only, --icon-size-md

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'datepicker' component per forms/datepicker.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

