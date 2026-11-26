# Sidebar

> Purpose: Side navigation at --sidebar-width-expanded or --sidebar-width-collapsed, --sidebar-animation toggle, items with active state.
> Section: layout | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: sidebar. Section: layout. Side navigation at --sidebar-width-expanded or --sidebar-width-collapsed, --sidebar-animation toggle, items with active state.

## 2. Anatomy (parts, ASCII diagram ok)

```
+-----------------------------------------+
| header                                    |
| > item a                                  |
|   item b   (active)                       |
| [toggle]                                  |
+-----------------------------------------+
```

- **container**: --color-surface-raised, height 100% viewport
- **header**: --text-xs --color-text-secondary, region label
- **item**: --color-accent-soft on active, >= --touch-target-min
- **active indicator**: --color-accent, inline-start edge
- **collapse toggle**: Lucide chevron-left, --touch-target-min

## 2b. Build notes (authoritative, read before the state matrix)

These notes win over any older line in this file.

- Fixed to the inline-start edge, starts below the header (top = --header-height), runs to the bottom of the viewport, sits at --z-sidebar. Surface is --color-surface-raised with a hairline --color-border on the inline-end edge. It is NOT navy.
- Expanded width --sidebar-width-expanded, collapsed (icon rail) --sidebar-width-collapsed. The toggle is the animated hamburger in the header (layout/header.md). Open and close slide on --sidebar-animation; main content reflows with the same timing, no jump.
- Mobile: sidebar is an off-canvas drawer over a scrim, closed by default, closes on scrim click, Escape and item activation. Desktop: expanded by default, remembers the user choice.
- Item: --touch-target-min tall, --radius-md, icon (Lucide, --icon-size-md) then label, --space-3 inline padding. Resting: transparent, --color-text-secondary. Hover: --color-brand-soft fill, --color-text-primary. Active (current page): --color-accent-soft fill, --color-accent text and icon, a 3 unit inline-start edge in --color-accent, aria-current page.
- Section labels: --text-xs, uppercase, --tracking-wider, --color-text-tertiary. Groups separated by --space-4, no dividers unless the group is long.
- Collapsed rail shows icons only, label appears as a tooltip on hover and focus. Active item keeps its fill.
- The menu entry for the page being built is always present and marked current. Order: primary destinations first, settings and help last.


## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hovered-click | --cursor-pointer | --color-surface-sunken + --opacity-pressed overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| pressed/active | N/A: sidebar has no press phase, it commits on click | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no hover fill |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no press |
| selected/checked | N/A: sidebar carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| unselected | N/A: sidebar carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| expanded/collapsed | N/A: sidebar has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: sidebar is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | N/A: sidebar is not a menu, it has no item activation | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | --cursor-default | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=page |
| visited | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-secondary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | history visited, no style-only meaning |
| invalid + disabled | N/A: sidebar holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: sidebar is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: sidebar takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | N/A: sidebar renders fixed content, an empty data set cannot occur | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no data semantics |
| error | N/A: sidebar fetches nothing, no error state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no error semantics |
| success | N/A: sidebar completes no async work, no success state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no success semantics |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for sidebar are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-raised | --color-text-primary | hairline --color-border-strong | --radius-none | expanded sidebar |
| collapsed | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-none | --sidebar-width-collapsed |
| mini | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-none | icons only |

Sizes: width --sidebar-width-expanded or collapsed, item height >= --touch-target-min, gap --space-2, height 100% viewport.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab reaches items, Enter activates, Escape collapses where declared.
- Mouse: hover item wash --color-brand-soft, click activates, toggle collapses.
- Touch: items >= --touch-target-min, swipe drawer where declared.
- Dismiss: Escape collapses where declared.
- Offline: items cached, renders instantly.
- Debounce: toggle debounce --duration-fast, async items skeleton sidebar.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over sidebar |
| hover | --cursor-pointer | item wash --color-brand-soft | over item |
| pressed/active | --cursor-pointer | --opacity-pressed fill | during activate |
| disabled | --cursor-not-allowed | pointer-events none | when disabled |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus |
| loading | --cursor-progress | skeleton items --duration-skeleton-shimmer | async items |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Item activate -> --sound-click, toggle -> --sound-click. Haptics: --haptic-light on toggle. No sound on hover.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | drawer hidden until toggle | width 100% minus gutters when open |
| tablet (--bp-sm..--bp-lg) | collapsed width --sidebar-width-collapsed | fluid minmax tokens |
| desktop (>= --bp-lg) | expanded width --sidebar-width-expanded | same scale, no layout shift |

Fluid rules: no fixed px; width from --sidebar-width-* tokens, height viewport, collapse then hide.

## 9. RTL mirror behavior (what flips, what stays)

Sidebar starts inline-start in LTR and mirrors to inline-end in RTL, items follow bidi, toggle flips, no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-raised, --color-text-primary, --color-text-secondary, --color-brand, --color-brand-soft, --color-border, --color-border-strong, --color-border-focus, --radius-none, --radius-md, --shadow-lg, --shadow-focus-glow, --space-1.--space-6, --space-gutter, --text-xs/sm/base, --weight-medium/semibold, --font-ui, --leading-normal, --duration-fast, --sidebar-animation, --ease-standard, --cursor-default/pointer/not-allowed/progress, --sound-click, --sound-volume, --motion-reduced, --bp-sm, --bp-lg, --touch-target-min, --sidebar-width-expanded/collapsed, --z-sticky.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; animate via --sidebar-animation; label items; announce collapse; hold 40% expansion.
Do not: hardcode width; use color alone for active; hide the ring; trap focus; autoplay sound; let items overflow sidebar.
Premium treatment: premium toggle via --sidebar-animation, crisp ring, zero layout shift on collapse.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- container: role=complementary, aria-label sidebar
- header: role=region, aria-label region
- item: role=link, aria-current=page when active
- active indicator: aria-hidden=true, visual only
- collapse toggle: role=button, aria-expanded, aria-label collapse sidebar

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on focused item or toggle, never outline:none.
Contrast: AA 4.5:1 item text both themes; active item --color-brand verified; focus ring 3:1; --color-text-primary on --color-surface-raised verified.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Item labels, region label: externalized, 40% expansion, ellipsis policy, no mid-word break.
- Item order per locale token.
- Bidi isolate spans; RTL mirrors sidebar edge and toggle.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Prints sidebar items as text list, active state as text, no ring, no interactive states.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Container: full-width block at --sidebar-width-expanded, --color-skeleton-base
- Item: width 100% bar at row height, --color-skeleton-base
- Toggle: square --touch-target-min, --color-skeleton-base

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced static gray. aria-busy=true while loading, role=status announcement when content lands, skeleton never read as content.

## 16. Icon usage (Lucide names only)

- chevron-left for collapse, alert-circle for error
- Lucide only, --icon-size-md

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'sidebar' component per layout/sidebar.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

