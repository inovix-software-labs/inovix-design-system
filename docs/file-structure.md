# File Structure

> Purpose: File structure: directory map, one file per component, section order, wildcard rules, what lives where.
> Section: docs | Theme: light + dark, same tokens | Skeleton: mandatory

## 1. Name + one-line purpose

Name: file-structure. Section: docs. File structure: directory map, one file per component, section order, wildcard rules, what lives where.

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
- Two modes: GENERATOR only on explicit owner request; CONSUMER ignores REQUIREMENTS.MD completely. This file carries the full generated tree: 479 MD files across 18 directories, plus generator-only theme-variables.md and REQUIREMENTS.MD. One file per component, names kebab-case, sections 1-17 in order.

Generated tree (479 files, including this doc):
```
design-system/
  REQUIREMENTS.MD
  theme-variables.md
  a11y/
    contrast.md
    focus.md
    forced-colors.md
    grayscale.md
    high-contrast.md
    keyboard.md
    monochrome.md
    pointer.md
    reduced-motion.md
    safe-area.md
    screen-reader.md
    touch-target.md
  ai-prompts/
    a11y-prompt-template.md
    animation-prompt-template.md
    chart-prompt-template.md
    component-prompt-template.md
    cursor-prompt-template.md
    i18n-prompt-template.md
    page-prompt-template.md
    print-prompt-template.md
    skeleton-prompt-template.md
    sound-prompt-template.md
    state-prompt-template.md
    token-prompt-template.md
  brand/
    logo-a11y.md
    logo-clear-space.md
    logo-colors.md
    logo-dark-background.md
    logo-light-background.md
    logo-min-size.md
    logo-print.md
    logo-provisional-flags.md
    logo-responsive.md
    logo-source-spec.md
    logo-states.md
    logo-text-only.md
    logo-typography.md
    logo-usage-rules.md
    logo.md
  contexts/
    activity-timeline.md
    admin-panel.md
    analytics.md
    approval-chain.md
    attachments-uploads.md
    attendance.md
    audit-logs.md
    auth.md
    billing.md
    blog.md
    bulk-actions.md
    call-log.md
    cart.md
    chat.md
    checkout-steps.md
    comments.md
    coupon.md
    deal-stage.md
    docs-site.md
    email-preview.md
    employee-directory.md
    files-manager.md
    forecast-chart.md
    form-builder.md
    import-export.md
    kpi-goals.md
    landing.md
    lead-card.md
    leave-request.md
    marketing.md
    mentions-reactions.md
    messaging.md
    mini-cart.md
    monitoring.md
    notifications-center.md
    onboarding.md
    order-status.md
    org-chart.md
    payment-method-list.md
    payslip.md
    pipeline-kanban.md
    pricing.md
    product-card.md
    product-grid.md
    query-builder.md
    recommendation-rail.md
    reports.md
    review-rating.md
    role-management-rbac.md
    saas-dashboard.md
    search-results.md
    settings-pages.md
    sharing-permissions.md
    shift-roster.md
    stock-badge.md
    table-builder.md
    task-list.md
    team-management.md
    user-management.md
    user-profile.md
    wishlist.md
    workflows.md
  data-display/
    audio.md
    avatar.md
    badge.md
    barcode.md
    calendar.md
    card.md
    chart-area.md
    chart-bar.md
    chart-boxplot.md
    chart-bubble.md
    chart-candlestick.md
    chart-combo.md
    chart-donut.md
    chart-errorbar.md
    chart-funnel.md
    chart-gantt.md
    chart-gauge.md
    chart-grouped.md
    chart-heatmap.md
    chart-histogram.md
    chart-inline-bar.md
    chart-line.md
    chart-percent-stacked.md
    chart-pie.md
    chart-polar.md
    chart-radar.md
    chart-sankey.md
    chart-scatter.md
    chart-sparkline-cell.md
    chart-sparkline.md
    chart-stacked.md
    chart-status-pill.md
    chart-sunburst.md
    chart-treemap.md
    chart-waterfall.md
    chip.md
    file.md
    folder.md
    gantt.md
    graph-dag.md
    graph-flow.md
    graph-hierarchy.md
    graph-mindmap.md
    graph-network.md
    graph-org.md
    graph-timeline.md
    graph-tree.md
    grid.md
    icon.md
    image.md
    invoice.md
    kanban.md
    kpi.md
    label.md
    link.md
    list.md
    map-choropleth.md
    map-circle.md
    map-cluster.md
    map-control.md
    map-geocode.md
    map-heatmap-layer.md
    map-heatmap.md
    map-layer.md
    map-legend.md
    map-marker.md
    map-polygon.md
    map-route.md
    map-tooltip.md
    pill.md
    qr.md
    receipt.md
    report.md
    stat.md
    table.md
    tag.md
    tile.md
    timeline.md
    tree.md
    video.md
  docs/
    README.md
    changelog.md
    contribution.md
    decision-log.md
    file-structure.md
    getting-started.md
    icon-policy.md
    motion-policy.md
    naming.md
    typography-policy.md
    versioning.md
  feedback/
    alert.md
    autosave-indicator.md
    banner.md
    beta-tag.md
    coming-soon.md
    deprecated-tag.md
    dirty-state.md
    empty-state.md
    error-state.md
    error.md
    info.md
    last-updated.md
    loader.md
    loading-state.md
    maintenance-state.md
    message.md
    new-feature-badge.md
    notification.md
    offline-state.md
    progress-bar.md
    progress-circle.md
    rate-limit-message.md
    relative-time.md
    saved-indicator.md
    session-expiry-modal.md
    skeleton.md
    snackbar.md
    spinner.md
    success.md
    sync-status.md
    toast.md
    toaster.md
    unsaved-changes-guard.md
    warning.md
  forms/
    autocomplete.md
    button.md
    checkbox.md
    code-block.md
    colorpicker.md
    combobox.md
    datepicker.md
    drag-drop-zone.md
    field-error.md
    file-upload.md
    form-field.md
    input.md
    markdown.md
    masked-input.md
    multiselect.md
    otp.md
    radio.md
    range.md
    rich-text.md
    segmented-control.md
    select.md
    signature.md
    slider.md
    switch.md
    tag-input.md
    textarea.md
    timepicker.md
    toggle.md
    validation.md
  i18n/
    arabic.md
    bidi.md
    calendar.md
    cjk.md
    currency.md
    cyrillic.md
    date.md
    devanagari.md
    expansion.md
    fallback.md
    hyphenation.md
    language-switcher.md
    line-height.md
    ltr.md
    number.md
    plural.md
    rtl.md
    time.md
    timezone.md
    truncation.md
  layout/
    footer.md
    header.md
    holy-grail.md
    main-content.md
    scroll-region.md
    scrollbar.md
    sidebar.md
  media/
    audio.md
    avatar.md
    carousel.md
    file.md
    folder.md
    gallery.md
    icon.md
    image.md
    player.md
    recorder.md
    slideshow.md
    video.md
  micro/
    age-gate.md
    aggregate-pivot-compare-diff.md
    aspect-ratio-box.md
    avatar-fallback.md
    avatar-presence-dot.md
    back-forward-history.md
    badge-dot.md
    beforeunload-policy.md
    bookmark-favorite-subscribe-follow.md
    captcha.md
    clipboard.md
    coach-mark.md
    coming-soon-page.md
    command-palette-footer.md
    comment.md
    consent-banner.md
    cookie-banner.md
    copy-button.md
    custom-scrollbar-thumb.md
    dark-scrollbar.md
    disabled-button-tooltip.md
    divider.md
    drag-drop-ghost.md
    drag-handle.md
    drawer-edit.md
    drawer-stacking.md
    duplicate-archive-restore-trash.md
    empty-illustration.md
    error-boundary.md
    error-illustration.md
    file-type-icon.md
    focus-ring.md
    forbidden-page.md
    forced-colors-spec.md
    grayscale-images.md
    grip-dots.md
    hashtag.md
    help-tooltip.md
    high-contrast-spec.md
    info-popover.md
    inline-edit.md
    keyboard-shortcut-hint.md
    keyboard-shortcut-modal.md
    last-updated-time.md
    loading-button.md
    long-press-menu.md
    maintenance-page.md
    mention.md
    modal-edit.md
    modal-stacking.md
    monochrome-spec.md
    not-found-page.md
    notification-dot.md
    offline-illustration.md
    pin-marker.md
    print-styles.md
    pull-to-refresh.md
    reaction.md
    reduced-motion-spec.md
    reorder-drag-drop.md
    resize-grip.md
    retry-button.md
    ring-offset.md
    save-discard-reset-refresh-retry.md
    scrollbar-corner.md
    selection-handles.md
    separator.md
    server-error-page.md
    session-expiry.md
    share-button.md
    share-embed-preview.md
    skeleton-avatar.md
    skeleton-breadcrumbs.md
    skeleton-cards.md
    skeleton-chart.md
    skeleton-charts.md
    skeleton-detail.md
    skeleton-forms.md
    skeleton-image.md
    skeleton-lists.md
    skeleton-maps.md
    skeleton-nav.md
    skeleton-shimmer-direction.md
    skeleton-tables.md
    skeleton-text.md
    sort-filter-group.md
    spacer.md
    status-indicator-dot.md
    swipe-actions.md
    text-selection.md
    toast-stacking.md
    tooltip-arrow.md
    tooltip-disabled-wrapper.md
    tour-spotlight.md
    undo-redo.md
    unread-marker.md
    unsaved-changes.md
    zoom-pan-annotate-highlight.md
  micro-interactions/
    active.md
    animation.md
    border.md
    caret.md
    context-menu-right-click.md
    cursor.md
    disabled.md
    focus.md
    font-face.md
    font-family.md
    gradient.md
    haptic.md
    hover-capability.md
    hover.md
    loading.md
    margin.md
    overscroll-behavior.md
    padding.md
    pointer-coarse-fine.md
    print-page-break.md
    scroll-behavior.md
    scroll-snap.md
    selection-copy.md
    selection.md
    shadow.md
    sound.md
    stacking-context.md
    sticky-positioning.md
    transform.md
    transition.md
    z-index-scale.md
  navigation/
    breadcrumbs.md
    command-palette.md
    context-menu.md
    menu.md
    navbar.md
    pagination.md
    stepper.md
    tabs.md
    workflow-breadcrumbs.md
  overlays/
    backdrop.md
    command-palette.md
    confirm.md
    context-menu.md
    dialog.md
    drawer.md
    dropdown.md
    lightbox.md
    menu.md
    modal.md
    overlay.md
    popover.md
    prompt.md
    scrim.md
    sheet.md
    tooltip.md
  pages/
    403.md
    404.md
    500.md
    coming-soon.md
    empty-folder.md
    maintenance.md
    no-internet.md
    offline-queue.md
    slow-network.md
    zero-results.md
  qa/
    accessibility-audit.md
    audit.md
    checklist.md
    i18n-audit.md
    performance.md
    premium-review.md
    regression.md
    snapshot.md
    visual.md
  theming/
    brand.md
    color-palette.md
    dark.md
    forced-colors.md
    light.md
    premium-principles.md
    preset.md
    skin.md
    surfaces-and-elevation.md
    template.md
    theme-toggle.md
    white-label.md
```

