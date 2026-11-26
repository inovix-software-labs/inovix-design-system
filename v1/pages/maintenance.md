# Maintenance

> Purpose: Scheduled maintenance page: wrench illustration, downtime window, back later action, status link, subscribe note.
> Section: pages | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: maintenance. Section: pages. Scheduled maintenance page: wrench illustration, downtime window, back later action, status link, subscribe note.

## 2. Anatomy (parts, ASCII diagram ok)

```
+----------------------------------+
|        [wrench glyph]            |
|       down for work              |
|   back after the window          |
|   [back]  view status            |
|   [ notify me................]   |
+----------------------------------+
```

- **illustration**: Lucide wrench or hammer glyph, --icon-size-xl, --color-text-tertiary
- **code**: short code --text-2xl --weight-bold --color-text-primary, mono digits
- **window**: downtime window --text-sm --color-text-secondary, calendar token policy
- **actions**: back button primary, status link secondary, --touch-target-min
- **subscribe**: notify me field --radius-field, --color-surface-raised, Lucide bell

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
| selected/checked | N/A: maintenance carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| unselected | N/A: maintenance carries no selection, it renders supplied data only | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| expanded/collapsed | N/A: maintenance has no disclosure subtree, nothing to expand | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: maintenance is not an overlay, it never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | N/A: maintenance is not a menu, it has no item activation | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | --cursor-default | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=page |
| visited | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-secondary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | history visited, no style-only meaning |
| invalid + disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-error | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-invalid=true + aria-disabled=true |
| readonly | --cursor-default | --color-surface-sunken | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-readonly=true |
| required + filled | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-required=true, value present |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | N/A: maintenance renders fixed content, an empty data set cannot occur | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no data semantics |
| error | N/A: maintenance fetches nothing, no error state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no error semantics |
| success | N/A: maintenance completes no async work, no success state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no success semantics |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for maintenance are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-base | --color-text-primary | hairline --color-border | --radius-md | rest |
| window-live | --color-surface-base | --color-text-primary | hairline --color-border | --radius-md | downtime running |
| subscribed | --color-surface-base | --color-text-primary | hairline --color-border | --radius-md | notify on |
| error | --color-surface-base | --color-error | hairline --color-error | --radius-md | subscribe failed |

Sizes: code --text-2xl; illustration --icon-size-xl; window --text-sm; actions >= --touch-target-min; subscribe field >= --touch-target-min; gap --space-2.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab reaches actions then subscribe; Enter activates; B goes back; Escape clears subscribe; focus ring on all; S subscribes.
- Mouse: hover actions lift --shadow-sm; click back reloads; click status opens; click subscribe toggles; right-click native menu.
- Touch: actions and subscribe >= --touch-target-min; tap subscribe toggles; swipe not used; long-press copies code.
- Dismiss: Escape clears subscribe and closes status; outside tap closes status; back action always reachable.
- Offline: cached page renders, subscribe queued, status link disabled with note, replay on reconnect.
- Debounce: subscribe debounces --duration-debounce-input; async window load shows skeleton bar; status link debounces --duration-fast.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over page |
| hover | --cursor-pointer | lift --shadow-sm | over actions |
| pressed/active | --cursor-pointer | --opacity-pressed fill | during action |
| disabled | --cursor-not-allowed | pointer-events none | when subscribe offline |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus |
| loading | --cursor-progress | skeleton bar --duration-skeleton-shimmer | window pending |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Back -> --sound-click, subscribe done -> --sound-upload-complete, failure -> --sound-error. Haptics: --haptic-light on back. No sound on hover or code copy.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | code center, actions stack, subscribe full width | stack, gap --space-1 |
| tablet (--bp-sm..--bp-lg) | code center, actions inline, subscribe inline | inline row |
| desktop (>= --bp-lg) | code center, actions inline, subscribe max --measure-reading | same scale |

Fluid rules: no fixed px; code size from --text-*; illustration scales with --icon-size-sm/md/lg/xl; window clamps one line; actions wrap then stack; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Code digits stay LTR numeric; illustration centered; window aligns logical inline-start; actions logical order; status link mirrors in RTL; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-base, --color-surface-raised, --color-brand, --color-brand-soft, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-error, --color-border, --color-border-strong, --color-border-focus, --color-skeleton-base, --color-skeleton-shine, --opacity-hover, --opacity-pressed, --radius-md, --radius-field, --shadow-sm, --shadow-focus-glow, --space-1, --space-2, --text-xs/sm/base/2xl, --weight-bold, --font-ui, --font-mono, --leading-normal, --duration-fast, --duration-debounce-input, --duration-skeleton-shimmer, --ease-standard, --icon-size-xl, --touch-target-min, --cursor-pointer, --cursor-not-allowed, --cursor-progress, --sound-click, --sound-upload-complete, --sound-error, --motion-reduced, --bp-sm, --bp-lg, --measure-reading.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; code paired with window text; actions labeled; subscribe paired with bell icon; hold 40% expansion; window honest from token.
Do not: hardcode code size; use color alone for error state; hide the ring; subscribe without label; ship without skeleton bar; let window overflow; fixed illustration.
Premium treatment: premium treatment: illustration draw-in --motion-enter, code shimmer --duration-skeleton-shimmer once, action glow --shadow-colored-brand, zero shift on subscribe.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- code: role=text, aria-label maintenance code
- illustration: role=img, aria-label wrench illustration, aria-hidden when decorative
- window: role=text, aria-label downtime window
- actions: role=button and role=link, aria-label back and status
- subscribe: role=textbox, aria-label notify me, aria-describedby window

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on actions and subscribe, never outline:none.
Contrast: AA 4:5:1 window, code, action labels, subscribe placeholder both themes; error --color-error on --color-surface-base verified; focus ring 3:1.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Code, window text, action labels, subscribe placeholder: externalized, 40% expansion, ellipsis policy.
- Code digits per locale number format; window date per locale token.
- Bidi isolate spans; RTL mirrors action order, code digits stay LTR, status link logical end.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: page prints framed, illustration prints outlined, code prints mono, actions print text labels, no shimmer.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Code: width 40% bar at --text-2xl, --color-skeleton-base
- Illustration: square --icon-size-xl centered, --color-skeleton-base
- Subscribe: width 70% bar at field height, --color-skeleton-base

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced. aria-busy=true while window loads, role=status when window lands, skeleton never read as content. Failure replaces skeleton with --color-error note.

## 16. Icon usage (Lucide names only)

- Lucide wrench for illustration, bell for subscribe, rotate-cw for back, activity for status
- Lucide only, --icon-size-xl

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'maintenance' component per pages/maintenance.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

