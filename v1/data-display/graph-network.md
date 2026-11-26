# Graph Network

> Purpose: Network display: peer nodes, undirected links, cluster groups, node degree by size token, legend slot.
> Section: data-display | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: graph-network. Section: data-display. Network display: peer nodes, undirected links, cluster groups, node degree by size token, legend slot.

## 2. Anatomy (parts, ASCII diagram ok)

```
+-----------------------------+
|  (p) --- (p)   cluster A    |
|   | \     |                 |
|  (p) --- (p)  cluster B     |
|            \   |            |
|            (p)-(p) legend   |
+-----------------------------+
```

- **peer**: peer node, radius --radius-full, size from degree token, fill --color-surface-raised
- **link**: undirected link, stroke --color-border-strong, no arrow
- **cluster**: cluster group ring, stroke --chart-1..--chart-12, dashed
- **degree**: degree label, --text-2xs --font-mono, --color-text-tertiary
- **legend**: legend slot, swatch + text, --text-xs

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hovered-click | --cursor-pointer | --color-surface-sunken + --opacity-pressed overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| pressed/active | N/A: graph-network has no press phase, it commits on click | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no hover fill |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no press |
| selected/checked | --cursor-default | --color-brand-soft | hairline --color-border-strong | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=true |
| unselected | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=false |
| expanded/collapsed | N/A: graph-network has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: graph-network is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | --cursor-pointer | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=true |
| current page | N/A: graph-network does not navigate, no current-page concept | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no navigation semantics |
| visited | N/A: graph-network is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: graph-network holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: graph-network is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: graph-network takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide inbox, --color-text-tertiary | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=status 'No items' |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-*, --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |
| success | --cursor-default | --color-surface-raised | hairline --color-success | --color-text-primary | Lucide check-*, --color-success | none at --duration-instant | --sound-success token if user enabled | role=status announced once |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for graph-network are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-full | rest |
| hub | --color-surface-raised | --color-text-primary | hairline --color-primary | --radius-full | high degree |
| clustered | --color-brand-soft | --color-text-primary | hairline --color-border-strong | --radius-full | in cluster |
| isolated | --color-surface-raised | --color-text-tertiary | hairline --color-border | --radius-full | no links |
| selected | --color-selection | --color-selection-text | hairline --color-border-strong | --radius-full | chosen peer |

Sizes: peer node size from degree token --space-*; degree label --text-2xs; link stroke --icon-stroke-thin; cluster ring dashed; legend rows --text-xs; gap --space-* tokens.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab reaches peers then legend; arrows move peer focus; Enter selects peer; Escape clears selection and closes menu; focus ring on peer.
- Mouse: hover peer washes --opacity-hover with --shadow-xs; click selects; hover link highlights both peers; drag canvas pans with --cursor-grab; right-click opens peer menu.
- Touch: peers >= --touch-target-min; tap selects; drag canvas pans; pinch zoom optional with button alternative; long-press opens peer menu.
- Dismiss: peer menu closes on Escape + outside + scroll; cluster legend popover closes on Escape with focus back on swatch.
- Offline: cached network renders; sync failure marks legend slot --color-warning; never fake links.
- Debounce: layout recompute debounces --duration-normal; peer load shows skeleton nodes; selection commits at --duration-instant.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over canvas |
| hover | --cursor-pointer | peer wash --opacity-hover | over peer |
| pressed/active | --cursor-grab | canvas pan, --opacity-pressed fill | during pan |
| disabled | --cursor-not-allowed | pointer-events none | when network locked |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus on peer |
| loading | --cursor-progress | peer shimmer --duration-skeleton-shimmer | async network |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Peer select -> --sound-click, layout recompute -> --sound-toggle, load error -> --sound-error, at --sound-volume user opt-in. Haptics: --haptic-light on select. No sound on hover of links.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | clusters stack vertical, degree labels hidden, legend below | width 100% minus --space-4 gutters |
| tablet (--bp-sm..--bp-lg) | two clusters per row, degree labels inline, legend right | fluid minmax tokens |
| desktop (>= --bp-lg) | full canvas, cluster rings, degree labels, legend inline-end | max --measure-reading |

Fluid rules: no fixed px; peer size from degree token; links reroute before peers overlap; degree labels clamp to 1 line; canvas scrolls inside scroll-region only; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Peer order mirrors in RTL; links stay undirected; cluster rings keep identity across mirror; legend order mirrors; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-raised, --color-surface-sunken, --color-brand-soft, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-selection, --color-selection-text, --color-primary, --color-warning, --color-border, --color-border-strong, --color-border-focus, --color-skeleton-base, --color-skeleton-shine, --opacity-hover, --opacity-pressed, --opacity-selected, --opacity-disabled, --radius-full, --shadow-xs, --shadow-focus-glow, --grid-columns, --space-1.--space-6, --text-2xs/xs, --weight-medium, --font-ui, --font-mono, --leading-tight, --duration-instant, --duration-fast, --duration-normal, --duration-skeleton-shimmer, --ease-standard, --icon-size-sm, --icon-stroke-thin, --touch-target-min, --cursor-default/pointer/grab/not-allowed/progress, --sound-click/toggle/error, --sound-volume, --motion-reduced, --bp-sm/md/lg, --chart-1.--chart-12.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; ship all 26 states; cluster color from --chart-* ramp only; pair isolated state with icon + text; hold 40% expansion; announce peer selection via aria; links never carry text alone.
Do not: use color alone for cluster; let links cross peer labels; hide the ring; trap focus in menu; autoplay sound on layout change; ship without peer skeleton; let peers overlap at narrow widths.
Premium treatment: premium treatment: peer drag settles with --ease-standard, link highlight draws at --duration-fast, hub node glows --shadow-xs once at --duration-slow off under --motion-reduced, zero shift when peers load.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- graph: role=img, aria-label network title + peer count
- peer: role=button, aria-label peer title + degree, aria-selected
- link: role=presentation, aria-hidden
- cluster: role=group, aria-label cluster name + member count
- legend: role=list, aria-label cluster legend

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on peers, legend rows, menu trigger; links never focusable; never outline:none.
Contrast: AA 4.5:1 peer text, degree labels, legend text both themes; hub ring --color-primary 3:1; selected --color-selection with --color-selection-text verified pair; focus 3:1.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Peer titles, cluster names, legend text: externalized, 40% expansion, ellipsis policy, no mid-word break.
- Peer degree plural-safe; cluster counts per locale number format; legend order per locale.
- Bidi isolate spans; RTL mirrors peer order; degree digits stay locale-formatted.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: clusters print dashed rings, hubs print solid fill with degree label, isolated peers print dotted ring, legend prints swatch + text, no shimmer, network prints framed at --color-border-strong.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- ('Peers', '5 circles --space-* width, --color-skeleton-base')
- ('Links', '5 lines --icon-size-sm height, --color-skeleton-base')
- ('Clusters', '2 rings --space-* width, --color-skeleton-base')
- ('Legend', '3 rows at --text-xs, --color-skeleton-base')

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced. No pulse on degree labels. aria-busy=true while loading, role=status when peer list lands, skeleton never read as content. Offline/error: skeleton replaced by state panel per section 3, not by blank.

## 16. Icon usage (Lucide names only)

- network for peer nodes, users for cluster, link-2 for undirected link
- Lucide only, --icon-size-sm

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'graph-network' component per data-display/graph-network.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

