# Theme Toggle

> Purpose: Theme toggle: single control flips light + dark token sets at once, persists choice, respects OS first, AA on both.
> Section: theming | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: theme-toggle. Section: theming. Theme toggle: single control flips light + dark token sets at once, persists choice, respects OS first, AA on both.

## 2. Anatomy (parts, ASCII diagram ok)

```
[sun icon] [moon icon]   one visible per theme
        |
   aria-pressed=true/false
        |
  flip ALL --color-* tokens at once (never partial)
        |
  persist choice (user pref, then OS)
```

- **Trigger**: icon button or switch in header, right of language switcher, 44x44 min hit area
- **Icons**: Lucide sun + moon, one visible per theme, aria-hidden decorative
- **Label**: aria-label "Toggle dark mode", announced via role=switch or aria-pressed
- **Scope**: flips every theme token in one pass; component files never edited

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide sun or moon, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=switch or aria-pressed |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide sun or moon, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent | role=switch or aria-pressed |
| pressed/active | --cursor-pointer | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide sun or moon | transform press scale token, --duration-fast | silent | aria-pressed flips mid-press |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | icon swaps sun<->moon at --duration-instant | theme fade --duration-fast | --sound-toggle token if user enabled | aria-pressed updated before fade |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide sun or moon | ring --duration-instant | silent | aria-pressed true/false |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide sun or moon, --color-text-disabled | none at --duration-instant | silent | aria-disabled=true |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | spinner --duration-normal linear | spinner --duration-normal linear | silent | aria-busy=true |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-* , --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |

States N/A for this component, with reason: hovered-click (no distinct pressed-hover step on a single trigger), selected/checked (a toggle is binary pressed, not selectable), unselected (same), expanded/collapsed (no expandable parts), open/closed (no panel), active menu item (not in a menu), current page (not navigation), visited (no history), invalid + disabled (no value to invalidate), readonly (user always allowed to flip), required + filled (no form value), skeleton + hover (no data shape to skeleton), offline (works offline, no fetch), empty (no content slot), success (no success surface of its own), focus (indistinguishable from focus-visible on a single trigger), disabled + hover (disabled suppresses hover feedback), disabled + pressed (disabled suppresses press feedback).

Every row names its tokens; no raw value appears anywhere. States not applicable to this component are marked N/A with a one-line reason, never dropped silently.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| icon-button | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-md | default header slot |
| icon-button-active | --color-brand-soft | --color-text-primary | hairline --color-border-strong | --radius-md | pressed state feedback |
| switch | track --color-surface-sunken, thumb --color-surface-raised | --color-text-primary | hairline --color-border | --radius-pill | settings page, labeled |
| menu-item | --color-surface-raised | --color-text-primary | none | --radius-sm | inside command palette or menu |

Sizes: sm / md / lg all from --space-* + --text-* tokens; hit area never below --touch-target-min at any size; sm never below --text-xs; lg never above --text-xl without --measure-reading cap.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Enter or Space flips theme; focus-visible ring per section 12; no keyboard path into token internals.
- Click: single click flips light + dark in one pass; never partial swap; debounce --duration-debounce-input against double-flips.
- Persist: choice stored by the app shell under a token-named key; on load, stored choice wins over OS preference; OS preference wins when no stored choice.
- OS first: first visit reads OS color-scheme; OS change mid-session does NOT override a stored user choice.
- Fade: theme change uses --duration-fast fade on surfaces; off under --motion-reduced; no flash of wrong theme (FOIT window <= --duration-fast).
- Touch: tap target --touch-target-min; no long-press menu; no drag; no right-click menu on the toggle.
- Sound: --sound-toggle token if user enabled, at --sound-volume; silent when sound off or reduced-motion + mute set.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | root idle |
| hover | --cursor-pointer | background --color-surface-sunken or --opacity-hover overlay | on every interactive part |
| pressed/active | --cursor-pointer | scale press token + --opacity-pressed | on the triggered part |
| disabled | --cursor-not-allowed | pointer-events none | on disabled parts |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus |
| loading + disabled | --cursor-progress | spinner --duration-normal linear | async in flight |
| checked | --cursor-default | --color-brand-soft fill | --color-brand-soft, --color-border-strong |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Theme toggle -> --sound-toggle if enabled, at --sound-volume, user opt-in. Haptic equivalent on touch: one light tick at flip, none on hover, none on persist. No sound for token swap internals, white-label load, or skin preview.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | icon-button variant only, 44x44 hit area | width from --space-* tokens |
| tablet (--bp-sm..--bp-lg) | switch variant in settings, icon-button in header | fluid minmax tokens |
| desktop (>= --bp-lg) | all variants available | max --measure-reading for text |

