# Graph Mindmap

> Purpose: Mind map display: center topic, radial branches, leaf nodes, branch color from chart ramp, branch collapse marker.
> Section: data-display | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: graph-mindmap. Section: data-display. Mind map display: center topic, radial branches, leaf nodes, branch color from chart ramp, branch collapse marker.

## 2. Anatomy (parts, ASCII diagram ok)

```
+-----------------------------+
|        (leaf)               |
|          |                  |
| (leaf)--(branch)  (leaf)    |
|            |                |
|         (center)            |
|            |                |
| (leaf)--(branch)  +3 more   |
+-----------------------------+
```

- **center**: center topic node, fill --color-primary, text --color-text-on-brand, radius --radius-full
- **branch**: branch node, fill --color-brand-soft, text --text-sm, hairline --color-border-strong
- **leaf**: leaf node, fill --color-surface-raised, text --text-xs, hairline --color-border
- **spoke**: radial spoke, stroke --chart-1..--chart-12 per branch
- **collapse**: branch collapse marker, Lucide plus, --color-warning, count --text-xs

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hovered-click | --cursor-pointer | --color-surface-sunken + --opacity-pressed overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| pressed/active | N/A: graph-mindmap has no press phase, it commits on click | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no hover fill |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no press |
| selected/checked | --cursor-default | --color-brand-soft | hairline --color-border-strong | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=true |
| unselected | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=false |
| expanded/collapsed | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | chevron rotate --duration-normal on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded per state |
| open/closed | N/A: graph-mindmap is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | --cursor-pointer | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=true |
| current page | --cursor-default | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=page |
| visited | N/A: graph-mindmap is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: graph-mindmap holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: graph-mindmap is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: graph-mindmap takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide inbox, --color-text-tertiary | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=status 'No items' |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-*, --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |
| success | --cursor-default | --color-surface-raised | hairline --color-success | --color-text-primary | Lucide check-*, --color-success | none at --duration-instant | --sound-success token if user enabled | role=status announced once |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for graph-mindmap are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-md | rest |
| center | --color-primary | --color-text-on-brand | hairline --color-primary | --radius-full | center topic |
| branch | --color-brand-soft | --color-text-primary | hairline --color-border-strong | --radius-md | branch topic |
| leaf | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-sm | leaf idea |
| collapsed | --color-surface-raised | --color-text-primary | hairline --color-warning | --radius-md | branch folded |

Sizes: center node min --space-* tokens; branch text --text-sm; leaf text --text-xs; spoke stroke from --icon-stroke-thin; collapse count --text-xs; radial gap --space-* tokens.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab reaches center then branches then leaves; arrows move radially; Right expands collapsed branch; Left collapses; Enter selects; Escape clears selection and closes menu; focus ring on node.
- Mouse: hover node washes --opacity-hover with --shadow-xs; click selects; click collapse marker expands branch; drag canvas pans with --cursor-grab; right-click opens node menu.
- Touch: nodes >= --touch-target-min; tap selects; tap collapse marker expands; pinch zoom optional with button alternative; long-press opens node menu.
- Dismiss: node menu closes on Escape + outside + scroll; canvas pan ends on release; collapse popover closes on Escape with focus back on marker.
- Offline: cached map renders; sync failure marks collapsed branches --color-warning; never fake leaves.
- Debounce: branch recompute debounces --duration-normal; node load shows skeleton nodes; selection commits at --duration-instant.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over canvas |
| hover | --cursor-pointer | node wash --opacity-hover | over node |
| pressed/active | --cursor-grab | canvas pan, --opacity-pressed fill | during pan |
| disabled | --cursor-not-allowed | pointer-events none | when map locked |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus on node |
| loading | --cursor-progress | node shimmer --duration-skeleton-shimmer | async map |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Node select -> --sound-click, branch expand -> --sound-toggle, load error -> --sound-error, at --sound-volume user opt-in. Haptics: --haptic-light on select. No sound on hover of spokes.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | branches stack vertical, leaves inline, collapse counts inline-end | width 100% minus --space-4 gutters |
| tablet (--bp-sm..--bp-lg) | two-level radial, center top, leaves below | fluid minmax tokens |
| desktop (>= --bp-lg) | full radial, center middle, branches around, chart ramp per branch | max --measure-reading |

Fluid rules: no fixed px; nodes size from --space-* tokens; spokes reroute before nodes overlap; leaf labels clamp to 1 line with ellipsis policy; canvas scrolls inside scroll-region only; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Branches mirror in RTL; center stays centered; spoke colors keep branch identity across mirror; collapse counts stay on branch end; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-raised, --color-surface-sunken, --color-brand-soft, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-text-on-brand, --color-primary, --color-warning, --color-border, --color-border-strong, --color-border-focus, --color-skeleton-base, --color-skeleton-shine, --opacity-hover, --opacity-pressed, --opacity-selected, --opacity-disabled, --radius-md, --radius-sm, --radius-full, --shadow-xs, --shadow-focus-glow, --grid-columns, --space-1.--space-6, --text-xs/sm, --weight-medium, --font-ui, --leading-tight, --duration-instant, --duration-fast, --duration-normal, --duration-skeleton-shimmer, --ease-standard, --icon-size-sm, --icon-stroke-thin, --touch-target-min, --cursor-default/pointer/grab/not-allowed/progress, --sound-click/toggle/error, --sound-volume, --motion-reduced, --bp-sm/md/lg, --chart-1.--chart-12.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; ship all 26 states; branch color from --chart-* ramp only; pair collapse count with icon + text; hold 40% expansion; announce branch state via aria-expanded; center topic never truncated.
Do not: use color alone for branch; let spokes cross node text; hide the ring; trap focus in menu; autoplay sound on expand; ship without node skeleton; let leaves overlap center at narrow widths.
Premium treatment: premium treatment: expand animates spokes at --duration-fast with --ease-standard off under --motion-reduced, center glows --shadow-xs once, selected node settles with --opacity-pressed, zero shift when leaves load.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- graph: role=tree, aria-label mind map title + node count
- node: role=treeitem, aria-expanded, aria-selected, aria-level
- spoke: role=presentation, aria-hidden
- collapse: role=button, aria-label expand branch + count
- menu: role=menu, closes on Escape

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on nodes, collapse markers, menu trigger; spokes never focusable; never outline:none.
Contrast: AA 4.5:1 center, branch, leaf text both themes; center --color-primary with --color-text-on-brand verified pair; selected --color-brand-soft with --color-text-primary 13.40:1; focus 3:1.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Center topic, branch titles, leaf text: externalized, 40% expansion, ellipsis policy, no mid-word break.
- Leaf counts plural-safe; branch order per locale; collapse marker count per locale number format.
- Bidi isolate spans; RTL mirrors branch order; node titles stay as stored.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: center prints solid dark, branches print outlined with ramp converted to hatch, leaves print framed, collapse marker prints icon + count, no shimmer, map prints framed at --color-border-strong.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- ('Center', 'circle --space-* width, --color-skeleton-base')
- ('Branches', '4 squares --space-* width, --color-skeleton-base')
- ('Leaves', '6 squares --space-* width, --color-skeleton-base')
- ('Spokes', '6 lines --icon-size-sm height, --color-skeleton-base')

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced. No pulse on node text. aria-busy=true while loading, role=status when node list lands, skeleton never read as content. Offline/error: skeleton replaced by state panel per section 3, not by blank.

## 16. Icon usage (Lucide names only)

- plus for collapse marker, brain for center topic, lightbulb for leaf idea
- Lucide only, --icon-size-sm

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'graph-mindmap' component per data-display/graph-mindmap.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

