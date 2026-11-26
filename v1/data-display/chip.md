# Chip

> Purpose: Filter or selection chip: removable pill, selected state, clear-all policy, input-adjacent behavior.
> Section: data-display | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: chip. Section: data-display. Filter or selection chip: removable pill, selected state, clear-all policy, input-adjacent behavior.

## 2. Anatomy (parts, ASCII diagram ok)

```
+--( icon label x )--+
   chip, radius full
```

- **chip**: pill with label, --radius-full, selected fill --color-brand-soft
- **remove**: Lucide x action, --touch-target-min
- **leading icon**: optional Lucide, --icon-size-sm

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| hovered-click | --cursor-pointer | --color-surface-sunken + --opacity-pressed overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| pressed/active | N/A: chip has no press phase, it commits on click | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no hover fill |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-disabled=true, no press |
| selected/checked | --cursor-default | --color-brand-soft | hairline --color-border-strong | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=true |
| unselected | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=false |
| expanded/collapsed | N/A: chip has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: chip is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | N/A: chip is not a menu, it has no item activation | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | N/A: chip does not navigate, no current-page concept | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no navigation semantics |
| visited | N/A: chip is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: chip holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: chip is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: chip takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | N/A: chip renders fixed content, an empty data set cannot occur | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no data semantics |
| error | N/A: chip fetches nothing, no error state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no error semantics |
| success | N/A: chip completes no async work, no success state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no success semantics |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for chip are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-sunken | --color-text-secondary | hairline --color-border | --radius-full | rest |
| selected | --color-brand-soft | --color-text-primary | hairline --color-border-strong | --radius-full | chosen |
| removable | --color-surface-sunken | --color-text-secondary | hairline --color-border | --radius-full | with x action |
| invalid | --color-surface-raised | --color-error | hairline --color-error | --radius-full | validation failed |

Sizes: chip height --space-6; text --text-xs; padding --space-2; remove x >= --touch-target-min; group gap --space-2.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab enters chip; Space or Enter toggles; Backspace removes when focused and removable; Escape clears group; arrows move in group where declared.
- Mouse: hover strengthens fill; click toggles; click x removes; drag not used; right-click native menu.
- Touch: chip and x >= --touch-target-min; long-press previews; swipe chip removes where declared; no hover-only path.
- Dismiss: x removes with confirmation only where destructive; Escape clears group; focus stays.
- Offline: state queued, replayed on reconnect, validation re-run.
- Debounce: group change fires once per commit, debounce --duration-debounce-input; async filter pending announced.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-pointer | none | over chip |
| hover | --cursor-pointer | fill strengthen --opacity-hover | over chip |
| pressed/active | --cursor-pointer | --opacity-pressed fill | during toggle |
| disabled | --cursor-not-allowed | pointer-events none | when disabled |
| focus-visible | --cursor-pointer | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus |
| loading | --cursor-progress | skeleton chip --duration-skeleton-shimmer | async filter |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Select -> --sound-toggle, remove -> --sound-click, error -> --sound-error. Haptics: --haptic-light on toggle. No sound on hover.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | chips wrap full width, remove x inside | width 100% minus --space-4 gutters |
| tablet (--bp-sm..--bp-lg) | chips wrap, two-column groups | fluid minmax |
| desktop (>= --bp-lg) | chips inline, clear-all at inline-end | same scale |

Fluid rules: no fixed px; chip height from --space-*; text wraps never truncates without ellipsis; collapse then stack then hide.

## 9. RTL mirror behavior (what flips, what stays)

Chip content follows bidi; remove x mirrors to inline-start in RTL; leading icon stays inline-start; selected fill unchanged; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-raised, --color-surface-sunken, --color-brand-soft, --color-text-primary, --color-text-secondary, --color-text-disabled, --color-error, --color-success, --color-border, --color-border-strong, --color-border-focus, --color-skeleton-base, --color-skeleton-shine, --opacity-hover, --opacity-pressed, --opacity-selected, --opacity-disabled, --radius-full, --shadow-focus-glow, --space-1.--space-3, --text-xs/sm, --weight-medium, --font-ui, --leading-tight, --duration-fast, --duration-normal, --duration-debounce-input, --duration-skeleton-shimmer, --ease-standard, --icon-size-sm, --icon-stroke-thin, --touch-target-min, --cursor-pointer, --cursor-not-allowed, --cursor-progress, --sound-toggle/click/error, --sound-volume, --motion-reduced, --bp-sm/md/lg.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; ship all 26 states; pair selected with check or text; hold 40% expansion; announce group count; confirm destructive removes.
Do not: hardcode chip height; use color alone; hide the ring; autoplay sound; ship without chip skeleton; let chip overflow the group; allow remove without undo where declared.
Premium treatment: calm pill at rest, refined hover as fill strengthen, tactile toggle, crisp ring, graceful disabled, loading chip matching final chip height with zero shift.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- chip: role=button or checkbox, aria-pressed or aria-checked, aria-required where mandatory
- remove: role=button, aria-label remove chip value, --touch-target-min
- group: role=group or listbox, aria-label chip group
- error: role=alert, aria-describedby

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on chip and remove x, never outline:none.
Contrast: AA 4:5:1 chip text both themes; selected --color-brand-soft with --color-text-primary 13.40:1; error AA; focus 3:1.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Chip label, group label, hint, error: externalized, 40% expansion, ellipsis policy, no mid-word break.
- Chip count plural-safe; locale number format inside label.
- Bidi isolate spans; RTL mirrors remove x.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: selected prints outlined with the word selected, error prints with text, no ring, no shimmer.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Chip: width 30% bar at --text-xs height, radius --radius-full, --color-skeleton-base
- Remove x: square --icon-size-sm at inline-end, --color-skeleton-base

Fill --color-skeleton-base, shimmer --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced. aria-busy=true while loading, role=status when content lands. Offline/error: skeleton replaced by state panel per section 3.

## 16. Icon usage (Lucide names only)

- x for remove, check for selected, plus for add, alert-circle for invalid
- Lucide only, --icon-size-sm

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'chip' component per data-display/chip.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

