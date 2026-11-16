# Graph Dag

> Purpose: Directed acyclic graph display: nodes, edges with direction arrows, layout direction token, cycle policy marker.
> Section: data-display | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: graph-dag. Section: data-display. Directed acyclic graph display: nodes, edges with direction arrows, layout direction token, cycle policy marker.

## 2. Anatomy (parts, ASCII diagram ok)

```
+-----------------------------+
| entry (A) --> (B) --> (C)   |
|              |              |
|              v              |
|             (D)  exit ring  |
| cycle policy: warn marker   |
+-----------------------------+
```

- **node**: task node, radius --radius-md, fill --color-surface-raised, text --text-sm
- **edge**: directed edge, stroke --color-border-strong, arrow head at target
- **dir**: layout direction slot, horizontal or vertical from token
- **cycle**: cycle policy marker, Lucide shield-alert, --color-warning
- **entry**: entry node ring --color-primary, exit node ring --color-success

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hovered-click | --cursor-pointer | --color-surface-sunken + --opacity-pressed overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| pressed/active | N/A: graph-dag has no press phase, it commits on click | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no hover fill |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no press |
| selected/checked | --cursor-default | --color-brand-soft | hairline --color-border-strong | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=true |
| unselected | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=false |
| expanded/collapsed | N/A: graph-dag has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: graph-dag is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | --cursor-pointer | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=true |
| current page | --cursor-default | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=page |
| visited | N/A: graph-dag is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: graph-dag holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: graph-dag is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: graph-dag takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide inbox, --color-text-tertiary | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=status 'No items' |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-*, --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |
| success | --cursor-default | --color-surface-raised | hairline --color-success | --color-text-primary | Lucide check-*, --color-success | none at --duration-instant | --sound-success token if user enabled | role=status announced once |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for graph-dag are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-md | rest |
| entry | --color-surface-raised | --color-text-primary | hairline --color-primary | --radius-md | start node |
| exit | --color-surface-raised | --color-text-primary | hairline --color-success | --radius-md | end node |
| cycle | --color-surface-raised | --color-text-primary | hairline --color-warning | --radius-md | cycle flagged |
| selected | --color-brand-soft | --color-text-primary | hairline --color-border-strong | --radius-md | chosen node |

Sizes: node min width --space-* tokens; node text --text-sm; edge stroke from --icon-stroke-thin; arrow head --icon-size-sm; gap --space-* tokens; direction slot --text-xs.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab reaches nodes in layout order; arrows move node focus along edges; Enter selects node; Escape clears selection and closes menu; focus ring on node.
- Mouse: hover node washes --opacity-hover with --shadow-xs; click selects; drag node repositions with --cursor-move; hover edge highlights source + target; right-click opens node menu.
- Touch: nodes >= --touch-target-min; tap selects; drag node repositions; two-finger pan moves canvas; long-press opens node menu.
- Dismiss: node menu closes on Escape + outside + scroll; drag cancels on Escape with node restored.
- Offline: cached graph renders; sync failure marks cycle slot --color-warning; never fake edges.
- Debounce: layout recompute debounces --duration-normal; node load shows skeleton nodes; selection commits at --duration-instant.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over canvas |
| hover | --cursor-pointer | node wash --opacity-hover | over node |
| pressed/active | --cursor-move | node drag, --opacity-pressed fill | during reposition |
| disabled | --cursor-not-allowed | pointer-events none | when graph locked |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus on node |
| loading | --cursor-progress | node shimmer --duration-skeleton-shimmer | async graph |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Node select -> --sound-click, layout recompute -> --sound-toggle, cycle detect -> --sound-warning, at --sound-volume user opt-in. Haptics: --haptic-light on select. No sound on hover of edges.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | layout direction forced vertical, node labels wrap, edge arrows shrink | width 100% minus --space-4 gutters |
| tablet (--bp-sm..--bp-lg) | horizontal layout, labels single line, cycle slot below | fluid minmax tokens |
| desktop (>= --bp-lg) | full horizontal layout, entry + exit rings, cycle slot inline-end | max --measure-reading |

Fluid rules: no fixed px; nodes size from --space-* tokens; edges reroute before nodes overlap; labels clamp to 2 lines with ellipsis policy; canvas scrolls inside scroll-region only; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Edges follow layout direction token; arrow heads point to target in both directions; node order mirrors in RTL for horizontal layout; entry ring stays on entry node; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-raised, --color-surface-sunken, --color-brand-soft, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-text-on-error, --color-primary, --color-success, --color-warning, --color-border, --color-border-strong, --color-border-focus, --color-skeleton-base, --color-skeleton-shine, --opacity-hover, --opacity-pressed, --opacity-selected, --opacity-disabled, --radius-md, --shadow-xs, --shadow-focus-glow, --grid-columns, --space-1.--space-6, --text-xs/sm, --weight-medium, --font-ui, --leading-tight, --duration-instant, --duration-fast, --duration-normal, --duration-skeleton-shimmer, --ease-standard, --icon-size-sm, --icon-stroke-thin/regular, --touch-target-min, --cursor-default/pointer/move/not-allowed/progress, --sound-click/toggle/warning, --sound-volume, --motion-reduced, --bp-sm/md/lg.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; ship all 26 states; pair cycle flag with icon + text; keep entry and exit rings distinct; hold 40% expansion; announce node selection via aria; edges never carry text alone.
Do not: use color alone for cycle flag; let edges cross node text; hide the ring; trap focus in menu; autoplay sound on layout change; ship without node skeleton; let nodes overlap at narrow widths.
Premium treatment: premium treatment: node drag settles with --ease-standard, edge highlight draws at --duration-fast, cycle marker flashes once at --duration-slow off under --motion-reduced, zero shift when layout recomputes.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- graph: role=img, aria-label graph title + node count
- node: role=button, aria-label node title, aria-selected
- edge: role=img, aria-label edge from source to target
- cycle: role=status, cycle policy text announced once
- menu: role=menu, closes on Escape

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on nodes and menu trigger; edges never focusable; never outline:none.
Contrast: AA 4.5:1 node text, cycle text both themes; entry --color-primary ring 3:1; exit --color-success ring 3:1; selected --color-brand-soft with --color-text-primary 13.40:1; focus 3:1.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Node titles, edge labels, cycle policy text: externalized, 40% expansion, ellipsis policy, no mid-word break.
- Node counts plural-safe; direction words per locale; layout direction token per locale.
- Bidi isolate spans; RTL mirrors horizontal node order; edge labels stay on their edge.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: entry ring prints solid, exit ring prints dashed, cycle marker prints icon + text, edges print dashed arrows, no shimmer, graph prints framed at --color-border-strong.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- ('Nodes', '3 squares --space-* width, --color-skeleton-base')
- ('Edges', '3 lines --icon-size-sm height, --color-skeleton-base')
- ('Cycle', 'width 30% bar at --text-xs, --color-skeleton-base')
- ('Entry', 'ring square --space-1 width, --color-skeleton-base')

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced. No pulse on node text. aria-busy=true while loading, role=status when node list lands, skeleton never read as content. Offline/error: skeleton replaced by state panel per section 3, not by blank.

## 16. Icon usage (Lucide names only)

- shield-alert for cycle policy, arrow-right for edge head, circle-dot for entry node
- Lucide only, --icon-size-sm

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'graph-dag' component per data-display/graph-dag.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

