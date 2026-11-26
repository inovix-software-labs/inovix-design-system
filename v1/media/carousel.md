# Carousel

> Purpose: Sliding card track with prev next arrows, dot index, auto-advance pause, swipe drag, per-card slot.
> Section: media | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: carousel. Section: media. Sliding card track with prev next arrows, dot index, auto-advance pause, swipe drag, per-card slot.

## 2. Anatomy (parts, ASCII diagram ok)

```
+----------------------------------+
| <  [card] [card] [card]  >       |
|        o o O o                   |
|        2 of 4                    |
+----------------------------------+
```

- **track**: horizontal card row, overflow hidden, gap --space-2
- **card**: aspect slot per card, --radius-lg, --color-skeleton-base until ready
- **arrow**: Lucide chevron-left / chevron-right buttons, --touch-target-min
- **dots**: index dots --icon-size-sm, active dot --color-brand, rest --color-border-strong
- **counter**: --text-xs --color-text-secondary, position of total

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hovered-click | --cursor-pointer | --color-surface-sunken + --opacity-pressed overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| pressed/active | --cursor-pointer | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | transform press scale token, --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no hover fill |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no press |
| selected/checked | N/A: carousel carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| unselected | N/A: carousel carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| expanded/collapsed | N/A: carousel has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: carousel is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | N/A: carousel is not a menu, it has no item activation | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | --cursor-default | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=page |
| visited | N/A: carousel is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: carousel holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: carousel is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: carousel takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | N/A: carousel renders fixed content, an empty data set cannot occur | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no data semantics |
| error | N/A: carousel fetches nothing, no error state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no error semantics |
| success | N/A: carousel completes no async work, no success state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no success semantics |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for carousel are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-lg | rest |
| active-dot | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-lg | dot active |
| paused | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-lg | auto-advance paused |
| dragging | --color-surface-sunken | --color-text-primary | hairline --color-border-strong | --radius-lg | swipe in flight |

Sizes: card width from slot token; gap --space-2; arrows >= --touch-target-min; dots --icon-size-sm; counter --text-xs; track height from card aspect.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab reaches arrows and dots; Left and Right move card; Enter activates card; Home and End jump first and last; Pause key toggles auto-advance.
- Mouse: hover arrow highlights --color-brand-soft; click arrow slides; drag track swipes; dot click jumps; right-click native menu.
- Touch: swipe track moves card; dots >= --touch-target-min; long-press pauses auto-advance; tap card activates.
- Dismiss: Escape pauses auto-advance and clears drag; outside tap ends drag; focus leaves track pauses advance.
- Offline: cached cards render, missing card shows retry slot, position kept, replay on reconnect.
- Debounce: arrow press debounces --duration-fast; drag end debounces --duration-debounce-input; auto-advance window from token.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over card |
| hover | --cursor-pointer | arrow wash --color-brand-soft | over arrows |
| pressed/active | --cursor-grabbing | --opacity-pressed fill | during drag |
| disabled | --cursor-not-allowed | pointer-events none | on end arrows |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus |
| loading | --cursor-progress | card skeleton --duration-skeleton-shimmer | card pending |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Slide -> --sound-toggle, pause -> none, end reached -> --sound-notification, error -> --sound-error. Haptics: --haptic-light on slide. No sound on hover or dot jump.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | one card per view, arrows kept, dots below | stack, gap --space-1 |
| tablet (--bp-sm..--bp-lg) | two cards per view, dots inline | grid minmax tokens |
| desktop (>= --bp-lg) | three cards per view, counter inline-end | same scale |

Fluid rules: no fixed px; card width from slot token; track overflow hidden; dots wrap never; counter clamps; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Track travel mirrors in RTL; arrows swap logical edges; dots order logical; counter stays LTR numeric; card content follows bidi; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-raised, --color-surface-sunken, --color-brand, --color-brand-soft, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-border, --color-border-strong, --color-border-focus, --color-skeleton-base, --color-skeleton-shine, --opacity-hover, --opacity-pressed, --radius-lg, --shadow-sm, --shadow-focus-glow, --space-1, --space-2, --text-xs/sm, --font-ui, --leading-normal, --duration-fast, --duration-normal, --duration-debounce-input, --duration-skeleton-shimmer, --ease-standard, --ease-decelerate, --icon-size-sm, --touch-target-min, --cursor-pointer, --cursor-grabbing, --cursor-not-allowed, --cursor-progress, --sound-toggle, --sound-notification, --sound-error, --motion-reduced, --bp-sm, --bp-lg.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; dots paired with counter text; slide announced via aria-live; pause button labeled; hold 40% expansion; keyboard slide always available.
Do not: hardcode card width; use color alone for active dot; hide the ring; autoplay without pause control; ship without card skeleton; let track overflow viewport; fixed dot count.
Premium treatment: premium treatment: slide glide --ease-in-out, dot fill --color-brand with --stagger-step, drag rubber band --ease-bounce, zero shift on card swap.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- track: role=region, aria-roledescription carousel, aria-label card set
- card: role=group, aria-label card position of total
- arrow: role=button, aria-label previous or next card
- dots: role=tablist, each dot role=tab, aria-selected
- counter: role=status, aria-live=polite, position text

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on arrows and dots, never outline:none.
Contrast: AA 4.5:1 counter, dot labels both themes; active dot --color-brand on --color-surface-raised verified 3:1 non-text; focus ring 3:1.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Card labels, counter text, arrow labels: externalized, 40% expansion, ellipsis policy.
- Counter plural-safe per locale; position format per locale token.
- Bidi isolate spans; RTL mirrors arrow placement and track travel, counter stays LTR numeric.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: track prints framed, active dot prints filled, counter prints mono text, arrows print glyphs, no shimmer.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Card: width 70% bar at card aspect, --color-skeleton-base
- Arrow: square --icon-size-md at each edge, --color-skeleton-base
- Dots: 4 squares --icon-size-sm centered, --color-skeleton-base

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced. aria-busy=true while card loads, role=status when card lands, skeleton never read as content. Failure replaces skeleton with retry slot.

## 16. Icon usage (Lucide names only)

- Lucide chevron-left, chevron-right for arrows, pause for auto-advance, dot per index
- Lucide only, --icon-size-sm

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'carousel' component per media/carousel.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

