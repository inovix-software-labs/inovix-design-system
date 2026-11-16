# Contribution

> Purpose: Contribution: how to add a component, template use, review bar, no direct app edits, decision-log entry for changes.
> Section: docs | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: contribution. Section: docs. Contribution: how to add a component, template use, review bar, no direct app edits, decision-log entry for changes.

## 2. Anatomy (parts, ASCII diagram ok)

```
section/file.md  ->  H1 name
  > purpose line
  > Section: x | Theme: ... | Skeleton: mandatory
  1..17 sections in order
```

- **Rule**: the convention being documented: naming, structure, versioning, contribution
- **Scope**: which files and folders it governs
- **Example**: one canonical example, ASCII-safe
- **Enforcement**: how the AI/dev knows it was followed: file name, header line, token list

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| hovered-click | --cursor-pointer | --color-surface-sunken + --opacity-pressed overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| pressed/active | --cursor-pointer | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | transform press scale token, --duration-fast | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant, debounce --duration-debounce-input | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | ring --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| selected/checked | --cursor-default | --color-brand-soft | hairline --color-border-strong | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=true |
| unselected | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-checked/aria-selected=false |
| expanded/collapsed | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded per state |
| open/closed | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded per state |
| active menu item | --cursor-pointer | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=true |
| current page | --cursor-default | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current=page |
| visited | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-secondary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| invalid + disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-error | --color-text-disabled | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| readonly | --cursor-default | --color-surface-sunken | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-readonly=true |
| required + filled | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-required=true, value present |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | spinner --duration-normal linear, aria-busy=true | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide inbox, --color-text-tertiary | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=status 'No items' |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-* , --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |
| success | --cursor-default | --color-surface-raised | hairline --color-success | --color-text-primary | Lucide check-* , --color-success | none at --duration-instant | --sound-success token if user enabled | role=status announced once |

Every row names its tokens; no raw value appears anywhere. States not applicable to this component are marked N/A with a one-line reason, never dropped silently.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| readme | system level | n/a | n/a | n/a |
| policy | one policy per file | n/a | n/a | n/a |
| reference | name/version/structure | n/a | n/a | n/a |

Sizes: sm / md / lg all from --space-* + --text-* tokens; hit area never below --touch-target-min at any size; sm never below --text-xs; lg never above --text-xl without --measure-reading cap.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Read order: README -> file-structure -> naming -> the component MD you need; decisions live in changelog + decision-log.
- Change flow: edit the MD, run the audit, update changelog, bump version per versioning.md; never edit app code first.
- No stubs: every section 1-17 present in every component file; N/A requires a reason; no copy-paste filler between files.
- Naming: kebab-case everywhere; no abbreviations; section names fixed; wildcard rules in file-structure.md.
- Evidence: claims carry token names, not opinions; contrast claims carry the pair; skeleton claims carry the shape list.
- Two modes: GENERATOR only on explicit owner request; CONSUMER ignores REQUIREMENTS.MD completely.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event |
| --- | --- | --- |
| default | --cursor-default | none |
| hover | --cursor-pointer | background change only, no layout shift |
| pressed/active | --cursor-pointer | scale + --opacity-pressed |
| disabled | --cursor-not-allowed | pointer-events none |
| loading | --cursor-progress | busy, still interactive where safe |
| drag source | --cursor-grab | pickup at --duration-instant |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent. Documentation has no UI. No sound tokens apply.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | stack parts, full-width targets | width 100% minus --space-4 gutters |
| tablet (--bp-sm..--bp-lg) | two-column where listed | fluid minmax tokens |
| desktop (>= --bp-lg) | full anatomy | max --measure-reading for text |

