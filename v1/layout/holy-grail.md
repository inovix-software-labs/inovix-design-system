# Holy Grail

> Purpose: Full page shell at --z-base, header top, sidebar side, main center, footer bottom, scroll confined to main.
> Section: layout | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: holy-grail. Section: layout. Full page shell at --z-base, header top, sidebar side, main center, footer bottom, scroll confined to main.

## 2. Anatomy (parts, ASCII diagram ok)

```
+-----------------------------------------+
| header                                    |
| sidebar   main                          |
|         scrolls                         |
| footer                                    |
+-----------------------------------------+
```

- **container**: page shell, --z-base
- **header**: --header-height, top stripe
- **sidebar**: --sidebar-width-expanded or --sidebar-width-collapsed
- **main**: --color-surface-base, scrollable center
- **footer**: --footer-min-height, bottom stripe

## 2b. Build notes (authoritative, read before the state matrix)

These notes win over any older line in this file.

Page shell as a grid, 100 percent of the viewport, no page-level scroll:

```
+--------------------------------------------------------+
| HEADER  navy, fixed, full width, logo top-left          |
+----------+---------------------------------------------+
| SIDEBAR  | MAIN  (only this region scrolls)             |
| fixed,   |   page title + breadcrumbs                   |
| raised   |   content cards on --color-surface-base      |
|          +---------------------------------------------+
|          | FOOTER  copyright + current year             |
+----------+---------------------------------------------+
```

- Rows: header (--header-height), body (fills the rest), footer. Columns in the body: sidebar (--sidebar-width-expanded or collapsed), main (fluid, 1fr). There is no right sidebar.
- Header and sidebar are fixed. Only main scrolls (layout/scroll-region.md). The page itself never scrolls.
- Main padding is --grid-margin on inline sides and --space-6 on block sides. Content is a column of cards: --color-surface-raised, --radius-lg, hairline --color-border, --shadow-sm. Page background is --color-surface-base.
- Page heading block: breadcrumbs (--text-sm, --color-text-tertiary), then page title (--text-3xl, --weight-semibold, --color-text-primary), then one line of supporting text (--text-base, --color-text-secondary).
- Forms and reading content do not stretch edge to edge: the card holding a simple form is limited to --measure-reading wide and left aligned, or centered inside main, never 100 percent of a 2000 unit wide viewport.
- Sidebar open or closed, main reflows with the same animation; nothing jumps.


## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | N/A: holy-grail is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| hover | N/A: holy-grail is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| hovered-click | N/A: holy-grail is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| pressed/active | N/A: holy-grail is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| clicked | N/A: holy-grail is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| focus-visible | N/A: holy-grail is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| focus | N/A: holy-grail is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| disabled | N/A: holy-grail is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| disabled + hover | N/A: holy-grail is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| disabled + pressed | N/A: holy-grail is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| selected/checked | N/A: holy-grail carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| unselected | N/A: holy-grail carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| expanded/collapsed | N/A: holy-grail has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: holy-grail is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | N/A: holy-grail is not a menu, it has no item activation | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | N/A: holy-grail does not navigate, no current-page concept | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no navigation semantics |
| visited | N/A: holy-grail is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: holy-grail holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: holy-grail is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: holy-grail takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | N/A: holy-grail renders fixed content, an empty data set cannot occur | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no data semantics |
| error | N/A: holy-grail fetches nothing, no error state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no error semantics |
| success | N/A: holy-grail completes no async work, no success state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no success semantics |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for holy-grail are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-base | --color-text-primary | hairline --color-border-strong | --radius-none | standard shell |
| sidebar-collapsed | --color-surface-base | --color-text-primary | hairline --color-border | --radius-none | --sidebar-width-collapsed |
| full-width | --color-surface-base | --color-text-primary | hairline --color-border | --radius-none | no sidebar |

Sizes: header --header-height, sidebar --sidebar-width-expanded or collapsed, main gap --space-gutter, footer --footer-min-height, width 100% viewport.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab moves header then sidebar then main then footer in order.
- Mouse: hover none structural, click passes to content.
- Touch: swipe drawer sidebar where declared, targets >= --touch-target-min.
- Dismiss: not applicable, persistent shell.
- Offline: shell cached, renders instantly.
- Debounce: resize debounce --duration-fast, sidebar toggle --sidebar-animation.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over shell |
| hover | --cursor-pointer | sidebar toggle wash | over toggle |
| pressed/active | --cursor-pointer | --opacity-pressed fill | during toggle |
| disabled | --cursor-not-allowed | pointer-events none | when locked |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | on focusable chrome |
| loading | --cursor-progress | skeleton shell --duration-skeleton-shimmer | async layout |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Sidebar toggle -> --sound-click. Haptics: --haptic-light on toggle. No sound on hover.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | stacked header main footer, sidebar hidden drawer | width 100% minus gutters |
| tablet (--bp-sm..--bp-lg) | sidebar collapsed width | fluid minmax tokens |
| desktop (>= --bp-lg) | full holy-grail | same scale, no layout shift |

Fluid rules: no fixed px; main 1fr minus --space-gutter, collapse to stacked then hide.

## 9. RTL mirror behavior (what flips, what stays)

Sidebar starts inline-start in LTR and mirrors to inline-end in RTL, main follows bidi, no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-base, --color-surface-raised, --color-text-primary, --color-text-secondary, --color-border, --color-border-strong, --radius-none, --radius-md, --shadow-sm, --shadow-focus-glow, --space-gutter, --space-section, --text-base/sm, --weight-medium, --font-ui, --leading-normal, --duration-fast, --sidebar-animation, --ease-standard, --cursor-default/pointer/not-allowed/progress, --sound-click, --sound-volume, --motion-reduced, --bp-sm, --bp-lg, --touch-target-min, --header-height, --sidebar-width-expanded/collapsed, --footer-min-height, --z-base.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; animate sidebar via --sidebar-animation; keep scroll in main; label regions; hold 40% expansion.
Do not: hardcode sidebar width; trap focus in shell; autoplay sound; let main overflow viewport; fixed px heights.
Premium treatment: premium sidebar toggle via --sidebar-animation, crisp ring, zero layout shift on toggle.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- container: role=region, aria-label page shell
- header: role=banner
- sidebar: role=complementary, aria-label sidebar
- main: role=main
- footer: role=contentinfo

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on focusable chrome only, never outline:none.
Contrast: AA 4.5:1 header, sidebar, main, footer text both themes; focus ring 3:1; --color-text-primary on --color-surface-base verified.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Region labels: externalized, 40% expansion, ellipsis policy, no mid-word break.
- Region order per locale token.
- Bidi isolate spans; RTL mirrors sidebar edge.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Prints shell as framed page, header and footer repeated, no ring, no interactive states.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Container: full-width block, --color-skeleton-base
- Header: width 100% bar height --header-height, --color-skeleton-base
- Sidebar: width bar at --sidebar-width-expanded, --color-skeleton-base
- Main: width 1fr block, --color-skeleton-base
- Footer: width 100% bar height --footer-min-height, --color-skeleton-base

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced static gray. aria-busy=true while loading, role=status announcement when content lands, skeleton never read as content.

## 16. Icon usage (Lucide names only)

- alert-circle for layout error
- Lucide only, --icon-size-md

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'holy-grail' component per layout/holy-grail.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

