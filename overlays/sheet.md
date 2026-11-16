# Sheet

> Purpose: Bottom slide-in sheet at --z-modal over scrim dim, height capped by --footer-min-height, grab handle, dismiss on swipe down or Escape.
> Section: overlays | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: sheet. Section: overlays. Bottom slide-in sheet at --z-modal over scrim dim, height capped by --footer-min-height, grab handle, dismiss on swipe down or Escape.

## 2. Anatomy (parts, ASCII diagram ok)

```
+-----------------------------------------+
| = handle                                  |
| title                       x             |
|                                           |
| body scrolls inside the sheet             |
+-----------------------------------------+
```

- **container**: --color-surface-overlay at --z-modal, slides up from bottom
- **handle**: grab bar, --radius-full, --touch-target-min
- **title**: --text-lg --weight-semibold --color-text-primary, aria-labelledby
- **close**: Lucide x, --touch-target-min, dismisses on press
- **body**: scrollable region, --color-text-primary on raised sheet

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hovered-click | --cursor-pointer | --color-surface-sunken + --opacity-pressed overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| pressed/active | N/A: sheet has no press phase, it commits on click | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no hover fill |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no press |
| selected/checked | N/A: sheet carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| unselected | N/A: sheet carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| expanded/collapsed | N/A: sheet has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | --cursor-default | --color-surface-overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | enter --motion-enter, exit --motion-exit | silent (sound events only via --sound-* tokens, user opt-in) | aria-hidden when closed, role=dialog when open |
| active menu item | N/A: sheet is not a menu, it has no item activation | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | N/A: sheet does not navigate, no current-page concept | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no navigation semantics |
| visited | N/A: sheet is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: sheet holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: sheet is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: sheet takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | N/A: sheet renders fixed content, an empty data set cannot occur | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no data semantics |
| error | N/A: sheet fetches nothing, no error state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no error semantics |
| success | N/A: sheet completes no async work, no success state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no success semantics |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for sheet are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-overlay | --color-text-primary | hairline --color-border-strong | --radius-lg | standard bottom sheet |
| compact | --color-surface-overlay | --color-text-primary | hairline --color-border | --radius-md | short sheet |
| expanded | --color-surface-overlay | --color-text-primary | hairline --color-border-strong | --radius-none | full viewport height |

Sizes: height from --space-* tokens capped by viewport, handle target >= --touch-target-min, close target >= --touch-target-min, width 100% minus gutters.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Escape closes and returns focus to trigger, Tab cycles sheet controls.
- Mouse: click close dismisses, handle drag not a mouse gesture, outside tap dismisses where declared.
- Touch: swipe down dismisses with button alternative, targets >= --touch-target-min.
- Dismiss: Escape + close + swipe down + outside tap where declared, focus returns to trigger, close announced politely.
- Offline: content cached, actions queued, replayed on reconnect.
- Debounce: close events debounce --duration-fast, open shows skeleton overlay.

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

Silent by default. Open -> none; close -> --sound-click; error -> --sound-error. Haptics: --haptic-medium on close. No sound on hover.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | bottom sheet full width minus --space-safe-bottom | width 100% minus gutters |
| tablet (--bp-sm..--bp-lg) | bottom sheet width clamp via --space-* tokens | fluid minmax tokens |
| desktop (>= --bp-lg) | centered sheet, max width --measure-reading | same scale, no layout shift |

Fluid rules: no fixed px; height from --space-* tokens capped by viewport, width from --space-* tokens, collapse then stack then hide.

## 9. RTL mirror behavior (what flips, what stays)

Handle stays centered, title follows bidi, close mirrors to inline-start in RTL, no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-overlay, --color-scrim, --opacity-scrim, --color-text-primary, --color-text-secondary, --color-border, --color-border-strong, --color-border-focus, --radius-lg, --radius-md, --radius-none, --shadow-lg, --shadow-scrim, --shadow-focus-glow, --space-4.--space-8, --space-safe-top/bottom, --footer-min-height, --text-base/lg, --weight-medium/semibold, --font-ui, --leading-normal, --duration-fast, --duration-skeleton-shimmer, --ease-standard, --ease-decelerate, --cursor-default/pointer/not-allowed/progress, --sound-click/error, --sound-volume, --motion-reduced, --bp-sm, --bp-lg, --touch-target-min, --z-modal.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; pull up via --ease-decelerate; return focus to trigger; label close button; hold 40% expansion.
Do not: hardcode height; use color alone for state; hide the ring; trap focus without escape path; autoplay sound; ship without scrim; let content overflow viewport.
Premium treatment: premium pull-up via --ease-decelerate, crisp ring, calm hover wash on close, zero layout shift on open and close.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- container: role=dialog, aria-modal=true, aria-labelledby title
- title: id referenced by aria-labelledby on container
- close: role=button, aria-label close sheet, --touch-target-min
- scrim: aria-hidden=true behind the sheet
- handle: aria-hidden=true, visual grab bar

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on the focused control inside the sheet, never outline:none.
Contrast: AA 4.5:1 title and body on sheet both themes; close control 3:1; focus ring 3:1; --color-text-primary on --color-surface-overlay verified.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Title, body, close label: externalized, 40% expansion, ellipsis policy, no mid-word break.
- Sheet open and close announcements per locale token.
- Bidi isolate spans; RTL mirrors close position and body alignment.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Prints inline without scrim or ring, title and body grayscale, no interactive states, page breaks avoided inside body.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Panel: full-width block at --radius-lg, --color-skeleton-base
- Title: width 60% bar at --text-lg, --color-skeleton-base
- Handle: bar at --radius-full, --color-skeleton-base
- Close: square --touch-target-min at inline-end, --color-skeleton-base
- Body: width 80% block at --text-base, --color-skeleton-base

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced static gray. aria-busy=true while loading, role=status announcement when content lands, skeleton never read as content.

## 16. Icon usage (Lucide names only)

- x for close at --icon-size-md
- chevron-up for handle affordance, alert-circle for error
- Lucide only, --icon-size-md

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'sheet' component per overlays/sheet.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

