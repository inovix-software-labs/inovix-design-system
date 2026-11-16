# Decision Log

> Purpose: Decision log: dated, reversible records of design-system choices, who made them, why, and how to revisit.
> Section: docs | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: decision-log. Section: docs. Decision log: dated, reversible records of design-system choices, who made them, why, and how to revisit.

## 2. Anatomy (parts, ASCII diagram ok)

```
entry = date | id | decision | context | alternatives | status
        + how to revisit (token, file, owner)
newest first; one entry per decision; never edited, only superseded
```

- **Entry**: one decision, one line of context, the alternatives rejected, and a status
- **Status**: accepted | superseded-by-<id> | rejected (with reason)
- **Owner**: the role that can revisit it (design system owner, not a person)
- **Enforcement**: a decision with no entry is a decision that did not happen


Entries (newest first):

```
2026-11-14 | DS-001 | Navy #03182D + white only, no second palette | brand owner spec, single pair keeps AA trivial | multi-accent palette rejected: brand says one pair | accepted | owner: design system owner | revisit: theming/theme-variables.md
2026-11-14 | DS-002 | Text-only logo, 3 lines INOVIX / SOFTWARE LABS / tagline, DejaVu Sans | no raster art in the system, text scales in RTL | image logo rejected: breaks print + forced colors | accepted | owner: design system owner | revisit: brand/logo-source-spec.md
2026-11-14 | DS-003 | Clear-space / min-size / dark-bg / print rules provisional | brand approval pending, ship anyway to unblock consumers | waiting for approval rejected: blocks every component | provisional | owner: design system owner | revisit: brand/logo-source-spec.md
2026-11-14 | DS-004 | Rule 26 splits GENERATOR vs CONSUMER mode | AI must not read REQUIREMENTS.MD when consuming | single-mode rejected: generator rules leak into output | accepted | owner: design system owner | revisit: REQUIREMENTS.MD rule 26
2026-11-14 | DS-005 | 17-section skeleton, fixed order, all 26 states | one shape per component makes AI regeneration deterministic | free-form files rejected: drift across 290 files | accepted | owner: design system owner | revisit: docs/naming.md
```

## 3. FULL state matrix (MANDATORY): default, hover, hovered-click, pressed/active, clicked, focus-visible, focus, disabled, disabled + hover, disabled + pressed, selected/checked, unselected, expanded/collapsed, open/closed, active menu item, current page, visited, invalid + disabled, readonly, required + filled, loading + disabled, skeleton + hover, offline, empty, error, success. Every state: cursor style, background, border, text color, icon, animation, sound (if any), aria state.