Fluid rules: no fixed px; all widths from --space-* / --measure-* / --bp-* tokens; text wraps, never truncates without ellipsis policy; horizontal scroll only inside scroll-region; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Docs note: RTL rules live in i18n/rtl.md; naming and structure unchanged by direction.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-base, --color-surface-raised, --color-surface-sunken, --color-surface-overlay, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-text-disabled, --color-primary, --color-primary-content, --color-secondary, --color-accent, --color-success, --color-warning, --color-error, --color-info, --color-border, --color-border-strong, --color-border-focus, --color-brand, --color-brand-soft, --color-scrim, --color-skeleton-base, --color-skeleton-shine, --opacity-hover, --opacity-pressed, --opacity-scrim, --opacity-selected, --opacity-disabled, --radius-sm, --radius-md, --radius-lg, --shadow-sm, --shadow-md, --shadow-focus-glow, --space-1..--space-8, --text-xs/sm/base/lg/xl, --weight-regular/semibold/extrabold, --font-ui, --font-mono, --leading-tight/normal/relaxed, --tracking-tight, --duration-instant/fast/normal/slow, --ease-standard/decelerate/accelerate/spring, --icon-size-sm/md/lg/xl, --icon-stroke-thin/regular/thick, --touch-target-min, --cursor-pointer/default/not-allowed, --sound-success/error/notification/click/toggle, --sound-volume, --motion-reduced, --bp-sm/md/lg, --measure-reading, --space-safe-top/right/bottom/left, --font-mono, --text-sm, --space-4.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

## 11. Do / Do not list

Do: reference tokens by name; ship all 26 states or mark N/A with reason; render skeleton for every shape; use Lucide line art at token size/stroke; keep keyboard full flow; announce state to screen readers; honor reduced motion; hold 40% text expansion; print grayscale.
Do not: hardcode a value; use emoji or raster art; trap focus; hide focus ring; use color alone for meaning; autoplay sound; fetch data inside the component; edit this file for white-label; add JS without a state that needs it; ship without a skeleton.
Premium treatment: this document stays token-only and teaches no bypass of the navy ramp, tinted neutrals, single accent or AA contrast rules (rule 28).

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Role and accessible name on the root; state via aria-pressed/aria-expanded/aria-selected/aria-current as applicable; errors via role=alert inline + linked by aria-describedby; live region for async change, polite by default, assertive for error only. Focus: :focus-visible ring --shadow-focus-glow + 2 units of --color-border-focus width, never :focus-only, never outline:none without replacement. Contrast: AA 4.5:1 body, 3:1 large text and UI, verified on light + dark token pairs; high-contrast theme strengthens borders and removes opacity text; forced-colors maps to system colors. Reduced motion: --duration-instant, no shimmer, no spring, content always visible. Touch target --touch-target-min. Safe area: respect --space-safe-top/right/bottom/left, no content under notches. Keyboard-only full flow with no mouse dependency; no keyboard trap; Escape always works where dismissible.
- how-to block: role=region, aria-label names the contribution flow in this doc
- review bar: role=list, each bar item one role=listitem with its check token
- template note: role=note, aria-label names the component template to copy

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Externalize every contribution string (step label, review note) to locale files; zero literals in code.
- Step rows hold 40% expansion from en inside the flow column; no fixed heights on step bars.
- Bidi: isolate spans on mixed-direction examples; RTL mirrors the steps per section 9; CLDR plurals on item counts.

## 14. Print behavior

Grayscale readable: no color-only meaning, every status pairs icon + text. Backgrounds dropped except essential fills; no ink waste. Headers/footers repeat on page break; keep-together on label + value. Mono variant where listed; borders at --color-border-strong in print. Charts/graphs/maps print as labeled list or pattern-filled outline, never raster. No shadow, no blur, no animation. Print styles come from tokens, same no-hardcode rule.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes: root block 100% width at component height token, radius --radius-sm; label bar width 40% at --text-sm with --leading-normal; value bar width 70%; action bar width 20% height --space-10; icon block --icon-size-md square. Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced (static gray). No pulse on text. aria-busy=true while loading, role=status announcement when content lands, skeleton never read as content. Offline/error: skeleton replaced by state panel per section 3, not by blank.
- Step row: width 75% bar at --text-sm height, --leading-normal, fill --color-skeleton-base
- Bar item: width 50% bar at --text-xs height, radius --radius-sm, fill --color-skeleton-base
- Log chip: width 28% bar at --text-xs height, --font-mono, fill --color-skeleton-shine

## 16. Icon usage (Lucide names only)

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.
- Lucide git-pull-request on the contribution header at --icon-size-lg, --icon-stroke-regular, --color-text-secondary
- Lucide clipboard-check on the review bar row at --icon-size-md, --icon-stroke-thin, --color-text-tertiary

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'contribution' component per docs/contribution.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
Return: component code + state matrix evidence + token usage list.
```
