# Kpi

> Purpose: Key performance indicator card: metric, target progress, threshold band, trend note, drill link.
> Section: data-display | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: kpi. Section: data-display. Key performance indicator card: metric, target progress, threshold band, trend note, drill link.

## 2. Anatomy (parts, ASCII diagram ok)

```
+-------------------------------+
| metric label                  |
| value  --font-mono            |
| [====track====] threshold |   |
| trend note          drill >   |
+-------------------------------+
```

- **metric**: --text-2xl --font-mono tabular, --color-text-primary
- **progress**: bar toward target, fill --color-primary, track --color-surface-sunken, --radius-full
- **threshold**: band marker, --color-warning or --color-success per state
- **note**: trend sentence, --text-xs --color-text-secondary
- **link**: drill action, --touch-target-min

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hovered-click | --cursor-pointer | --color-surface-sunken + --opacity-pressed overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| pressed/active | N/A: kpi has no press phase, it commits on click | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no hover fill |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no press |
| selected/checked | N/A: kpi carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| unselected | N/A: kpi carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| expanded/collapsed | N/A: kpi has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: kpi is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | N/A: kpi is not a menu, it has no item activation | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | --cursor-default | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=page |
| visited | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-secondary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | history visited, no style-only meaning |
| invalid + disabled | N/A: kpi holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: kpi is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: kpi takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide inbox, --color-text-tertiary | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=status 'No items' |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-*, --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |
| success | --cursor-default | --color-surface-raised | hairline --color-success | --color-text-primary | Lucide check-*, --color-success | none at --duration-instant | --sound-success token if user enabled | role=status announced once |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for kpi are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-lg | rest |
| on-target | --color-surface-raised | --color-text-primary | hairline --color-success | --radius-lg | progress at goal |
| at-risk | --color-surface-raised | --color-text-primary | hairline --color-warning | --radius-lg | progress below band |
| off-target | --color-surface-raised | --color-text-primary | hairline --color-error | --radius-lg | progress failed |

Sizes: metric --text-2xl; progress bar height --space-1; padding --space-4; link >= --touch-target-min; width fluid.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab reaches link; Enter drills; arrows not used; Escape blurs; focus ring on link.
- Mouse: hover link underlines --color-accent; click drills; hover card lifts --shadow-sm; no drag; right-click native menu.
- Touch: link >= --touch-target-min; long-press previews; swipe not used.
- Dismiss: not applicable.
- Offline: cached metric renders, band marked --color-warning, replay on reconnect.
- Debounce: metric refresh debounces --duration-debounce-input; async load shows skeleton card.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over card |
| hover | --cursor-pointer | link underline --color-accent | over link |
| pressed/active | --cursor-pointer | --opacity-pressed fill | during drill |
| disabled | --cursor-not-allowed | pointer-events none | when link disabled |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus |
| loading | --cursor-progress | skeleton shimmer --duration-skeleton-shimmer | async metric |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Drill -> --sound-click, threshold breach -> --sound-warning, error -> --sound-error. Haptics: --haptic-light on breach. No sound on hover.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | stack to single column, hide secondary meta | width 100% minus --space-4 gutters |
| tablet (--bp-sm..--bp-lg) | two-column grid where listed, meta inline | fluid minmax tokens |
| desktop (>= --bp-lg) | full grid, meta inline, max --measure-reading | same scale, no fixed widths |

Fluid rules: no fixed px; all widths from --space-* / --measure-* / --bp-* tokens; text wraps, never truncates without ellipsis policy; horizontal scroll only inside scroll-region; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Content aligns start; progress bar runs inline-start to inline-end and mirrors in RTL; threshold marker stays on bar; link mirrors to inline-end; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-raised, --color-surface-sunken, --color-brand-soft, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-text-disabled, --color-primary, --color-primary-content, --color-success, --color-warning, --color-error, --color-accent, --color-border, --color-border-strong, --color-border-focus, --color-skeleton-base, --color-skeleton-shine, --opacity-hover, --opacity-pressed, --opacity-disabled, --radius-lg, --radius-full, --shadow-sm, --shadow-focus-glow, --space-1.--space-6, --text-xs/sm/base/2xl, --weight-medium/semibold, --font-ui, --font-mono, --leading-normal, --duration-fast, --duration-normal, --duration-debounce-input, --duration-skeleton-shimmer, --ease-standard, --icon-size-sm/md, --icon-stroke-thin, --touch-target-min, --cursor-default/pointer/not-allowed/progress, --sound-click/warning/error, --sound-volume, --motion-reduced, --bp-sm/md/lg, --measure-reading.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; ship all 26 states; pair band with icon + text; announce progress via aria-valuenow; hold 40% expansion.
Do not: hardcode bar height; use color alone for band; hide the ring; trap focus; autoplay sound; ship without card skeleton; let metric overflow the card.
Premium treatment: calm raised surface, refined hover as link underline, tactile drill press, crisp ring, graceful disabled, loading card matching final card size with zero shift.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- card: role=article or region, name from metric label
- progress: role=progressbar, aria-valuenow/min/max, aria-label progress to target
- threshold: aria-hidden=true, decorative
- link: role=link, accessible name, --touch-target-min

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on link only, never outline:none.
Contrast: AA 4:5:1 metric, note, link both themes; band pairs icon + text; progress fill --color-primary on sunken track clears 3:1; focus 3:1.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Label, note, link text: externalized, 40% expansion, ellipsis policy, no mid-word break.
- Metric per locale number format; target plural-safe.
- Bidi isolate spans; RTL mirrors progress direction and link position.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: progress prints as solid bar with text percent, band prints as word, no ring, no shimmer, card prints framed.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Card: full-width block at card height, radius --radius-lg, --color-skeleton-base
- Progress: bar width 80%, height --space-1, --color-skeleton-base
- Metric: width 50% bar at --text-2xl height, --color-skeleton-base
- Link: width 20% bar at --text-sm, --color-skeleton-base

Fill --color-skeleton-base, shimmer --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced. aria-busy=true while loading, role=status when content lands. Offline/error: skeleton replaced by state panel per section 3.

## 16. Icon usage (Lucide names only)

- trending-up / trending-down for note, flag for threshold, arrow-right for drill, alert-circle for error
- Lucide only, --icon-size-sm / --icon-size-md

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'kpi' component per data-display/kpi.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