| State | Cursor | Background | Border | Text color | Icon | Animation | Sound | ARIA |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| default | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-current/aria-pressed/aria-expanded per state, role set |
| hover | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | background --duration-fast on --ease-standard | silent | aria-current/aria-pressed/aria-expanded per state, role set |
| hovered-click | --cursor-pointer | --color-surface-sunken or --opacity-hover overlay | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | press scale token over the hover wash, --duration-fast | silent | aria-current/aria-pressed/aria-expanded per state, role set |
| pressed/active | --cursor-pointer | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part | transform press scale token, --duration-fast | silent | aria-expanded=true on expanded entry |
| clicked | --cursor-pointer | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part | none at --duration-instant | silent | aria-current/aria-pressed/aria-expanded per state |
| focus-visible | --cursor-default | --color-surface-raised | 2 units --color-border-focus + --shadow-focus-glow | --color-text-primary | Lucide per part | ring --duration-instant | silent | aria-current/aria-pressed/aria-expanded per state |
| focus | --cursor-default | --color-surface-raised | hairline --color-border (no ring; ring is focus-visible only) | --color-text-primary | Lucide per part | none at --duration-instant | silent | aria-current/aria-pressed/aria-expanded per state |
| disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part | none at --duration-instant | silent | aria-disabled=true |
| disabled + hover | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part | none at --duration-instant | silent | aria-disabled=true |
| disabled + pressed | --cursor-not-allowed | --color-surface-sunken | hairline --color-border | --color-text-disabled | Lucide per part | none at --duration-instant | silent | aria-disabled=true |
| selected/checked | --cursor-default | --color-brand-soft | hairline --color-border-strong | --color-text-primary | Lucide per part | none at --duration-instant | silent | aria-selected=true |
| unselected | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part | none at --duration-instant | silent | aria-selected=false |
| expanded/collapsed | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part | none at --duration-instant | silent | aria-expanded per state |
| open/closed | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part | none at --duration-instant | silent | aria-expanded per state |
| active menu item | --cursor-pointer | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part | none at --duration-instant | silent | aria-current=true |
| current page | --cursor-default | --color-brand-soft | hairline --color-border | --color-text-primary | Lucide per part | none at --duration-instant | silent | aria-current=page |
| visited | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-secondary | Lucide per part | none at --duration-instant | silent | aria-current/aria-pressed/aria-expanded per state |
| invalid + disabled | --cursor-not-allowed | --color-surface-sunken | hairline --color-error | --color-text-disabled | Lucide per part | none at --duration-instant | silent | aria-current/aria-pressed/aria-expanded per state |
| readonly | --cursor-default | --color-surface-sunken | hairline --color-border | --color-text-primary | Lucide per part | none at --duration-instant | silent | aria-readonly=true |
| required + filled | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part | none at --duration-instant | silent | aria-required=true |
| loading + disabled | --cursor-progress | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part | spinner --duration-normal linear | silent | aria-busy=true |
| skeleton + hover | --cursor-default | --color-skeleton-base + --color-skeleton-shine sweep | hairline --color-border | --color-text-primary | Lucide per part | shimmer --duration-skeleton-shimmer, off under --motion-reduced | silent | aria-busy=true |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent | aria-busy=false |
| empty | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide inbox, --color-text-tertiary | none at --duration-instant | silent | role=status 'No decisions' |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-* , --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |
| success | --cursor-default | --color-surface-raised | hairline --color-success | --color-text-primary | Lucide check-* , --color-success | none at --duration-instant | --sound-success token if user enabled | role=status announced once |

Every row names its tokens; no raw value appears anywhere. States not applicable to this component are marked N/A with a one-line reason, never dropped silently.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| entry | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-sm | one decision, one row block |
| entry-superseded | --color-surface-sunken | --color-text-secondary | hairline --color-border | --radius-sm | status superseded-by-<id> |
| entry-rejected | --color-surface-sunken | --color-text-disabled | hairline --color-border | --radius-sm | status rejected, reason kept |
| group-heading | --color-surface-base | --color-text-primary | none | --radius-sm | per-month or per-area group |

Sizes: sm / md / lg all from --space-* + --text-* tokens; hit area never below --touch-target-min at any size; sm never below --text-xs; lg never above --text-xl without --measure-reading cap.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- Keyboard: entries are plain text rows, fully readable without a mouse; no interactive widget required.
- Append-only: an entry is never edited after acceptance; a change is a new entry that supersedes by id.
- Order: newest first; a superseded entry keeps its original date and gains status superseded-by-<id>.
- Search: entries are grep-able by id, token name, or file path; no JS needed to read the log.
- Dismiss: rejected entries stay, with reason; deleting a rejected entry is forbidden.
- No debounce, no drag, no long-press, no right-click menu: a log is read, not operated.

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event |
| --- | --- | --- |
| default | --cursor-default | none |
| disabled | --cursor-not-allowed | pointer-events none |
| focus-visible | --cursor-default | ring only |
| loading | --cursor-progress | busy, still interactive where safe |
| drag source | --cursor-grab | pickup at --duration-instant |
| drag over | --cursor-grabbing | drop target highlight --color-brand-soft |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent. A decision log makes no sound and sends no haptic signal on any event; reading it is offline and local.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| mobile (< --bp-sm) | one column: date + id, then decision text | width 100% minus --space-4 gutters |
| tablet (--bp-sm..--bp-lg) | date + id inline, alternatives on next line | fluid minmax tokens |
| desktop (>= --bp-lg) | full row: date, id, decision, context, alternatives, status | max --measure-reading for text |

Fluid rules: no fixed px; all widths from --space-* / --measure-* / --bp-* tokens; text wraps, never truncates without ellipsis policy; horizontal scroll only inside scroll-region; collapse then stack then hide, in that order.

## 9. RTL mirror behavior (what flips, what stays)

