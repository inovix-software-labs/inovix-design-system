# Header

> Purpose: Top stripe at --header-height and --z-header, sticky on scroll, brand and utilities.
> Section: layout | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: header. Section: layout. Top stripe at --header-height and --z-header, sticky on scroll, brand and utilities.

## 2. Anatomy (parts, ASCII diagram ok)

```
+-----------------------------------------+
| [=] INOVIX        search   [theme][user]  |
+-----------------------------------------+
```

- **container**: --color-header-bg at --header-height, --z-header
- **brand**: INOVIX text logo, 3 lines, --logo-* tokens, white on navy
- **actions**: --touch-target-min, aligned inline-end
- **utilities**: --text-base --color-navy-300
- **divider**: hairline --color-header-border at bottom

## 2b. Build notes (authoritative, read before the state matrix)

These notes win over any older line in this file.

- The header is brand navy (--color-header-bg) with white text (--color-header-text) in BOTH themes. It is never a white or raised surface. Toggling the theme does not change the header.
- Left to right: sidebar toggle (animated hamburger to X, --touch-target-min square, white icon), then the INOVIX text logo (3 lines, brand/logo.md), then flexible space, then page title or search if the app has one, then utilities at inline-end: theme toggle, language switcher, user menu avatar.
- The sidebar toggle lives here, inline-start, so it stays reachable when the sidebar is fully hidden on mobile.
- The logo is the only brand element. No icon, no image, no extra product name next to it.
- Height is --header-height at every breakpoint. The 3 line lockup is vertically centered and never clipped. Descriptor and tagline hide first at narrow widths (brand/logo-responsive.md).
- Header sits at --z-header, position fixed to the top, full width. Bottom edge is a hairline --color-header-border plus --shadow-sm once the main region has scrolled.
- Header controls: icon buttons are transparent with --color-header-text icons, hover fill --color-navy-800, pressed fill --color-navy-900, focus ring --color-border-focus offset from the edge (use --color-navy-300 ring if the accent ring fails 3:1 on navy; check theming/color-palette.md).
- Page content never goes under the header: main region starts at --header-height.


## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-header-bg | hairline --color-header-border | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hover | --cursor-pointer | --color-navy-800 | hairline --color-header-border | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hovered-click | --cursor-pointer | --color-navy-800 + --opacity-pressed overlay | hairline --color-header-border | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| pressed/active | N/A: header has no press phase, it commits on click | --color-header-bg | hairline --color-header-border | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| clicked | --cursor-pointer | --color-header-bg | hairline --color-header-border | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus-visible | --cursor-default | --color-header-bg | 2 units --color-border-focus + --shadow-focus-glow | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus | --cursor-default | --color-header-bg | hairline --color-header-border (no ring; ring is focus-visible only) | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| disabled | --cursor-not-allowed | --color-navy-800 | hairline --color-header-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true |
| disabled + hover | --cursor-not-allowed | --color-navy-800 | hairline --color-header-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no hover fill |
| disabled + pressed | --cursor-not-allowed | --color-navy-800 | hairline --color-header-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no press |
| selected/checked | N/A: header carries no selection, it renders supplied data only | --color-header-bg | hairline --color-header-border | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| unselected | N/A: header carries no selection, it renders supplied data only | --color-header-bg | hairline --color-header-border | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| expanded/collapsed | N/A: header has no disclosure subtree, nothing to expand | --color-header-bg | hairline --color-header-border | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: header is not an overlay, it never opens or closes | --color-header-bg | hairline --color-header-border | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | N/A: header is not a menu, it has no item activation | --color-header-bg | hairline --color-header-border | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | --cursor-default | --color-brand-soft | hairline --color-header-border | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=page |
| visited | --cursor-pointer | --color-header-bg | hairline --color-header-border | --color-navy-300 | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | history visited, no style-only meaning |
| invalid + disabled | N/A: header holds no user input, no validity state exists | --color-header-bg | hairline --color-header-border | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: header is not editable, readonly does not apply | --color-header-bg | hairline --color-header-border | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: header takes no input, required + filled does not apply | --color-header-bg | hairline --color-header-border | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-header-bg | hairline --color-header-border | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-header-border | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-header-bg | hairline --color-header-border | --color-header-text | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | N/A: header renders fixed content, an empty data set cannot occur | --color-header-bg | hairline --color-header-border | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no data semantics |
| error | N/A: header fetches nothing, no error state exists | --color-header-bg | hairline --color-header-border | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no error semantics |
| success | N/A: header completes no async work, no success state exists | --color-header-bg | hairline --color-header-border | --color-header-text | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no success semantics |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for header are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-header-bg | --color-header-text | hairline --color-header-border | --radius-none | standard sticky stripe |
| scrolled | --color-header-bg | --color-header-text | hairline --color-header-border | --radius-none | shadow on scroll |
| compact | --color-header-bg | --color-header-text | hairline --color-header-border | --radius-none | reduced height |
| hairline | --color-header-bg | --color-header-text | hairline --color-header-border | --radius-none | border-only bottom |

