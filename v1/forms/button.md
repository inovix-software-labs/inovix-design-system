# Button

> Purpose: Primary, secondary, ghost, outline and danger actions with sm/md/lg heights, loading spinner swap, icon + label policy, hit floor via --touch-target-min.
> Section: forms | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: button. Section: forms. Primary, secondary, ghost, outline and danger actions with sm/md/lg heights, loading spinner swap, icon + label policy, hit floor via --touch-target-min.

## 2. Anatomy (parts, ASCII diagram ok)

```
+---------------------------------------------+
| (icon)  Label            | spinner when busy |
+---------------------------------------------+
```

- **label**: visible action text, --text-sm --weight-semibold, never icon alone
- **icon**: optional leading or trailing Lucide, --icon-size-md, --icon-gap from label
- **spinner**: replaces label at loading + disabled, --duration-normal linear rotate
- **hit area**: padding box never below --touch-target-min even at sm

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
| selected/checked | N/A: button carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| unselected | N/A: button carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| expanded/collapsed | N/A: button has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: button is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | N/A: button is not a menu, it has no item activation | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | N/A: button does not navigate, no current-page concept | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no navigation semantics |
| visited | N/A: button is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: button holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: button is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: button takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | N/A: button renders fixed content, an empty data set cannot occur | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no data semantics |
| error | N/A: button fetches nothing, no error state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no error semantics |
| success | N/A: button completes no async work, no success state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no success semantics |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for button are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| primary | --color-primary fill | --color-primary-content | transparent border | --radius-sm | default action, one per view region (rule 28c) |
| secondary | --color-secondary fill | --color-secondary-content | transparent border | --radius-sm | supporting action |
| ghost | transparent | --color-text-primary | transparent | --radius-sm | low emphasis inside panels |
| outline | transparent | --color-text-primary | hairline --color-border-strong | --radius-sm | tertiary on calm surfaces |
| danger | --color-error fill | --color-error-content | transparent | --radius-sm | destructive, always confirm first |

Sizes: sm / md / lg heights from --space-* + --text-* tokens; every size keeps hit area >= --touch-target-min; sm text never below --text-xs; lg never above --text-xl; icon-only variant is a square of the same height with aria-label + tooltip.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab enters, Shift+Tab leaves; Enter and Space both activate; Space prevents page scroll during press; Escape cancels a press in progress; disabled buttons stay in tab order only when aria-disabled is used, otherwise removed from order.
- Mouse: hover at --opacity-hover with zero layout shift; press at --opacity-pressed; click debounce --duration-fast; double-click never fires twice on submit; right-click is native context menu, never repurposed.
- Touch: every target >= --touch-target-min; long-press is not a button behavior; swipe never triggers; tap delay removed via touch-action manipulation token policy.
- Dismiss: not applicable, buttons are not overlays.
- Offline: queue the intent, mark --color-warning, replay on reconnect only for idempotent actions; destructive actions never replay silently.
- Debounce: async actions debounce --duration-debounce-input; submit disables at --duration-fast to block double submit; validation pending shows spinner not a new button.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | root idle |
| hover | --cursor-pointer | background --opacity-hover wash | on every enabled variant |
| pressed/active | --cursor-pointer | scale press token + --opacity-pressed | on the button |
| disabled | --cursor-not-allowed | pointer-events none | when disabled or loading + disabled |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus |
| loading | --cursor-progress | spinner --duration-normal linear | async in flight |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Submit success -> --sound-success, validation error -> --sound-error, toggle-family buttons -> --sound-toggle, each at --sound-volume, user opt-in, off under --motion-reduced for haptics. No sound on hover, focus, or press. Haptics: --haptic-light on press, --haptic-medium on success, --haptic-heavy on destructive confirm.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | full-width rows, label above icon, height md | width 100% minus --space-4 gutters |
| tablet (--bp-sm..--bp-lg) | inline icon + label groups, height md | fluid minmax tokens |
| desktop (>= --bp-lg) | compact groups, height sm allowed | same scale, no fixed widths |

Fluid rules: no fixed px; heights from --space-*; text wraps never truncates; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Label and icon keep DOM order; leading icon sits inline-start and mirrors in RTL; trailing icon mirrors to inline-end; text-align start; arrow icons flip direction; the press scale origin stays center.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-raised, --color-surface-sunken, --color-brand-soft, --color-text-primary, --color-text-disabled, --color-primary, --color-primary-content, --color-secondary, --color-secondary-content, --color-error, --color-error-content, --color-border, --color-border-strong, --color-border-focus, --color-warning, --color-success, --color-skeleton-base, --color-skeleton-shine, --opacity-hover, --opacity-pressed, --opacity-disabled, --radius-sm, --shadow-sm, --shadow-focus-glow, --space-1.--space-4, --text-sm, --text-xs, --weight-semibold, --font-ui, --leading-tight, --tracking-tight, --duration-fast, --duration-normal, --duration-debounce-input, --ease-standard, --icon-size-md, --icon-stroke-thin, --icon-gap, --touch-target-min, --cursor-pointer, --cursor-not-allowed, --cursor-progress, --sound-success, --sound-error, --sound-toggle, --sound-volume, --motion-reduced, --bp-sm, --bp-lg.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens by name; ship all 26 states from section 3; keep one primary-filled action per view region (rule 28c); hold --touch-target-min at every size; disable at --duration-fast during async submit; pair every danger action with a confirm overlay.
Do not: hardcode a color or height; use emoji as the label; stack two primary fills in one region; hide the focus ring; autoplay sound on hover; ship a submit button without a skeleton or pending state; let double-click fire twice.
Premium treatment: calm resting fill, refined hover as a subtle tint or elevation shift never a color jump, tactile press scale, crisp --shadow-focus-glow ring, graceful disabled at --opacity-disabled, loading spinner that matches the final label width so nothing reflows.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- button: role=button or native button, accessible name from visible label, aria-disabled when soft-disabled
- icon: aria-hidden=true when decorative, aria-label when icon-only
- spinner: aria-hidden=true, announced via the button aria-busy=true
- group: role=group when buttons form a toolbar, name from toolbar label

Focus: :focus-visible ring --shadow-focus-glow + 2 units of --color-border-focus width, never :focus-only styling, never outline:none without replacement; ring order after border, inside overflow.
Contrast: AA 4.5:1 label on every fill both themes (verified in theme-variables.md contrast table); danger fill pairs with --color-error-content; disabled text is exempt but stays above 4.5:1 on sunken surfaces; focus indicator clears 3:1 on adjacent surfaces.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Label: externalized string, 40% expansion from en, ellipsis token policy, no mid-word break.
- Icon-only variant: aria-label externalized, tooltip externalized, never a bare icon.
- Loading label swap: pending / done strings externalized, plural-safe.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: fill drops to outline in print, label stays; danger prints with the word danger, never color alone; no shadow, no spinner animation, spinner prints as the word loading; background fills off except the danger outline.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Label: width 40% bar at --text-sm --leading-normal, --color-skeleton-base
- Icon: square --icon-size-md at --space-1 offset, --color-skeleton-base
- Hit area: full button box at component height token, radius --radius-sm, --color-skeleton-base

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced (static gray). No pulse on text. aria-busy=true while loading, role=status announcement when content lands, skeleton never read as content. Offline/error: skeleton replaced by state panel per section 3, not by blank.

## 16. Icon usage (Lucide names only)

- leading action icons per verb: plus, check, x, arrow-right, pencil, trash-2, download, upload, search, filter
- spinner: loader-2 rotated --duration-normal linear
- danger pair: alert-triangle beside destructive labels when space allows

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'button' component per forms/button.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