Text direction flips per locale; the entry structure (date, id, decision, status) stays in reading order; ids and token names never translate and never mirror.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-base, --color-surface-raised, --color-surface-sunken, --color-text-primary, --color-text-secondary, --color-text-disabled, --color-error, --color-success, --color-warning, --color-border, --color-border-strong, --color-border-focus, --radius-sm, --space-1..--space-8, --text-sm/base/lg, --weight-regular/semibold, --font-ui, --font-mono, --leading-normal, --duration-instant, --touch-target-min, --cursor-default/not-allowed, --bp-sm/md/lg, --measure-reading, --shadow-focus-glow, --color-border-focus, --opacity-hover, --color-brand-soft, --color-skeleton-base, --color-skeleton-shine, --motion-reduced, --sound-error, --sound-success, --cursor-pointer/progress.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

## 11. Do / Do not list

Do: reference tokens by name; ship all 26 states or mark N/A with reason; render skeleton for every shape; use Lucide line art at token size/stroke; keep keyboard full flow; announce state to screen readers; honor reduced motion; hold 40% text expansion; print grayscale.
Do not: hardcode a value; use emoji or raster art; trap focus; hide focus ring; use color alone for meaning; autoplay sound; fetch data inside the component; edit this file for white-label; add JS without a state that needs it; ship without a skeleton.
Premium treatment: this document stays token-only and teaches no bypass of the navy ramp, tinted neutrals, single accent or AA contrast rules (rule 28).

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Role and accessible name on the root; state via aria-pressed/aria-expanded/aria-selected/aria-current as applicable; errors via role=alert inline + linked by aria-describedby; live region for async change, polite by default, assertive for error only. Focus: :focus-visible ring --shadow-focus-glow + 2 units of --color-border-focus width, never :focus-only, never outline:none without replacement. Contrast: AA 4.5:1 body, 3:1 large text and UI, verified on light + dark token pairs; high-contrast theme strengthens borders and removes opacity text; forced-colors maps to system colors. Reduced motion: --duration-instant, no shimmer, no spring, content always visible. Touch target --touch-target-min. Safe area: respect --space-safe-top/right/bottom/left, no content under notches. Keyboard-only full flow with no mouse dependency; no keyboard trap; Escape always works where dismissible.
- decision row: role=listitem, each entry one dated decision with its owner token
- revisit note: role=note, aria-label names the revisit trigger for the decision
- status cell: role=cell, aria-label states reversible or final for the entry

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Externalize every decision string (title, owner note) to locale files; zero literals in code.
- Decision rows hold 40% expansion from en without clipping the date column; no fixed heights on rows.
- Bidi: isolate spans on mixed-direction rationale; RTL mirrors the log per section 9; CLDR plurals on entry counts.

## 14. Print behavior

Grayscale readable: no color-only meaning, every status pairs icon + text. Backgrounds dropped except essential fills; no ink waste. Headers/footers repeat on page break; keep-together on label + value. Mono variant where listed; borders at --color-border-strong in print. Charts/graphs/maps print as labeled list or pattern-filled outline, never raster. No shadow, no blur, no animation. Print styles come from tokens, same no-hardcode rule.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes: root block 100% width at component height token, radius --radius-sm; label bar width 40% at --text-sm with --leading-normal; value bar width 70%; action bar width 20% height --space-10; icon block --icon-size-md square. Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced (static gray). No pulse on text. aria-busy=true while loading, role=status announcement when content lands, skeleton never read as content. Offline/error: skeleton replaced by state panel per section 3, not by blank.
- Decision row: width 85% bar at --text-sm height, --leading-normal, fill --color-skeleton-base
- Date chip: width 14% bar at --text-xs height, --font-mono, fill --color-skeleton-base
- Status dot: width 10% bar at --text-xs height, radius --radius-full, fill --color-skeleton-shine

## 16. Icon usage (Lucide names only)

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.
- Lucide scale on the decision header at --icon-size-lg, --icon-stroke-regular, --color-text-secondary
- Lucide history on the revisit row at --icon-size-sm, --icon-stroke-thin, --color-text-tertiary

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'decision-log' component per docs/decision-log.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Entry = date | id | decision | context | alternatives | status; newest first.
3. Append-only: supersede by id, never edit or delete; rejected entries keep reason.
4. All 26 states from section 3 or N/A with reason; AA on light + dark.
5. Lucide icons only; no emoji; no hardcoded color/size/duration; print grayscale.
Return: component code + state matrix evidence + token usage list.
```
