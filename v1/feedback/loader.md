# Loader

> Purpose: Loader wrapper: any skeleton or spinner policy, size tokens, reduced-motion static, aria-busy region.
> Section: feedback | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: loader. Section: feedback. Loader wrapper: any skeleton or spinner policy, size tokens, reduced-motion static, aria-busy region.

## 2. Anatomy (parts, ASCII diagram ok)

```
+-----------------+
|    ( indicator )|
|    label        |
+-----------------+
```

- **region**: loader region, --color-surface-raised, min height token
- **indicator**: spinner or skeleton per policy, --icon-size-md
- **label**: optional label, --text-xs --color-text-tertiary

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | N/A: loader is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| hover | N/A: loader is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| hovered-click | N/A: loader is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| pressed/active | N/A: loader is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| clicked | N/A: loader is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| focus-visible | N/A: loader is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| focus | N/A: loader is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| disabled | N/A: loader is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| disabled + hover | N/A: loader is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| disabled + pressed | N/A: loader is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| selected/checked | N/A: loader carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| unselected | N/A: loader carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| expanded/collapsed | N/A: loader has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: loader is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | N/A: loader is not a menu, it has no item activation | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | N/A: loader does not navigate, no current-page concept | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no navigation semantics |
| visited | N/A: loader is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: loader holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: loader is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: loader takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | N/A: loader renders fixed content, an empty data set cannot occur | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no data semantics |
| error | N/A: loader fetches nothing, no error state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no error semantics |
| success | N/A: loader completes no async work, no success state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no success semantics |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for loader are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-md | rest |
| inline | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-none | inline loader |
| overlay | --color-surface-overlay | --color-text-primary | hairline --color-border | --radius-lg | overlay loader |
| skeleton | --color-skeleton-base | --color-text-primary | hairline --color-border | --radius-md | skeleton policy |

Sizes: region min height --space-* tokens; indicator --icon-size-md; label --text-xs; width fluid.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab enters the interactive parts; Enter activates; Escape dismisses where declared; arrows move within groups; focus ring on every interactive part.
- Mouse: hover washes --opacity-hover with no layout shift; press at --opacity-pressed; click activates; drag only with keyboard alternative; right-click native menu.
- Touch: every target >= --touch-target-min; long-press previews only where declared; swipe only where declared; no hover-only path on coarse pointers.
- Dismiss: Escape + outside click close where declared; focus returns to trigger; no trap without scrim.
- Offline: cached content renders, queue mutations, replay on reconnect, conflict note --color-warning.
- Debounce: user-driven changes debounce --duration-debounce-input; async pending announced via aria-busy; no double-commit.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | root idle |
| hover | --cursor-default | none | no hover state on a display element |
| pressed/active | N/A: this element is not pressable, it displays data | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent | no press semantics |
| disabled | --cursor-not-allowed | pointer-events none | when disabled |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus |
| loading | --cursor-progress | skeleton shimmer --duration-skeleton-shimmer | async data |
| pressed/active | --cursor-default | none | region not pressable |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. No sound on appear, spin, or dismiss. Haptics none. Sound policy belongs to micro-interactions/sound.md.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | stack to single column, hide secondary meta | width 100% minus --space-4 gutters |
| tablet (--bp-sm..--bp-lg) | two-column grid where listed, meta inline | fluid minmax tokens |
| desktop (>= --bp-lg) | full grid, meta inline, max --measure-reading | same scale, no fixed widths |

Fluid rules: no fixed px; all widths from --space-* / --measure-* / --bp-* tokens; text wraps, never truncates without ellipsis policy; horizontal scroll only inside scroll-region; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Region centers content; indicator is circular, no flip; label follows bidi; overlay anchors to region; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-raised, --color-surface-sunken, --color-brand-soft, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-text-disabled, --color-error, --color-success, --color-warning, --color-info, --color-border, --color-border-strong, --color-border-focus, --color-skeleton-base, --color-skeleton-shine, --opacity-hover, --opacity-pressed, --opacity-disabled, --radius-md, --shadow-sm, --shadow-focus-glow, --space-1.--space-4, --text-xs/sm/base, --weight-medium, --font-ui, --leading-normal, --duration-fast, --duration-normal, --duration-debounce-input, --duration-skeleton-shimmer, --ease-standard, --icon-size-sm/md, --icon-stroke-thin, --touch-target-min, --cursor-default/pointer/not-allowed/progress, --sound-volume, --motion-reduced, --bp-sm/md/lg, --measure-reading, --color-surface-overlay, --color-skeleton-base, --color-skeleton-shine, --z-overlay, --opacity-scrim.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens by name; ship all 26 states from section 3; pair every status with icon + text; hold 40% text expansion; announce state changes via aria; print grayscale readable.
Do not: hardcode a value; use color alone for meaning; hide the focus ring; trap focus; autoplay sound; ship without a skeleton; let text overflow the element.
Premium treatment: calm resting surface, refined hover as a wash never a color jump, tactile press at --opacity-pressed, crisp --shadow-focus-glow ring, graceful disabled at --opacity-disabled, loading skeleton matching the final layout with zero shift.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- root: role set from the component, accessible name from visible label
- region: role=region or status, aria-label loading, aria-busy=true
- indicator: aria-hidden=true, decorative
- label: role=text, aria-hidden=false

Focus: :focus-visible ring --shadow-focus-glow + 2 units of --color-border-focus width, never :focus-only styling, never outline:none without replacement.
Contrast: AA 4.5:1 text on every fill both themes (verified in theme-variables.md contrast table); semantic fills pair with content tokens; focus indicator clears 3:1; disabled text exempt but above 4.5:1 on sunken surfaces.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Visible text: externalized string, 40% expansion from en, ellipsis token policy, no mid-word break.
- Counts and values plural-safe per CLDR category, locale number format.
- Bidi isolate spans; RTL mirrors inline edges; numbers stay locale-formatted.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: fills drop to hairlines, status prints icon + text, no ring, no shimmer, element prints framed at --color-border-strong.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Region: full-width block at region height, radius --radius-md, --color-skeleton-base
- Indicator: square --icon-size-md centered, --color-skeleton-base
- Label: width 30% bar at --text-xs, --color-skeleton-base

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced (static gray). No pulse on text. aria-busy=true while loading, role=status announcement when content lands, skeleton never read as content. Offline/error: skeleton replaced by state panel per section 3, not by blank.

## 16. Icon usage (Lucide names only)

- loader for indicator, inbox for empty, alert-circle for error
- circle-help for label hint at --icon-size-sm

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'loader' component per feedback/loader.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

