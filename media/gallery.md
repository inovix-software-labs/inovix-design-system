# Gallery

> Purpose: Grid of media slots with select mode, hover preview, bulk actions, lazy reveal per slot.
> Section: media | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: gallery. Section: media. Grid of media slots with select mode, hover preview, bulk actions, lazy reveal per slot.

## 2. Anatomy (parts, ASCII diagram ok)

```
+----------------------------------+
| [o] [o] [o] [o]                  |
| [o] [o] [o] [o]                  |
| [o] [o] [o] [o]                  |
+----------------------------------+
| toolbar: select all  share  more |
```

- **grid**: slot columns from --grid-columns, gap --space-2
- **slot**: aspect box per slot token, --radius-md, --color-skeleton-base until decode
- **check**: Lucide check circle top inline-end when selected, --color-brand
- **toolbar**: bulk action bar --color-surface-raised, appears in select mode
- **preview**: hover preview panel --z-popover, larger frame, caption line

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
| selected/checked | --cursor-default | --color-brand-soft | hairline --color-border-strong | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=true |
| unselected | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=false |
| expanded/collapsed | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | chevron rotate --duration-normal on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded per state |
| open/closed | --cursor-default | --color-surface-overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | enter --motion-enter, exit --motion-exit | silent (sound events only via --sound-* tokens, user opt-in) | aria-hidden when closed, role=dialog when open |
| active menu item | --cursor-pointer | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=true |
| current page | --cursor-default | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=page |
| visited | N/A: gallery is not a link, visited history does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: gallery holds no user input, no validity state exists | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: gallery is not editable, readonly does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: gallery takes no input, required + filled does not apply | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide inbox, --color-text-tertiary | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=status 'No items' |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-*, --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |
| success | --cursor-default | --color-surface-raised | hairline --color-success | --color-text-primary | Lucide check-*, --color-success | none at --duration-instant | --sound-success token if user enabled | role=status announced once |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for gallery are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-md | rest |
| selected | --color-brand-soft | --color-text-primary | hairline --color-primary | --radius-md | check shown |
| select-mode | --color-surface-raised | --color-text-primary | hairline --color-brand | --radius-md | bulk toolbar on |
| empty | --color-surface-sunken | --color-text-tertiary | hairline --color-border | --radius-md | no items yet |

Sizes: slot columns from --grid-columns; slot aspect per token; gap --space-2; toolbar buttons >= --touch-target-min; preview panel max --measure-reading.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: Tab moves slot to slot; Space toggles select; Enter opens preview; Escape closes preview and select mode; arrows navigate grid; A selects all.
- Mouse: hover slot shows --opacity-hover wash and preview panel; click selects in select mode; drag selects range; right-click slot menu.
- Touch: slots >= --touch-target-min; long-press enters select mode; swipe scrolls grid; pinch not used.
- Dismiss: Escape closes preview then select mode; outside tap closes preview; toolbar clears on Escape.
- Offline: cached thumbs render, failed slot shows retry action, bulk actions queued, replay on reconnect.
- Debounce: scroll reveal debounces --duration-fast; preview open debounces --duration-tooltip-delay; async decode shows slot skeleton.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| default | --cursor-default | none | over slot |
| hover | --cursor-pointer | wash --opacity-hover | over slot |
| pressed/active | --cursor-pointer | --opacity-pressed fill | during select |
| disabled | --cursor-not-allowed | pointer-events none | when slot locked |
| focus-visible | --cursor-default | ring --shadow-focus-glow + 2 units --color-border-focus | keyboard focus |
| loading | --cursor-progress | slot skeleton --duration-skeleton-shimmer | decode pending |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default. Select -> --sound-click, bulk action done -> --sound-upload-complete, failure -> --sound-error. Haptics: --haptic-selection on select toggle. No sound on hover or scroll.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | two slot columns, toolbar sticky, preview full width | stack, gap --space-2 |
| tablet (--bp-sm..--bp-lg) | three columns, toolbar inline | grid minmax tokens |
| desktop (>= --bp-lg) | four columns per --grid-columns, preview panel right | same scale, max --measure-reading |

Fluid rules: no fixed px; columns from --grid-columns; slot aspect from token; toolbar wraps then stacks; preview clamps caption; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Grid flows logical start to end; check badge stays inline-end; toolbar actions logical order; preview panel anchors inline-end; no physical left/right.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-raised, --color-surface-sunken, --color-surface-overlay, --color-brand, --color-brand-soft, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-error, --color-border, --color-border-strong, --color-border-focus, --color-skeleton-base, --color-skeleton-shine, --opacity-hover, --opacity-pressed, --radius-md, --shadow-sm, --shadow-focus-glow, --space-1, --space-2, --text-xs/sm/base, --font-ui, --leading-normal, --duration-fast, --duration-tooltip-delay, --duration-skeleton-shimmer, --ease-standard, --icon-size-sm, --touch-target-min, --cursor-pointer, --cursor-not-allowed, --cursor-progress, --sound-click, --sound-upload-complete, --sound-error, --motion-reduced, --bp-sm, --bp-lg, --measure-reading, --z-popover, --grid-columns.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: reference tokens; slot alt from content policy; select mode announced via aria; bulk actions disabled until selection; hold 40% expansion; preview keyboard reachable.
Do not: hardcode slot aspect; use color alone for selected state; hide the ring; lazy load without placeholder; ship without slot skeleton; let toolbar overflow; fixed column count.
Premium treatment: premium treatment: slot reveal staggers with --stagger-step, preview rises --motion-enter, select check pops --ease-bounce, zero shift on decode.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- slot: role=img, alt per policy, aria-selected in select mode
- check: aria-hidden=true, state via aria-selected on slot
- toolbar: role=toolbar, aria-label bulk actions
- preview: role=dialog, aria-label preview, Escape documented
- grid: role=list, aria-label media gallery

Focus: :focus-visible ring --shadow-focus-glow + 2 units --color-border-focus on slot and toolbar buttons, never outline:none.
Contrast: AA 4.5:1 toolbar labels, preview caption both themes; selected fill --color-brand-soft verified; check glyph 3:1 non-text; focus ring 3:1.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Slot alt, toolbar labels, preview caption: externalized, 40% expansion, ellipsis policy, no mid-word break.
- Selection count plural-safe per locale; select all label per locale.
- Bidi isolate spans; RTL mirrors check badge to inline-start, toolbar order logical.

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Grayscale readable: slots print framed, selected prints with check glyph, toolbar prints with text labels, no shimmer, no pop.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Slot: square at slot aspect, --color-skeleton-base
- Check: square --icon-size-sm at inline-end, --color-skeleton-base
- Toolbar: width 60% bar at toolbar height, --color-skeleton-base

Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced. aria-busy=true while decoding, role=status when slot lands, skeleton never read as content. Failure replaces skeleton with retry action.

## 16. Icon usage (Lucide names only)

- Lucide image for slot fallback, check-circle for select, plus for add
- Lucide only, --icon-size-sm

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'gallery' component per media/gallery.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```

