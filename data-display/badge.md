# Badge

> Purpose: Compact count or status marker, pill-shaped, always paired with icon or text, never color alone.
> Section: data-display | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: badge. Section: data-display. Compact count or status marker, pill-shaped, always paired with icon or text, never color alone.

## 2. Anatomy (parts, ASCII diagram ok)

```
+--( dot  text )--+
   pill, radius full
```

- **pill**: --radius-full fill per variant
- **text**: --text-xs --weight-medium, plural-safe count
- **dot**: optional Lucide dot, --icon-size-sm

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | N/A: badge is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| hover | N/A: badge is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| hovered-click | N/A: badge is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| pressed/active | N/A: badge is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| clicked | N/A: badge is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| focus-visible | N/A: badge is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| focus | N/A: badge is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| disabled | N/A: badge is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| disabled + hover | N/A: badge is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| disabled + pressed | N/A: badge is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| selected/checked | N/A: badge carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| unselected | N/A: badge carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| expanded/collapsed | N/A: badge has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: badge is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | N/A: badge is not a menu, it has no item activation | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | N/A: badge does not navigate, no current-page concept | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no navigation semantics |
| visited | N/A: badge is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: badge holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: badge is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: badge takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide inbox, --color-text-tertiary | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=status 'No items' |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-*, --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |
| success | --cursor-default | --color-surface-raised | hairline --color-success | --color-text-primary | Lucide check-*, --color-success | none at --duration-instant | --sound-success token if user enabled | role=status announced once |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for badge are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-sunken | --color-text-secondary | hairline --color-border | --radius-full | neutral |
| success | --color-success | --color-success-content | transparent | --radius-full | positive |
| warning | --color-warning | --color-warning-content | transparent | --radius-full | caution |
| error | --color-error | --color-error-content | transparent | --radius-full | failure |
| info | --color-info | --color-info-content | transparent | --radius-full | informational |

Sizes: sm / md / lg from --space-* + --text-xs tokens; count badge min --touch-target-min only when interactive; hit area never below --touch-target-min when clickable.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: not focusable when static; when interactive, Tab enters, Enter activates, focus ring on pill.
- Mouse: hover strengthens fill; click only when interactive; no drag; right-click native menu.
- Touch: interactive badge target >= --touch-target-min; long-press not used; swipe not used.
- Dismiss: dismissable badge takes x action, Escape closes, focus returns.
- Offline: cached value renders, queue updates, replay on reconnect.
- Debounce: count updates debounce --duration-debounce-input; pulse once per new value.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | static badge |
| hover | --cursor-default | fill strengthen --opacity-hover | over static |
| pressed/active | N/A: badge is not pressable, it displays a value | --color-surface-sunken | hairline --color-border | --color-text-secondary | Lucide per part, --icon-size-sm | none at --duration-instant | silent | no press semantics |
| disabled | --cursor-not-allowed | --color-surface-sunken at --opacity-disabled | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-sm | none at --duration-instant | silent | aria-disabled=true |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus on interactive badge |
| loading | --cursor-progress | skeleton pill --color-skeleton-base | async count |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent always. Badge is a display element; no hover, press or count sound. Haptics none. Sound policy belongs to micro-interactions/sound.md.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | text only, dot hidden, count compact | stack inline |
| tablet (--bp-sm..--bp-lg) | dot + text | inline |
| desktop (>= --bp-lg) | dot + text + optional label | inline |

Fluid rules: no fixed px; padding from --space-*; text wraps never truncates without ellipsis; collapse then stack then hide.

## 9. RTL mirror behavior (what flips, what stays)

Pill content order follows bidi; dot stays inline-start of text; count stays LTR numeric; dismiss x mirrors to inline-end; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-sunken, --color-surface-raised, --color-brand-soft, --color-text-primary, --color-text-secondary, --color-text-disabled, --color-success, --color-success-content, --color-warning, --color-warning-content, --color-error, --color-error-content, --color-info, --color-info-content, --color-border, --color-border-strong, --color-border-focus, --color-skeleton-base, --opacity-hover, --opacity-disabled, --radius-full, --shadow-focus-glow, --space-1.--space-3, --text-xs, --weight-medium, --font-ui, --leading-tight, --duration-fast, --ease-standard, --icon-size-sm, --icon-stroke-thin, --touch-target-min, --cursor-default, --cursor-not-allowed, --sound-volume, --motion-reduced, --bp-sm, --bp-lg.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; ship all 26 states; pair every color with icon or text; hold 40% expansion; announce count changes via aria-live.
Do not: hardcode pill size; use color alone; hide the ring on interactive badges; autoplay sound; ship without skeleton; let count overflow the pill.
Premium treatment: calm pill at rest, refined hover as fill strengthen never a color jump, crisp ring on interactive, graceful disabled at --opacity-disabled, loading pill matching final width.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- badge: role=status or img, name from text, aria-live=polite for counts
- dot: aria-hidden=true when decorative
- dismiss: role=button, aria-label dismiss, --touch-target-min

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on interactive badges only, never outline:none.
Contrast: AA 4:5:1 text on every semantic fill both themes (verified in theme-variables.md contrast table); dot pairs with text; focus 3:1.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Text and label: externalized, 40% expansion, ellipsis policy, no mid-word break.
- Count plural-safe per CLDR category, locale number format.
- Bidi isolate spans; RTL mirrors dismiss x.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: fill drops to outline, text prints, dot prints as the word status in context, no shimmer, no ring.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Pill: width 30% bar at --text-xs height, radius --radius-full, --color-skeleton-base
- Dot: square --icon-size-sm at inline-start, --color-skeleton-base

Fill --color-skeleton-base, shimmer --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced. aria-busy=true while loading, role=status when content lands. Offline/error: skeleton replaced by state panel per section 3.

## 16. Icon usage (Lucide names only)

- dot: circle, check-circle-2 for success, alert-triangle for warning, x-circle for error, info for info
- x for dismiss, Lucide only, --icon-size-sm

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'badge' component per data-display/badge.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

