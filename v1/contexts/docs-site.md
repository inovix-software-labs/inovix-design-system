# Documentation site

> Purpose: Help readers find and finish a task through a persistent sidebar tree, searchable article body and prev/next paging.
> Section: contexts/ | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: docs-site. Section: contexts/. Help readers find and finish a task through a persistent sidebar tree, searchable article body and prev/next paging.

## 2. Anatomy (parts, ASCII diagram ok)

```
<body>
  <header> brand | search field | version menu </header>
  <div shell>
    <aside> section tree (expandable groups) </aside>
    <article> title / steps / code block / callouts </article>
    <nav> prev / next </nav>
  </div>
</body>
```

- **sidebar tree**: grouped navigation with expandable sections and active page marker
- **search field**: command-style lookup with recent results
- **article body**: headings, paragraphs, code fences, callouts
- **prev/next nav**: sequential paging at the article foot
- **version menu**: documentation version switcher

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
| selected/checked | N/A: no selection model exists in this surface | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| unselected | N/A: no selection model exists in this surface | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no selection semantics |
| expanded/collapsed | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| open/closed | N/A: not an overlay and never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| current page | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| visited | N/A: links carry no history styling here | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no history semantics |
| invalid + disabled | N/A: no form input exists here | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: no read-only field exists here | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: no required input exists here | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | N/A: content region swaps to a whole-area skeleton instead | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no loading semantics |
| skeleton + hover | N/A: skeleton blocks carry no pointer affordance | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no skeleton semantics |
| offline | N/A: offline is copy plus an icon, not a component state here | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no offline semantics |
| empty | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide inbox, --color-text-tertiary | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=status 'No items' |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-*, --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |
| success | --cursor-default | --color-surface-raised | hairline --color-success | --color-text-primary | Lucide check-*, --color-success | none at --duration-instant | --sound-success token if user enabled | role=status announced once |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for docs-site are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| default | --color-surface-base | --color-text-primary | hairline --color-border | --radius-md | reading surface |
| active page | --color-brand-soft | --color-brand-strong | inset 2 units --color-brand | --radius-sm | current article in the tree |
| expanded group | --color-surface-sunken | --color-text-secondary | none | --radius-sm | open section container |
| callout | --color-info-content background tint | --color-text-secondary | hairline --color-border | --radius-md | note or warning block |

Sidebar width from --sidebar-width-collapsed / --sidebar-width-expanded; article max-width --measure-reading; type --text-sm base; radius --radius-md.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- **Keyboard**: sidebar uses a treeview pattern, ArrowRight expands, ArrowLeft collapses, typing in search moves to results
- **Mouse**: tree rows show hover wash; chevrons rotate --duration-fast on expand
- **Touch**: sidebar becomes a drawer under --bp-md with scrim dismissal
- **Focus**: moving focus to the article sets tabindex=-1 on the heading
- **Search**: results announced politely, Escape clears and returns focus to the field
- **Offline**: article remains readable; search degrades to a client-side index

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| tree row | --cursor-pointer | click | pointer cursor, expandable rows show a chevron affordance |
| search field | --cursor-text | focus | text cursor with visible caret color token |
| prev/next | --cursor-pointer | click | pointer cursor, disabled direction shows --cursor-not-allowed |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default; navigation and content reveal fire no sound token; motion still honors --motion-reduced.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| --bp-sm | sidebar is a drawer, article full width | drawer overlay at --z-overlay |
| --bp-md | sidebar docks, article narrows with padding | flex layout, sidebar sticky |
| --bp-lg | sidebar plus article plus on-this-page rail | three-column grid |

Fluid rules: Fluid rules: article measure caps at --measure-reading; code blocks scroll internally; tree indents with nested padding rather than fixed widths.

## 9. RTL mirror behavior (what flips, what stays)

Horizontal layout mirrors: navigation moves to the end side, directional icons flip, progress and scroll affordances follow reading direction; centered media stays centered.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-base, --color-surface-sunken, --color-surface-raised, --color-border, --color-border-strong, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-text-disabled, --color-brand-soft, --color-brand-strong, --color-info, --color-info-content, --radius-md, --radius-sm, --text-sm, --text-xs, --font-mono, --leading-relaxed, --duration-fast, --ease-standard, --z-overlay, --space-safe-left.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: Reference tokens for every fill, border, radius, duration and spacing value; keep one accent family per surface.
Do not: Do not hardcode color, size, radius, duration, shadow or font values; do not use emoji or raster art.
Premium treatment: Restraint first: navy ramp neutrals, hairline borders, one brand accent, calm motion only on meaningful state change.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- Landmark regions named (header, main, footer)
- Headings in document order
- Buttons carry visible-text names

Focus: Every interactive element shows the --color-border-focus ring with --shadow-focus-glow at --duration-instant; focus is never suppressed.
Contrast: Text and icon pairs meet AA (>=4.5:1 body, >=3:1 large text and icons) on --color-surface-base, --color-surface-raised and --color-brand fills, in both themes.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- All labels, headings and CTAs externalized to locale files
- Locale number and date formats via format tokens

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Prints grayscale on white: hide decorative panels and hero visuals, keep headline, body, pricing and legal rows, expand all FAQ answers.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Sidebar tree of twelve narrow bars with indent guides
- Article title bar, six text bars, one code-block rectangle
- Prev/next pill pair
- Callout rectangle with left accent bar

All skeleton shapes use --color-skeleton-base with a --color-skeleton-shine sweep at --duration-skeleton-shimmer; the sweep is off under --motion-reduced, and every skeleton region carries aria-busy=true until content replaces it.

## 16. Icon usage (Lucide names only)

- chevron-right for collapsed groups
- chevron-down for expanded groups
- search for the lookup field
- book-open for the docs brand mark

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'docs-site' component per contexts/docs-site.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```