## 6. Cursor + pointer behavior per state (table)

| State | Cursor | Pointer event |
| --- | --- | --- |
| default | --cursor-default | none |
| pressed/active | --cursor-pointer | scale + --opacity-pressed |
| focus-visible | --cursor-default | ring only |
| loading | --cursor-progress | busy, still interactive where safe |
| drag source | --cursor-grab | pickup at --duration-instant |
| drag over | --cursor-grabbing | drop target highlight --color-brand-soft |

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
- dir tree: role=tree, each folder one role=treeitem with its section name
- file row: role=listitem, aria-label names the MD file and its section
- wildcard note: role=note, aria-label names the shared-MD wildcard rule

## 13. i18n requirements (text expansion, bidi, script, plural, locale format)

- Externalize every tree string (folder label, rule note) to locale files; zero literals in code.
- Tree rows hold 40% expansion from en inside the path column; no fixed heights on folder chips.
- Bidi: isolate spans on mixed-direction paths; RTL mirrors the tree per section 9; CLDR plurals on file counts.

## 14. Print behavior

Grayscale readable: no color-only meaning, every status pairs icon + text. Backgrounds dropped except essential fills; no ink waste. Headers/footers repeat on page break; keep-together on label + value. Mono variant where listed; borders at --color-border-strong in print. Charts/graphs/maps print as labeled list or pattern-filled outline, never raster. No shadow, no blur, no animation. Print styles come from tokens, same no-hardcode rule.

