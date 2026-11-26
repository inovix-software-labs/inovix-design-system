# Modal

> Purpose: Blocking surface layer at --z-modal that dims the page behind --color-scrim at --opacity-scrim, traps focus inside --color-surface-overlay until dismissed, and returns focus to the trigger on close.
> Section: overlays | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: modal. Section: overlays. Blocking surface layer at --z-modal that dims the page behind --color-scrim at --opacity-scrim, traps focus inside --color-surface-overlay until dismissed, and returns focus to the trigger on close.

## 2. Anatomy (parts, ASCII diagram ok)

```
+-----------------------------------------+
| x                                         |
| title                                     |
|                                           |
| body scrolls inside the surface           |
| [cancel]   [confirm]                      |
+-----------------------------------------+
```

- **container**: --color-surface-overlay at --z-modal, --radius-lg, focus trap inside
- **title**: --text-lg --weight-semibold --color-text-primary, aria-labelledby
- **close**: Lucide x, --touch-target-min, dismisses on press
- **body**: scrollable region, --color-text-primary on raised overlay
- **footer**: action buttons, --color-text-secondary, aligned inline-end

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hovered-click | --cursor-pointer | --color-surface-sunken + --opacity-pressed overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| pressed/active | N/A: modal has no press phase, it commits on click | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no hover fill |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no press |
| selected/checked | N/A: modal carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| unselected | N/A: modal carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| expanded/collapsed | N/A: modal has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | --cursor-default | --color-surface-overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | enter --motion-enter, exit --motion-exit | silent (sound events only via --sound-* tokens, user opt-in) | aria-hidden when closed, role=dialog when open |
| active menu item | N/A: modal is not a menu, it has no item activation | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | N/A: modal does not navigate, no current-page concept | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no navigation semantics |
| visited | N/A: modal is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: modal holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: modal is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: modal takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | N/A: modal renders fixed content, an empty data set cannot occur | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no data semantics |
| error | N/A: modal fetches nothing, no error state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no error semantics |
| success | N/A: modal completes no async work, no success state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no success semantics |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for modal are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-overlay | --color-text-primary | hairline --color-border-strong | --radius-lg | standard blocking modal |
| destructive | --color-surface-overlay | --color-text-primary | hairline --color-error | --radius-lg | delete or remove actions |
| compact | --color-surface-overlay | --color-text-primary | hairline --color-border | --radius-md | small choice set |
| full | --color-surface-overlay | --color-text-primary | hairline --color-border-strong | --radius-none | full viewport layer |

Sizes: width clamp via --space-* tokens, max width --measure-reading, min height from --space-* tokens, close target >= --touch-target-min.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab cycles modal controls only, Escape closes and returns focus to the trigger, focus trap active while open.
- Mouse: click close dismisses, click outside scrim inert unless declared, no drag by default, right-click native menu.
- Touch: close target >= --touch-target-min, outside tap closes only where declared, no swipe dismiss without alternate, long-press not used.
- Dismiss: Escape + close button + scrim tap where declared, focus returns to trigger, close announced politely.
- Offline: modal content cached, actions queued and replayed on reconnect, never silently dropped.
- Debounce: close events debounce --duration-fast, async open shows skeleton overlay.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over scrim or surface |
| hover | --cursor-pointer | --opacity-hover fill | over close button |
| pressed/active | --cursor-pointer | --opacity-pressed fill | during close press |
| disabled | --cursor-not-allowed | pointer-events none | when disabled |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | on focused control |
| loading | --cursor-progress | skeleton shimmer --duration-skeleton-shimmer | async content |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Open -> none; close -> --sound-click; error -> --sound-error. Haptics: --haptic-medium on close. No sound on hover or focus.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | full height minus --space-safe-top and --space-safe-bottom | width 100% minus gutters |
| tablet (--bp-sm..--bp-lg) | centered, max width --measure-reading | fluid minmax tokens |
| desktop (>= --bp-lg) | centered at token scale, no fixed widths | same scale, no layout shift |

Fluid rules: no fixed px; width from --space-* / --measure-* tokens; height capped by viewport tokens; collapse then stack then hide.

## 9. RTL mirror behavior (what flips, what stays)

Title and body follow bidi direction, close mirrors to inline-start in RTL, no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-overlay, --color-scrim, --opacity-scrim, --color-text-primary, --color-text-secondary, --color-border, --color-border-strong, --color-border-focus, --color-error, --radius-lg, --radius-md, --radius-none, --shadow-lg, --shadow-scrim, --shadow-focus-glow, --space-4.--space-8, --space-safe-top/bottom, --text-base/lg/xl, --weight-medium/semibold, --font-ui, --leading-normal, --duration-fast, --duration-skeleton-shimmer, --ease-standard, --cursor-default/pointer/not-allowed/progress, --sound-click/error, --sound-volume, --motion-reduced, --bp-sm, --bp-lg, --touch-target-min, --z-modal.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; trap focus inside the modal; return focus to the trigger on close; pair every action with an accessible label; hold 40% expansion.
Do not: hardcode width or height; use color alone for state; hide the focus ring; trap focus without an escape path; autoplay sound; ship without scrim; let content overflow the viewport.
Premium treatment: premium glass blur behind the scrim via --glass-bg / --glass-blur, refined close press with --opacity-pressed, crisp focus ring, zero layout shift on open and close.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- container: role=dialog, aria-modal=true, aria-labelledby title
- title: id referenced by aria-labelledby on container
- close: role=button, aria-label close modal, --touch-target-min
- scrim: aria-hidden=true behind the dialog
- footer: role=group, aria-label modal actions

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on the focused control inside the modal, never outline:none.
Contrast: AA 4.5:1 title and body on overlay both themes; close control 3:1; focus ring 3:1; --color-text-primary on --color-surface-overlay verified.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Title, body, close label, action text: externalized, 40% expansion, ellipsis policy, no mid-word break.
- Modal open and close announcements per locale token.
- Bidi isolate spans; RTL mirrors close position and body alignment.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Prints inline without scrim or ring, title and body grayscale, no interactive states, page breaks avoided inside body.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Panel: full-width block at --radius-lg, --color-skeleton-base
- Title: width 60% bar at --text-lg, --color-skeleton-base
- Close: square --touch-target-min at inline-end, --color-skeleton-base
- Body: width 80% block at --text-base, --color-skeleton-base

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced static gray. aria-busy=true while loading, role=alertdialog announcement when content lands, skeleton never read as content.

## 16. Icon usage (Lucide names only)

- x for close at --icon-size-md
- alert-circle for error, check-circle for success
- Lucide only, --icon-size-md

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'modal' component per overlays/modal.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