Sizes: bar height --header-height, brand --text-lg, actions >= --touch-target-min, width 100% viewport.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab reaches brand then actions, Enter activates.
- Mouse: hover action underlines --color-accent, click activates, brand click home.
- Touch: targets >= --touch-target-min, long-press not used.
- Dismiss: not applicable, persistent stripe.
- Offline: chrome cached, renders instantly.
- Debounce: scroll stickiness debounce --duration-fast.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over bar |
| hover | --cursor-pointer | link underline --color-header-text | over action |
| pressed/active | --cursor-pointer | --opacity-pressed fill | during activate |
| disabled | --cursor-not-allowed | pointer-events none | when disabled |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus |
| loading | --cursor-progress | skeleton header --duration-skeleton-shimmer | async brand |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Action activate -> --sound-click. Haptics none. No sound on hover.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | actions under hamburger | width 100% minus gutters |
| tablet (--bp-sm..--bp-lg) | inline max width --measure-reading | fluid minmax tokens |
| desktop (>= --bp-lg) | inline full width | same scale, no layout shift |

Fluid rules: no fixed px; width 100% viewport, gaps from --space-* tokens, collapse to hamburger then hide.

## 9. RTL mirror behavior (what flips, what stays)

Brand and actions mirror inline edges in RTL, no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-header-bg, --color-header-text, --color-navy-300, --color-accent, --color-border, --color-header-border, --color-border-focus, --radius-none, --radius-md, --shadow-md, --shadow-focus-glow, --space-1.--space-6, --space-gutter, --text-base/lg, --weight-medium/semibold, --font-ui, --leading-normal, --duration-fast, --ease-standard, --cursor-default/pointer/not-allowed/progress, --sound-click, --sound-volume, --motion-reduced, --bp-sm, --bp-lg, --touch-target-min, --header-height, --z-header.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; label brand; underline hover not color alone; hold 40% expansion.
Do not: hardcode bar height; hide the ring; trap focus; autoplay sound; fixed px widths; let actions overflow bar.
Premium treatment: premium sticky entry with --shadow-md on scroll, crisp ring, zero layout shift on scroll.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- container: role=banner
- brand: role=link, aria-label brand home
- actions: role=button, accessible name
- utilities: role=link, accessible name
- divider: aria-hidden=true, visual only

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on focused action, never outline:none.
Contrast: AA 4.5:1 brand and actions both themes; hover underline 3:1; focus ring 3:1; --color-header-text on --color-header-bg verified.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Brand label, action text: externalized, 40% expansion, ellipsis policy, no mid-word break.
- Action order per locale token.
- Bidi isolate spans; RTL mirrors bar inline edges.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Prints stripe as text line, brand and actions as text, no ring or shadow, no interactive states.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Bar: full-width block height --header-height, --color-skeleton-base
- Brand: width 30% bar at --text-lg, --color-skeleton-base
- Action: square --touch-target-min, --color-skeleton-base

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced static gray. aria-busy=true while loading, role=status announcement when content lands, skeleton never read as content.

## 16. Icon usage (Lucide names only)

- alert-circle for header error
- Lucide only, --icon-size-md

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-navy-300 / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'header' component per layout/header.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