Fluid rules: no fixed px; all widths from --space-* / --measure-* / --bp-* tokens; text wraps, never truncates without ellipsis policy; horizontal scroll only inside scroll-region; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

No flip: theme is direction-agnostic; token swap identical in RTL; toggle position follows layout mirror (header right becomes header left in RTL); icon glyphs never mirror.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-base, --color-surface-raised, --color-surface-sunken, --color-surface-overlay, --color-text-primary, --color-text-secondary, --color-text-disabled, --color-brand, --color-brand-soft, --color-border, --color-border-strong, --color-border-focus, --radius-sm, --radius-md, --radius-pill, --shadow-sm, --shadow-focus-glow, --space-1..--space-8, --text-sm, --weight-regular, --font-ui, --duration-instant/fast, --duration-debounce-input, --ease-standard, --icon-size-md, --icon-stroke-thin, --touch-target-min, --cursor-pointer/default/not-allowed/progress, --sound-toggle, --sound-volume, --motion-reduced, --bp-sm/md/lg, --opacity-hover, --opacity-pressed.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

## 11. Do / Do not list

Do: reference tokens by name; ship all 26 states from section 3 or mark N/A with reason; render skeleton for every sub-shape; use Lucide line art at token size/stroke; keep keyboard full flow; announce state to screen readers; honor reduced motion; hold 40% text expansion; print grayscale.
Do not: hardcode a value; use emoji or raster art; trap focus; hide focus ring; use color alone for meaning; autoplay sound; fetch data inside the component; edit this file for white-label; add JS without a state that needs it; ship without a skeleton.
Premium treatment: both themes keep identical restraint, one accent, calm motion and AAA body with AA minimum for large text, so neither theme reads as a louder or cheaper version (rule 28a, rule 28h).

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- Trigger: role=button or native button, accessible name
- Icons: role + accessible name, state via aria-*
- Label: role + accessible name, state via aria-*
- Scope: role + accessible name, state via aria-*

Focus: :focus-visible ring --shadow-focus-glow + 2 units of --color-border-focus width, never :focus-only, never outline:none without replacement. Contrast: AA 4.5:1 body, 3:1 large text and UI, verified on light + dark token pairs; high-contrast theme strengthens borders and removes opacity text; forced-colors maps to system colors. Reduced motion: --duration-instant, no shimmer, no spring, content always visible. Touch target --touch-target-min. Safe area: respect --space-safe-top/right/bottom/left, no content under notches. Keyboard-only full flow with no mouse dependency; no keyboard trap; Escape always works where dismissible.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Label: externalized string, 40% expansion from en, ellipsis token policy, no mid-word break
- Toggle i18n: label externalized; aria-label per locale; no literal in control
- Toggle expansion: label grows; --touch-target-min held; no clip on expand

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: no color-only meaning, every status pairs icon + text. Backgrounds dropped except essential fills; no ink waste. Headers/footers repeat on page break; keep-together on label + value. Mono variant where listed; borders at --color-border-strong in print. Charts/graphs/maps print as labeled list or pattern-filled outline, never raster. No shadow, no blur, no animation. Print styles come from tokens, same no-hardcode rule.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Trigger: block at component height token, radius --radius-sm, --color-skeleton-base
- Icons: --icon-size-md square, --color-skeleton-base
- Label: width 40% bar at --text-sm --leading-normal, --color-skeleton-base
- Scope: block at component height token, radius --radius-sm, --color-skeleton-base

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced (static gray). No pulse on text. aria-busy=true while loading, role=status announcement when content lands, skeleton never read as content. Offline/error: skeleton replaced by state panel per section 3, not by blank.

## 16. Icon usage (Lucide names only)

- Icons: Lucide per part, --icon-size-md / --icon-stroke-thin
- Lucide sun-moon for toggle mark, --icon-size-sm, --color-text-secondary

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'theme-toggle' component per theming/theme-toggle.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. One control flips ALL color tokens at once; never partial swap.
3. Persist choice; OS color-scheme only when no stored choice; AA on both themes.
4. Lucide sun + moon, one visible per theme; aria-pressed or role=switch.
5. Keyboard Enter + Space flip; focus-visible ring; Escape never needed.
6. Fade at --duration-fast, off under prefers-reduced-motion; silent by default.
Return: component code + state matrix evidence + token usage list.
```
