# Graph Tree

> Purpose: Tree display: root + child nodes, expand + collapse carets, indent guides, leaf markers, selected path highlight.
> Section: data-display | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: graph-tree. Section: data-display. Tree display: root + child nodes, expand + collapse carets, indent guides, leaf markers, selected path highlight.

## 2. Anatomy (parts, ASCII diagram ok)

```
+-----------------------------+
| (root)                      |
|  |- caret (child)           |
|  |   |- leaf (child)        |
|  |- caret (child)           |
|      |- leaf (child)        |
+-----------------------------+
```

- **root**: root node, fill --color-primary, text --color-text-on-brand, radius --radius-md
- **caret**: expand + collapse caret, Lucide chevron, --icon-size-sm, --color-text-secondary
- **child**: child node, fill --color-surface-raised, text --text-sm, hairline --color-border
- **guide**: indent guide, stroke --color-border, vertical hairline
- **leaf**: leaf marker, Lucide minus, --icon-size-sm, --color-text-tertiary

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hovered-click | --cursor-pointer | --color-surface-sunken + --opacity-pressed overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| pressed/active | N/A: graph-tree has no press phase, it commits on click | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no hover fill |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no press |
| selected/checked | --cursor-default | --color-brand-soft | hairline --color-border-strong | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=true |
| unselected | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=false |
| expanded/collapsed | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | chevron rotate --duration-normal on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded per state |
| open/closed | N/A: graph-tree is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | --cursor-pointer | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=true |
| current page | --cursor-default | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=page |
| visited | N/A: graph-tree is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: graph-tree holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: graph-tree is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: graph-tree takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide inbox, --color-text-tertiary | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=status 'No items' |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-*, --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |
| success | --cursor-default | --color-surface-raised | hairline --color-success | --color-text-primary | Lucide check-*, --color-success | none at --duration-instant | --sound-success token if user enabled | role=status announced once |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for graph-tree are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-md | rest |
| expanded | --color-surface-raised | --color-text-primary | hairline --color-border-strong | --radius-md | children visible |
| collapsed | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-md | children hidden |
| leaf | --color-surface-base | --color-text-primary | hairline --color-border | --radius-sm | no children |
| selected | --color-brand-soft | --color-text-primary | hairline --color-border-strong | --radius-md | chosen node |

Sizes: node min height --space-* tokens; caret --icon-size-sm; indent per level --space-* tokens; guide stroke --space-1; child text --text-sm; gap --space-1.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab reaches root then children; arrows move along rows; Right expands collapsed node; Left collapses or moves to parent; Enter selects; Space toggles; Escape clears selection and closes menu; focus ring on node.
- Mouse: hover row washes --opacity-hover; click caret expands or collapses; click row selects; drag row repositions with --cursor-move; right-click opens node menu.
- Touch: rows >= --touch-target-min; tap caret expands; tap row selects; drag row repositions; long-press opens node menu; no hover-only path on coarse pointers.
- Dismiss: node menu closes on Escape + outside + scroll; row drag cancels on Escape with node restored.
- Offline: cached tree renders; sync failure marks collapsed nodes --color-warning; never fake children.
- Debounce: expand recompute debounces --duration-fast; node load shows skeleton rows; selection commits at --duration-instant.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over empty row |
| hover | --cursor-pointer | row wash --opacity-hover | over node row |
| pressed/active | --cursor-move | row drag, --opacity-pressed fill | during reposition |
| disabled | --cursor-not-allowed | pointer-events none | when tree locked |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus on row |
| loading | --cursor-progress | row shimmer --duration-skeleton-shimmer | async tree |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Row select -> --sound-click, expand + collapse -> --sound-toggle, load error -> --sound-error, at --sound-volume user opt-in. Haptics: --haptic-light on select. No sound on hover of guides.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | indent shrinks one token, guides hidden, leaf markers inline | width 100% minus --space-4 gutters |
| tablet (--bp-sm..--bp-lg) | full indent, guides shown, carets before labels | fluid minmax tokens |
| desktop (>= --bp-lg) | full indent + guides, selected path highlighted, menu inline-end | max --measure-reading |

Fluid rules: no fixed px; rows keep min height token; indent grows by --space-* per level; labels clamp to 1 line with ellipsis policy; rows wrap before indent shrinks; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Caret + guide indent follows locale direction; row order mirrors in RTL; selected path highlights logical path; leaf markers stay at inline-end; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-raised, --color-surface-base, --color-brand-soft, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-text-on-brand, --color-primary, --color-warning, --color-border, --color-border-strong, --color-border-focus, --color-selection, --color-selection-text, --color-skeleton-base, --color-skeleton-shine, --opacity-hover, --opacity-pressed, --opacity-selected, --opacity-disabled, --radius-md, --radius-sm, --shadow-xs, --shadow-focus-glow, --grid-columns, --space-1.--space-6, --text-sm/base, --weight-medium, --font-ui, --leading-tight, --duration-instant, --duration-fast, --duration-skeleton-shimmer, --ease-standard, --icon-size-sm, --icon-stroke-thin, --touch-target-min, --cursor-default/pointer/move/not-allowed/progress, --sound-click/toggle/error, --sound-volume, --motion-reduced, --bp-sm/md/lg.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; ship all 26 states; pair caret with expand state text; keep selected path distinct from hover; hold 40% expansion; announce expand via aria-expanded; guides never carry text alone.
Do not: use color alone for selected path; let guides cross node text; hide the ring; trap focus in menu; autoplay sound on expand; ship without row skeleton; let labels truncate without ellipsis policy.
Premium treatment: premium treatment: caret rotates at --duration-fast with --ease-standard off under --motion-reduced, selected path fills --color-brand-soft once, row lifts --shadow-xs on hover, zero shift when children load.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- tree: role=tree, aria-label tree title + node count
- node: role=treeitem, aria-expanded, aria-selected, aria-level
- caret: role=button, aria-label expand or collapse
- guide: role=presentation, aria-hidden
- menu: role=menu, closes on Escape

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on rows, carets, menu trigger; guides never focusable; never outline:none.
Contrast: AA 4.5:1 node text, leaf markers both themes; root --color-primary with --color-text-on-brand verified pair; selected --color-brand-soft with --color-text-primary 13.40:1; focus 3:1.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Node labels, menu text, expand state: externalized, 40% expansion, ellipsis policy, no mid-word break.
- Node counts plural-safe; level words per locale; caret direction per locale convention.
- Bidi isolate spans; RTL mirrors indent and caret direction; node labels stay as stored.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: root prints solid dark, collapsed nodes print caret + count, guides print solid lines, selected path prints outline, no shimmer, tree prints framed at --color-border-strong.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- ('Root', 'square --space-* width, --color-skeleton-base')
- ('Rows', '4 bars at --text-sm height, --color-skeleton-base')
- ('Guides', '3 lines --space-1 width, --color-skeleton-base')
- ('Carets', '3 squares --icon-size-sm, --color-skeleton-base')

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced. No pulse on node text. aria-busy=true while loading, role=status when node list lands, skeleton never read as content. Offline/error: skeleton replaced by state panel per section 3, not by blank.

## 16. Icon usage (Lucide names only)

- chevron-right / chevron-down for caret, minus for leaf marker, folder-tree for root
- Lucide only, --icon-size-sm

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'graph-tree' component per data-display/graph-tree.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

