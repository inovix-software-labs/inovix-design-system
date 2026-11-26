# Back Forward History

> Purpose: Keep navigation predictable across in-app state, browser history and a visible history trail that distinguishes visited from current.
> Section: micro/ | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: back-forward-history. Section: micro/. Keep navigation predictable across in-app state, browser history and a visible history trail that distinguishes visited from current.

## 2. Anatomy (parts, ASCII diagram ok)

```
<chrome>  [<] [>] [history panel]
             |        |
             v        v
   in-app state stack    list of visited views with current marker
             | fail/session edge
             v
   safe fallback route
```

- **back and forward**: controls mirroring browser semantics inside the app shell
- **history panel**: recent views with timestamps and current marker
- **state restoration**: scroll position, filters and draft text preserved
- **edge handling**: expired sessions and dead ends route somewhere useful

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
| expanded/collapsed | N/A: no disclosure subtree exists here | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-expanded absent |
| open/closed | N/A: not an overlay and never opens or closes | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no open state |
| active menu item | N/A: no navigation list lives in this surface | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no menu semantics |
| current page | N/A: no current-page marker applies here | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no navigation semantics |
| visited | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role set, name from visible label |
| invalid + disabled | N/A: no form input exists here | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no validity semantics |
| readonly | N/A: no read-only field exists here | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no edit semantics |
| required + filled | N/A: no required input exists here | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no input semantics |
| loading + disabled | N/A: content region swaps to a whole-area skeleton instead | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no loading semantics |
| skeleton + hover | N/A: skeleton blocks carry no pointer affordance | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide per part, --icon-size-md / --icon-stroke-thin | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | no skeleton semantics |
| offline | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide cloud-off, --color-warning | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | aria-busy=false, offline note |
| empty | --cursor-default | --color-surface-raised | hairline --color-border | --color-text-primary | Lucide inbox, --color-text-tertiary | none at --duration-instant | silent (sound events only via --sound-* tokens, user opt-in) | role=status 'No items' |
| error | --cursor-default | --color-surface-raised | hairline --color-error | --color-error | Lucide alert-*, --color-error | none at --duration-instant | --sound-error token if user enabled | role=alert announced once |
| success | --cursor-default | --color-surface-raised | hairline --color-success | --color-text-primary | Lucide check-*, --color-success | none at --duration-instant | --sound-success token if user enabled | role=status announced once |

Every row names its tokens; no raw value appears anywhere. Inapplicable rows for back-forward-history are marked N/A with the reason specific to this component, never dropped silently and never one blanket sentence.

## 4. Variants + sizes (spec table)

| Variant | Fill | Text | Border | Radius | When |
| --- | --- | --- | --- | --- | --- |
| enabled | --color-surface-raised | --color-text-primary | hairline --color-border | --radius-md | navigation available |
| empty | --color-surface-sunken | --color-text-disabled | none | --radius-md | no history in this session |
| current entry | --color-brand-soft | --color-brand-strong | inset 2 units --color-brand | --radius-md | active history row |
| visited entry | --color-surface-base | --color-text-secondary | hairline --color-border | --radius-md | previously viewed row |

Controls --space-8 square; panel width --sidebar-width-expanded capped; type --text-xs to --text-sm; radius --radius-md.

## 5. Behavior + interaction rules (keyboard, mouse, touch, dismiss, debounce, drag, long-press, right-click)

- **Keyboard**: Alt+ArrowLeft/Right for history on desktop, panel items reachable by Tab
- **Mouse**: hover previews the destination label in a tooltip
- **Touch**: swipe-edge gestures map to back where the platform allows
- **State**: returning restores scroll, filters and any unsaved draft
- **Edge cases**: expired sessions return to a signed-in landing state, never a blank screen
- **History hygiene**: sensitive query terms stay out of the persisted trail

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event | When |
| --- | --- | --- | --- |
| back | --cursor-pointer | click | pointer cursor when enabled, --cursor-not-allowed when empty |
| forward | --cursor-pointer | click | pointer cursor when enabled, --cursor-not-allowed when empty |
| history entry | --cursor-pointer | click | pointer cursor, whole row navigates |

