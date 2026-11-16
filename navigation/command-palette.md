# Command Palette

> Purpose: Command palette: Cmd/Ctrl+K open, fuzzy list, arrow navigation, Enter run, Escape close, recent items, no network, results announced.
> Section: navigation | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: command-palette. Section: navigation. Command palette: Cmd/Ctrl+K open, fuzzy list, arrow navigation, Enter run, Escape close, recent items, no network, results announced.

## 2. Anatomy (parts, ASCII diagram ok)

```
+---------------------------------------+
| item  item  item  [current]  item      |
|  ^        ^           ^               |
| rest  hover  aria-current=page        |
+---------------------------------------+
```

- **Item**: label + optional icon, aria-current on current, --touch-target-min
- **Group**: optional divider + group label, --color-text-tertiary
- **Indicator**: active marker --color-accent, never color-only: text weight too
- **Overflow**: narrow-width menu, same item states, --z-dropdown

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| hovered-click | --cursor-pointer | --color-surface-sunken + --opacity-pressed overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| pressed/active | --cursor-pointer | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | transform press scale token, --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| selected/checked | --cursor-default | --color-brand-soft | hairline --color-border-strong | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=true |
| unselected | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=false |
| expanded/collapsed | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded per state |
| open/closed | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded per state |
| active menu item | --cursor-pointer | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=true |
| current page | --cursor-default | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=page |
| visited | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-secondary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| invalid + disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-error | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| readonly | --cursor-default | --color-surface-sunken | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-readonly=true |
| required + filled | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-required=true, value present |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide inbox, --color-text-tertiary | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=status 'No items' |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-* , --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |
| success | --cursor-default | --color-surface-raised | hairline --color-success | --color-text-primary | Lucide check-* , --color-success | none at --duration-instant | --sound-success token if user enabled | role=status announced once |

Every row names its tokens; no raw value appears anywhere. States not applicable to this component are marked N/A with a one-line reason, never dropped silently.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| horizontal | wide screens | --color-surface-raised | --color-text-primary | hairline --color-border |
| vertical | sidebar | --color-surface-raised | --color-text-primary | hairline --color-border |
| collapsed | narrow, icons only | --color-surface-raised | --color-text-primary | hairline --color-border |
| overflow | menu variant | --color-surface-overlay | --color-text-primary | hairline --color-border |

Sizes: sm / md / lg all from --space-* + --text-* tokens; hit area never below --touch-target-min at any size; sm never below --text-xs; lg never above --text-xl without --measure-reading cap.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab into the bar; arrows move within tablist/menu groups (roving tabindex); Enter/Space activate; Escape closes submenus; Home/End jump.
- Mouse: hover reveals submenu only with a delay token; click activates; current page marked aria-current=page plus weight, never color-only.
- Touch: targets --touch-target-min; swipe between tabs only where listed; no hover-only disclosure on coarse pointers.
- Dismiss: menus close on outside click + Escape; focus returns to trigger; breadcrumbs never trap.
- Collapse: navbar collapses to menu at --bp-md; sidebar collapses at --bp-lg; collapse then stack then hide, never display:none as the only response.
- RTL: direction flips via logical properties; directional icons mirror; order of items stays DOM order.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | root idle |
| hover | --cursor-pointer | background --color-surface-sunken or --opacity-hover overlay | on every interactive part |
| pressed/active | --cursor-pointer | scale press token + --opacity-pressed | on the triggered part |
| disabled | --cursor-not-allowed | pointer-events none | on disabled parts |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus |
| loading + disabled | --cursor-progress | spinner --duration-normal linear | async in flight |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Selection -> --sound-click, page change -> none, submenu open -> none, all at --sound-volume, user opt-in. Haptics: --haptic-selection on tab/step ticks. No sound on hover or focus; no sound for scroll.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | collapse to menu, icons + labels stacked | width 100% |
| tablet (--bp-sm..--bp-lg) | condensed labels, overflow menu | fluid clamp |
| desktop (>= --bp-lg) | full bar, all items visible | --grid-gutter |

