# Recorder

> Purpose: Capture surface with record pause stop, level meter, elapsed time, waveform preview, save discard.
> Section: media | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: recorder. Section: media. Capture surface with record pause stop, level meter, elapsed time, waveform preview, save discard.

## 2. Anatomy (parts, ASCII diagram ok)

```
+------------------+
|  o o o o o o o   |
|  o==[====]----o  |
|  00:04:12        |
|  ( ) [<] [[]]    |
|  [save] [discard]|
+------------------+
```

- **meter**: level bars --color-brand fill, peak marker --color-warning, height per token
- **timer**: elapsed time --text-base --font-mono --color-text-primary, tabular
- **waveform**: captured waveform --color-brand-soft fill, --radius-sm
- **controls**: Lucide record pause stop save discard, --touch-target-min
- **state**: capture state chip, --color-surface-sunken, --text-xs

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
| selected/checked | N/A: recorder carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| unselected | N/A: recorder carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| expanded/collapsed | N/A: recorder has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: recorder is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | N/A: recorder is not a menu, it has no item activation | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | N/A: recorder does not navigate, no current-page concept | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no navigation semantics |
| visited | N/A: recorder is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: recorder holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: recorder is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: recorder takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide inbox, --color-text-tertiary | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=status 'No items' |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-*, --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |
| success | --cursor-default | --color-surface-raised | hairline --color-success | --color-text-primary | Lucide check-*, --color-success | none at --duration-instant | --sound-success token if user enabled | role=status announced once |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for recorder are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-md | rest |
| recording | --color-surface-raised | --color-text-primary | hairline --color-error | --radius-md | capture live |
| paused | --color-surface-raised | --color-text-primary | hairline --color-warning | --radius-md | capture held |
| saved | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-md | waveform kept |

Sizes: meter bars height per token; timer --text-base; waveform height --space-10; controls >= --touch-target-min; chip --text-xs.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: R record pause; S stop; Enter save; Backspace discard; arrows scrub waveform; Escape cancels discard; Tab reaches controls.
- Mouse: hover control highlights --color-brand-soft; click control acts; drag waveform scrubs; right-click native menu.
- Touch: controls >= --touch-target-min; tap waveform scrubs; long-press discards; swipe not used.
- Dismiss: Escape cancels discard then clears state; outside tap closes menu; timer keeps on dismiss.
- Offline: capture stored local, save queued, replay on reconnect, queued badge --color-warning, failure offers retry.
- Debounce: level meter updates throttle --duration-fast; scrub debounces --duration-debounce-input; async save shows button skeleton.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over surface |
| hover | --cursor-pointer | control wash --color-brand-soft | over controls |
| pressed/active | --cursor-pointer | --opacity-pressed fill | during scrub |
| disabled | --cursor-not-allowed | pointer-events none | when capture locked |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus |
| loading | --cursor-progress | waveform skeleton --duration-skeleton-shimmer | save pending |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Record -> --sound-toggle, stop -> --sound-upload-complete, failure -> --sound-error. Haptics: --haptic-medium on record, --haptic-selection on stop. No sound on hover or scrub.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | controls stack, meter full width, timer center, waveform full width | stack, gap --space-1 |
| tablet (--bp-sm..--bp-lg) | controls inline, meter inline, timer inline-end | inline row |
| desktop (>= --bp-lg) | full row, waveform below, chip inline-start | same scale |

Fluid rules: no fixed px; meter bar height from token; timer tabular mono; waveform clamps; controls wrap then stack; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Meter bars flow logical start; timer stays LTR numeric; waveform scrub mirrors in RTL for forward; controls logical order; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-raised, --color-surface-sunken, --color-brand, --color-brand-soft, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-warning, --color-error, --color-border, --color-border-strong, --color-border-focus, --color-skeleton-base, --color-skeleton-shine, --opacity-hover, --opacity-pressed, --radius-md, --radius-sm, --shadow-sm, --shadow-focus-glow, --space-1, --space-10, --text-xs/sm/base, --font-ui, --font-mono, --leading-normal, --duration-fast, --duration-debounce-input, --duration-skeleton-shimmer, --ease-standard, --icon-size-sm, --icon-size-md, --touch-target-min, --cursor-pointer, --cursor-not-allowed, --cursor-progress, --sound-toggle, --sound-upload-complete, --sound-error, --motion-reduced, --bp-sm, --bp-lg.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; level meter paired with numeric level; timer paired with state chip; waveform alt from capture policy; hold 40% expansion; record state announced.
Do not: hardcode meter height; use color alone for state chip; hide the ring; record without consent note; ship without waveform skeleton; let timer overflow; fixed control set.
Premium treatment: premium treatment: meter bars stagger --stagger-step, record glow --shadow-colored-brand, waveform rise --motion-enter, zero shift on state change.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- meter: role=meter, aria-label capture level, aria-valuenow
- timer: role=timer, aria-label elapsed time, aria-live=off
- waveform: role=img, aria-label captured waveform preview
- controls: role=button, aria-label record pause stop save discard
- state: role=status, aria-label capture state

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on controls and waveform, never outline:none.
Contrast: AA 4:5:1 timer, chip text both themes; meter --color-brand on --color-surface-raised verified 3:1 non-text; state chip --color-error 4.5:1; focus ring 3:1.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Control labels, chip text, error copy: externalized, 40% expansion, ellipsis policy.
- Timer format per locale token; state plural-safe per locale.
- Bidi isolate spans; RTL keeps timer LTR numeric, controls logical, meter flows logical start.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: surface prints framed, meter prints as hatched bars with level text, waveform prints outlined, no shimmer.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Meter: width 70% bar at meter height, --color-skeleton-base
- Timer: width 30% bar at --text-base, --color-skeleton-base
- Waveform: width 80% bar at --space-10, --color-skeleton-base

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced. aria-busy=true while saving, role=status when save lands, skeleton never read as content. Failure replaces skeleton with retry action.

## 16. Icon usage (Lucide names only)

- Lucide mic for record, pause, square for stop, save, trash-2 for discard
- Lucide only, --icon-size-sm

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'recorder' component per media/recorder.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