## 7. Sound + haptic behavior per event (or explicit silent decision)

Silent by default; state changes announce through aria-live text rather than audio.

## 8. Responsive Behavior table (mobile/tablet/desktop, what changes, fluid rules)

| Breakpoint | What changes | Rule |
| --- | --- | --- |
| --bp-sm | history becomes a full-screen sheet with large rows | sheet pattern |
| --bp-md | panel docks as a dropdown from the toolbar | popover placement |
| --bp-lg | persistent rail optional beside content | aside placement |

Fluid rules: Fluid rules: entry titles truncate with tooltips; the panel caps height and scrolls internally instead of pushing the page.

## 9. RTL mirror behavior (what flips, what stays)

Directional affordances mirror to the end side; reading order of content never changes; numeric and stack order stay left-to-right only where the data demands it.

## 10. Token usage (which tokens, NO hardcoded values rule)

Tokens used: --color-surface-base, --color-surface-raised, --color-surface-sunken, --color-border, --color-border-strong, --color-text-primary, --color-text-secondary, --color-text-tertiary, --color-text-disabled, --color-brand, --color-brand-soft, --color-brand-strong, --radius-md, --space-8, --text-xs, --text-sm, --duration-fast, --ease-standard, --sidebar-width-expanded, --shadow-lg, --z-popover, --icon-size-md.

Hard rule: zero hardcoded color, size, radius, duration, easing, shadow, opacity, z-index, or font value. White-label rebrand swaps theme-variables.md only; this file is never edited for a customer.

Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden.

## 11. Do / Do not list

Do: Keep triggers discoverable, feedback immediate, and reversal always available for destructive steps.
Do not: Do not fire destructive changes on hover, do not rely on color-only state, do not hardcode motion or color values.
Premium treatment: One calm motion language: quick confirms, slow reveals, nothing decorative competes with the task.

## 12. Accessibility requirements (role, aria, focus, contrast, screen reader, reduced motion, high contrast, forced colors)

Per-part aria mapping:
- Trigger buttons named from the action they perform
- Transient feedback announced via role=status or alert

Focus: The active control shows the --color-border-focus ring with --shadow-focus-glow at --duration-instant; focus returns to the triggering element after any dismissal.
Contrast: Labels, icons and state markers meet AA against their surface in both themes; state is never conveyed by color alone.

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Short action labels externalized and expansion-tested
- Locale formats for counts, dates and durations

All strings externalized to locale files; zero literals in code. Layouts hold 40% expansion from en without truncation, overlap, or fixed heights. Bidi: Unicode algorithm, isolate spans, no concatenated mixed-direction strings. Scripts: Latin/Cyrillic/Greek first with CJK/Devanagari/Arabic fallback stacks from --font-ui; per-script line-height via --leading-* tokens, never fixed px. Plurals: CLDR categories with count token, never hardcoded suffix. Formats: date, time, number, currency, calendar, first-day-of-week, timezone all per locale token; store UTC, label always shown. RTL: full mirror per section 9. Truncation: ellipsis token policy only, never mid-word, tooltip on truncated. Hyphenation: off unless token enables per locale. Line breaking: CJK/Thai rules, no overflow hidden on text.

## 14. Print behavior

Interaction chrome (toolbars, toasts, drag handles) prints hidden; resulting content prints in its final state.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes:
- Toolbar pair of small buttons
- Panel rows with title bar and time dot
- Current-entry highlight slot

Feedback skeletons use --color-skeleton-base with a --color-skeleton-shine sweep at --duration-skeleton-shimmer, off under --motion-reduced; transient toasts carry role=status so screen readers hear completion.

## 16. Icon usage (Lucide names only)

- chevron-left and chevron-right for navigation
- history for the panel
- clock for timestamps

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'back-forward-history' component per micro/back-forward-history.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
7. Premium essentials: navy ramp tokens, tinted neutrals, single navy-family accent, restraint, AA minimum contrast, calm motion, light and dark parity.
Return: component code + state matrix evidence + token usage list.
```