## 15. Skeleton loader spec (if data-driven, plus skeleton for every sub-shape)

Skeleton first, content second. Shapes: root block 100% width at component height token, radius --radius-sm; label bar width 40% at --text-sm with --leading-normal; value bar width 70%; action bar width 20% height --space-10; icon block --icon-size-md square. Fill --color-skeleton-base, shimmer band --color-skeleton-shine sweep --duration-slow linear infinite, off under --motion-reduced (static gray). No pulse on text. aria-busy=true while loading, role=status announcement when content lands, skeleton never read as content. Offline/error: skeleton replaced by state panel per section 3, not by blank.
- Tree row: width 70% bar at --text-sm height, --font-mono, fill --color-skeleton-base
- Folder chip: width 22% bar at --text-xs height, radius --radius-sm, fill --color-skeleton-base
- Index bar: width 45% bar at --text-xs height, --leading-normal, fill --color-skeleton-shine

## 16. Icon usage (Lucide names only)

Lucide line art only, imported by name, never emoji, never custom raster, never icon font. Size from --icon-size-sm/md/lg/xl; stroke from --icon-stroke-thin/regular/thick; color from --color-text-secondary / state tokens; aria-hidden=true on decorative icons, meaningful icons carry aria-label or visible text. No icon-only control without accessible name. Directional icons mirror in RTL. If no Lucide glyph fits, the design system owns the gap: file a decision-log entry, do not hand-draw.
- Lucide folder on each dir row at --icon-size-md, --icon-stroke-regular, --color-text-secondary
- Lucide file-text on each MD row at --icon-size-sm, --icon-stroke-thin, --color-text-tertiary

## 17. Prompt snippet (5-15 lines a dev pastes into their AI tool to regenerate this component in ANY framework, consuming theme-variables in that framework's equivalent)

```
Follow the Inovix design system at <path-to-design-system>.
Build the 'file-structure' component per docs/file-structure.md.
1. Use ONLY tokens from theme-variables.md (map to <framework> theme equivalent).
2. Implement all 26 states from section 3, or mark N/A with reason.
3. Add the skeleton shapes from section 15; shimmer off under prefers-reduced-motion.
4. Lucide icons only; no emoji; no raster; no hardcoded color/size/duration.
5. Keyboard full flow + focus-visible ring + aria per section 12; AA contrast both themes.
6. RTL mirror, 40% expansion, locale formats per section 13; print grayscale per section 14.
Return: component code + state matrix evidence + token usage list.
```
