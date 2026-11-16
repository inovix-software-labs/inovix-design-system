# Input

> Purpose: Single-line text capture with label, hint, error, clear action, character count, validation states and full keyboard contract.
> Section: forms | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: input. Section: forms. Single-line text capture with label, hint, error, clear action, character count, validation states and full keyboard contract.

## 2. Anatomy (parts, ASCII diagram ok)

```
+---------------------------------------------------+
| Label (required marker)                           |
| +-----------------------------------------------+ |
| | control                          | clear/reveal | |
| +-----------------------------------------------+ |
| hint  /  error  /  character count               |
+---------------------------------------------------+
```

- **label**: for/id link, --text-sm --weight-medium, required marker token
- **control**: the input box, fill/border/text/radius/height from tokens
- **hint**: --text-xs --color-text-secondary, never error-colored at rest
- **error**: role=alert inline, icon + text, --color-error, aria-describedby
- **action**: optional clear or reveal, --touch-target-min, never the only path

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hovered-click | --cursor-pointer | --color-surface-sunken + --opacity-pressed overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| pressed/active | N/A: input has no press phase, it commits on click | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no hover fill |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no press |
| selected/checked | N/A: input carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| unselected | N/A: input carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| expanded/collapsed | N/A: input has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: input is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | N/A: input is not a menu, it has no item activation | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | N/A: input does not navigate, no current-page concept | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no navigation semantics |
| visited | N/A: input is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-error | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-invalid=true + aria-disabled=true |
| readonly | --cursor-default | --color-surface-sunken | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-readonly=true |
| required + filled | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-required=true, value present |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | N/A: input renders fixed content, an empty data set cannot occur | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no data semantics |
| error | N/A: input fetches nothing, no error state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no error semantics |
| success | N/A: input completes no async work, no success state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no success semantics |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for input are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| text | plain single line | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-field | default capture |
| password | masked with reveal action | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-field | secret capture |
| search | with search icon + clear | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-field | filtering entry |
| invalid | error styling | --color-surface-raised | --color-error | hairline --color-error | --radius-field | validation failed |
| readonly | non-editable | --color-surface-sunken | --color-text-primary | hairline --color-border | --radius-field | display-only value |

Sizes: sm / md / lg heights from --space-* + --text-* tokens; hit area never below --touch-target-min; sm never below --text-xs; lg never above --text-xl; width fluid via clamp, never fixed px.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab enters, Shift+Tab leaves; arrows move caret in text; Escape clears only when a clear action exists; Enter submits the parent form, never the field alone; autofill and paste are native.
- Mouse: hover shows no fill change, only border-strong; focus-visible ring; select-all via double-click native; drag selection native.
- Touch: target >= --touch-target-min; long-press selects natively; swipe not used; keyboard type inferred from inputmode token policy (numeric, email, url).
- Dismiss: clear action resets to empty and announces; no overlay behavior.
- Offline: entry queued locally, replayed on reconnect, validation re-run.
- Debounce: input-driven filtering debounces --duration-debounce-input; async validation pending state announced via aria-busy.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-text | caret blink at --duration-normal | inside the control |
| hover | --cursor-text | border-strong only | over the control |
| pressed/active | --cursor-text | selection highlight --color-selection | while selecting |
| disabled | --cursor-not-allowed | pointer-events none | when disabled |
| focus-visible | --cursor-text | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus |
| loading | --cursor-progress | spinner --duration-normal linear | async validation in flight |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Validation error -> --sound-error token if user enabled; successful commit -> --sound-success; clear action -> --sound-click. Haptics: --haptic-light on clear, --haptic-heavy on error. No sound on typing, hover, or focus.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | label above control, full width, hint below | width 100% minus --space-4 gutters |
| tablet (--bp-sm..--bp-lg) | label above, two-column field grid where listed | fluid minmax tokens |
| desktop (>= --bp-lg) | inline label + control, max --measure-reading | same grid, no fixed widths |

Fluid rules: no fixed px; all widths from --space-* / --measure-* / --bp-* tokens; text wraps, never truncates without ellipsis policy; horizontal scroll only inside scroll-region; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Label and control keep DOM order; text-align start; caret and selection follow bidi algorithm; error icon sits inline-end; clear/reveal action mirrors to inline-start; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-raised, --color-surface-sunken, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-text-disabled, --color-error, --color-success, --color-border, --color-border-strong, --color-border-focus, --color-selection, --color-selection-text, --color-skeleton-base, --color-skeleton-shine, --opacity-hover, --opacity-pressed, --opacity-disabled, --radius-field, --shadow-sm, --shadow-focus-glow, --space-1.--space-4, --text-xs/sm/base, --weight-medium, --font-ui, --leading-normal, --duration-fast, --duration-normal, --duration-debounce-input, --ease-standard, --cursor-text, --cursor-not-allowed, --cursor-progress, --sound-error, --sound-success, --sound-click, --sound-volume, --motion-reduced, --bp-sm, --bp-lg, --measure-reading, --space-safe-bottom, --touch-target-min.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens by name; ship all 26 states; pair every error with icon + text + aria-describedby; hold 40% expansion; keep hint calm at rest; announce async validation via aria-busy.
Do not: hardcode a height or border color; use placeholder as the only label; trap focus; hide the ring; autoplay sound on typing; ship without a skeleton; let error text wrap mid-word.
Premium treatment: calm raised fill at rest, refined hover as hairline strengthening never a fill jump, tactile focus ring with --shadow-focus-glow, graceful disabled at --opacity-disabled, loading that matches final layout with zero shift.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- label: for/id link, accessible name, aria-required when required
- control: role=textbox or native input, aria-invalid on error, aria-describedby hint + error
- hint: aria-hidden=false, referenced by describedby
- error: role=alert, announced once
- clear: role=button, aria-label clear, --touch-target-min

Focus: :focus-visible ring --shadow-focus-glow + 2 units of --color-border-focus width, never outline:none without replacement; ring sits outside the border, inside overflow visible.
Contrast: AA 4.5:1 label and hint both themes; error text --color-error on --color-surface-raised verified in the contrast table; disabled text exempt but above 4.5:1 on sunken; focus indicator 3:1 minimum.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Label, hint, error: externalized strings, 40% expansion, ellipsis token policy, no mid-word break.
- Placeholder: externalized, never the only name, never longer than the control width at --text-sm.
- Number/date/currency input: locale format tokens, store raw UTC/ISO, label per locale.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: borders print at --color-border-strong, error prints with the word error, no ring, no shadow, no shimmer; value prints in --font-mono where numeric.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Label: width 30% bar at --text-sm, --color-skeleton-base
- Control: full-width block at component height token, radius --radius-field, --color-skeleton-base
- Hint: width 60% bar at --text-xs, --color-skeleton-base
- Action: square --touch-target-min at inline-end, --color-skeleton-base

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced (static gray). No pulse on text. aria-busy=true while loading, role=status announcement when content lands. Offline/error: skeleton replaced by state panel per section 3.

## 16. Icon usage (Lucide names only)

- leading: search, mail, user, lock, calendar per inputmode
- trailing: x for clear, eye / eye-off for reveal, alert-circle for error, check-circle for valid

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'input' component per forms/input.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