Fluid rules: no fixed px; all widths from --space-* / --measure-* / --bp-* tokens; text wraps, never truncates without ellipsis policy; horizontal scroll only inside scroll-region; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Item order mirrors visually, DOM order unchanged; active indicator moves to inline-start; directional icons mirror; breadcrumbs reverse.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-base, --color-surface-raised, --color-surface-sunken, --color-surface-overlay, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-text-disabled, --color-primary, --color-primary-content, --color-secondary, --color-accent, --color-success, --color-warning, --color-error, --color-info, --color-border, --color-border-strong, --color-border-focus, --color-brand, --color-brand-soft, --color-scrim, --color-skeleton-base, --color-skeleton-shine, --opacity-hover, --opacity-pressed, --opacity-scrim, --opacity-selected, --opacity-disabled, --radius-sm, --radius-md, --radius-lg, --shadow-sm, --shadow-md, --shadow-focus-glow, --space-1.--space-8, --text-xs/sm/base/lg/xl, --weight-regular/semibold/extrabold, --font-ui, --font-mono, --leading-tight/normal/relaxed, --tracking-tight, --duration-instant/fast/normal/slow, --ease-standard/decelerate/accelerate/spring, --icon-size-sm/md/lg/xl, --icon-stroke-thin/regular/thick, --touch-target-min, --cursor-pointer/default/not-allowed, --sound-success/error/notification/click/toggle, --sound-volume, --motion-reduced, --bp-sm/md/lg, --measure-reading, --space-safe-top/right/bottom/left, --z-header, --z-sticky, --z-dropdown, --header-height, --sidebar-width-expanded, --sidebar-width-collapsed, --sidebar-animation.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

## 11. Do / Do not list

Do: reference tokens by name; ship all 26 states from section 3 or mark N/A with reason; render skeleton for every sub-shape; use Lucide line art at token size/stroke; keep keyboard full flow; announce state to screen readers; honor reduced motion; hold 40% text expansion; print grayscale.
Do not: hardcode a value; use emoji or raster art; trap focus; hide focus ring; use color alone for meaning; autoplay sound; fetch data inside the component; edit this file for white-label; add JS without a state that needs it; ship without a skeleton.

Premium treatment: opens on the single documented shortcut, results rank by recency then alpha, footer shows the kbd hints, selection moves with arrow keys only, escape restores focus exactly.
## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- Item: role=menuitemoption/tab, aria-current, aria-selected
- Group: role + accessible name, state via aria-*
- Indicator: role + accessible name, state via aria-*
- Overflow: role + accessible name, state via aria-*

Focus: :focus-visible ring --shadow-focus-glow + 2 units of --color-border-focus width, never :focus-only, never outline:none without replacement. Contrast: AA 4.5:1 body, 3:1 large text and UI, verified on light + dark token pairs; high-contrast theme strengthens borders and removes opacity text; forced-colors maps to system colors. Reduced motion: --duration-instant, no shimmer, no spring, content always visible. Touch target --touch-target-min. Safe area: respect --space-safe-top/right/bottom/left, no content under notches. Keyboard-only full flow with no mouse dependency; no keyboard trap; Escape always works where dismissible.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- all visible strings externalized to locale files; zero literals in code
- Command strings and result counts plural-safe per CLDR; no hardcoded suffix.
- Shortcut hints rendered from locale token, never raw keycode text.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: no color-only meaning, every status pairs icon + text. Backgrounds dropped except essential fills; no ink waste. Headers/footers repeat on page break; keep-together on label + value. Mono variant where listed; borders at --color-border-strong in print. Charts/graphs/maps print as labeled list or pattern-filled outline, never raster. No shadow, no blur, no animation. Print styles come from tokens, same no-hardcode rule.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Item: block at component height token, radius --radius-sm, --color-skeleton-base
- Group: block at component height token, radius --radius-sm, --color-skeleton-base
- Indicator: block at component height token, radius --radius-sm, --color-skeleton-base
- Overflow: block at component height token, radius --radius-sm, --color-skeleton-base

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced (static gray). No pulse on text. aria-busy=true while loading, role=status announcement when content lands, skeleton never read as content. Offline/error: skeleton replaced by state panel per section 3, not by blank.

## 16. Icon usage (Lucide names only)

- decorative marks: Lucide per part, --icon-size-md / --icon-stroke-thin, aria-hidden=true
- search for query field, corner-down-left for run, plus for create at --icon-size-sm

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'command-palette' component per navigation/command-palette.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: consume theme-variables.md tokens (navy ramp, tinted neutrals, single navy-family accent), keep one calm accent, AA contrast minimum both themes, calm short motion, light and dark parity, skeleton matches the final layout, Lucide icons only, no hardcoded values.
Return: component code + state matrix evidence + token usage list.
```
