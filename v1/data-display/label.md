# Label

> Purpose: Static text label: caption, key, or metadata line, token-bound type scale, never interactive by itself.
> Section: data-display | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: label. Section: data-display. Static text label: caption, key, or metadata line, token-bound type scale, never interactive by itself.

## 2. Anatomy (parts, ASCII diagram ok)

```
+---------------------------------+
| (icon) Label text    value mono |
+---------------------------------+
```

- **text**: --text-xs / --text-sm per level, --color-text-secondary or --color-text-tertiary
- **leading icon**: optional Lucide, --icon-size-sm, aria-hidden
- **value**: optional value span, --font-mono tabular

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | N/A: label is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| hover | N/A: label is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| hovered-click | N/A: label is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| pressed/active | N/A: label is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| clicked | N/A: label is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| focus-visible | N/A: label is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| focus | N/A: label is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| disabled | N/A: label is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| disabled + hover | N/A: label is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| disabled + pressed | N/A: label is non-interactive presentation, no pointer states | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=img or presentation, name from content |
| selected/checked | N/A: label carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| unselected | N/A: label carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| expanded/collapsed | N/A: label has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: label is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | N/A: label is not a menu, it has no item activation | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | N/A: label does not navigate, no current-page concept | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no navigation semantics |
| visited | N/A: label is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: label holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: label is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: label takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | N/A: label renders only supplied content, it never fetches | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no loading semantics |
| skeleton + hover | N/A: label is never data-driven, no skeleton phase exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no skeleton semantics |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | N/A: label renders fixed content, an empty data set cannot occur | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no data semantics |
| error | N/A: label fetches nothing, no error state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no error semantics |
| success | N/A: label completes no async work, no success state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no success semantics |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for label are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-raised | --color-text-secondary | none | --radius-none | rest |
| muted | --color-surface-raised | --color-text-tertiary | none | --radius-none | low emphasis |
| strong | --color-surface-raised | --color-text-primary | none | --radius-none | emphasis |
| code | --color-surface-sunken | --color-text-primary | hairline --color-border | --radius-sm | value is code |

Sizes: text --text-xs / --text-sm / --text-base per level; icon --icon-size-sm; gap --space-1; padding --space-1; width fluid.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: not focusable; when wrapped in a link or button, the wrapper owns focus and the ring.
- Mouse: hover none; click passes to wrapper; no drag; right-click native menu; text selection native.
- Touch: no target of its own; wrapper target >= --touch-target-min; long-press selects text natively.
- Dismiss: not applicable.
- Offline: cached text renders, no queue.
- Debounce: none; static text never debounces.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over text |
| hover | --cursor-default | none | no hover state |
| pressed/active | N/A: label is not pressable, it displays text | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent | no press semantics |
| disabled | --cursor-default | --color-surface-raised | none | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent | aria-hidden when decorative |
| focus-visible | --cursor-default | ring lands on wrapper when wrapped | keyboard focus on wrapper |
| loading | N/A: label is static, no loading phase exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent | no loading semantics |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent always. Label is a display element; no sound in any state. Haptics none. Sound policy belongs to micro-interactions/sound.md.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | text wraps, value below label | stack, gap --space-1 |
| tablet (--bp-sm..--bp-lg) | text + value inline | inline |
| desktop (>= --bp-lg) | text + value inline, max --measure-reading | same scale |

Fluid rules: no fixed px; type from --text-* tokens; text wraps, never truncates without ellipsis; collapse then stack then hide.

## 9. RTL mirror behavior (what flips, what stays)

Text follows bidi algorithm; icon stays inline-start; value mirrors to inline-end in RTL; selection follows direction; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-raised, --color-surface-sunken, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-text-disabled, --color-border, --color-border-strong, --radius-none, --radius-sm, --space-1.--space-3, --text-xs/sm/base, --weight-medium, --font-ui, --font-mono, --leading-normal, --duration-instant, --cursor-default, --motion-reduced.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; ship all 26 states with honest N/A rows; keep type scale token-bound; pair icon with text; hold 40% expansion.
Do not: hardcode a type size; use color alone; make label a button without wrapper; hide the ring on wrapper; autoplay sound; ship a label that truncates mid-word.
Premium treatment: calm static text, refined hover none by design, tactile press inherited from wrapper, crisp ring on wrapper only, graceful disabled at --color-text-disabled, no loading phase by design.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- label: role=text or span, name from text, aria-hidden when decorative
- icon: aria-hidden=true, decorative
- value: role=text, aria-label when code value
- wrapper: role=link or button when wrapped, owns focus and ring

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus lands on the wrapper when wrapped, never on the text itself; never outline:none.
Contrast: AA 4:5:1 text both themes; muted --color-text-tertiary on raised verified 17.00:1 light; code value AA on sunken; focus 3:1 on wrapper.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Text: externalized, 40% expansion, ellipsis policy, no mid-word break.
- Value per locale number format; code value stays LTR.
- Bidi isolate spans; RTL mirrors value position.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: text prints as-is, value prints --font-mono, no ring, no shimmer, no fill waste.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Text: width 60% bar at --text-xs height, --color-skeleton-base
- Value: width 30% bar at --text-xs, --color-skeleton-base
- Icon: square --icon-size-sm at inline-start, --color-skeleton-base

Fill --color-skeleton-base, shimmer --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced. aria-busy=true while loading, role=status when content lands. Offline/error: skeleton replaced by state panel per section 3.

## 16. Icon usage (Lucide names only)

- info for metadata, tag for category, hash for code value, none required when plain
- Lucide only, --icon-size-sm

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'label' component per data-display/label.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

