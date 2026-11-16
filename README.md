# Inovix Design System - Start Here

This file is the entry point for anyone building an app with this design system (CONSUMER mode). Read it first, then follow the reading order below. It is short on purpose: the folder has about 480 files, and nobody, human or AI, should read them all to build one page.

## MUST checklist (read this even if you read nothing else)

An app built from this system is wrong unless ALL of these are true:

1. Output is the real app in the requested format. This folder is Markdown only, your output is not.
2. Fonts: Inter for all UI text, DejaVu Sans only inside the logo. Both are loaded from the pinned CDN stylesheets in theme-variables.md (Font sources). Google Fonts has no DejaVu Sans, do not use it. Use the CSS variables from theme-variables.md exactly, including its clamp() values for sizes. No fixed 64px header or 240px sidebar.
3. Header: navy, fixed, logo top-left, 3 lines: INOVIX, SOFTWARE LABS, Engineering Intelligence. Securing the Future. The logo is a link with text-decoration none and inherited color, never underlined or blue. Left of it is the animated hamburger toggle that opens and closes the sidebar. Right side holds a light and dark theme toggle.
4. Sidebar: fixed below the header, collapsible, every item has a Lucide icon, the current page is marked with the accent-soft fill, accent text and a 3 unit accent edge (not a solid blue block).
5. Only the main region scrolls. Footer is always visible at the bottom with copyright and the current year.
6. Both themes work. Theme variables are set on the root element, dark overrides by attribute, first visit follows the OS setting.
7. Icons are Lucide from the pinned CDN build. No text-only navigation, no emoji.
8. Page heading spacing: breadcrumbs, then --space-3 gap, page title, then --space-1 gap, one line of supporting text, then --space-6 gap, then the content card. Never let flex or grid stretch these apart.
9. Content card: raised surface, hairline border, large radius, header row with title, body with fields, footer row with buttons inside the card. Fields have a visible label above, a Required marker, helper or error text below, 3rem tall inputs, focus ring from the tokens. Primary button is navy (light theme) with white text, secondary is ghost.
10. Info modal: icon in a tinted circle, title, label and value rows of what was submitted, a single primary button, scrim with blur, focus trapped, Escape and scrim click close it, focus returns to the submit button. Not a plain paragraph, not alert().

## Known mistakes to avoid (seen in real generated apps)

| Wrong | Right |
| --- | --- |
| Converting shadow or color tokens to another format, for example "#03182D / 0.08" | Copy token values verbatim. Shadows are already rgb() with alpha. Scrim is --scrim-fill, used directly as the backdrop background |
| main is a flex column with gap var(--space-section), which spreads breadcrumbs, title, subtitle and card far apart | main is a normal block. Wrap breadcrumbs, title and subtitle in one page header block using the exact gaps in MUST item 8 |
| No sidebar toggle, so the sidebar is unreachable on mobile | Animated hamburger in the header, left of the logo, opens and closes the sidebar on every breakpoint |
| Active nav item as a solid accent block | Accent-soft fill, accent text and icon, 3 unit accent edge on the inline-start side |
| Logo link underlined, blue, or tabindex -1 | text-decoration none, color inherited, focusable |
| Modal close button position absolute inside a modal that is not position relative, so the X lands in the screen corner | Put the close button in the modal header row, in normal flow, inline-end |
| Modal backdrop with no visible dim or blur because the scrim color was malformed | background var(--scrim-fill) plus backdrop blur from --glass-blur |
| Theme script at the end of body, causing a flash of the wrong theme | Tiny inline script in head sets data-theme before first paint |
| Setting the theme by removing the attribute in light and adding it in dark, while some tokens only exist for dark | Set data-theme to light or dark explicitly on the root element |
| Fixed pixel sizes for header, sidebar or fonts | The clamp() based tokens exactly as written |
| Footer text repeating the tagline | Footer is copyright and the current year, plus optional Privacy and Terms links |

## Rules for the AI reading this folder

1. You are in CONSUMER mode when the request is to build an app, page or component. Build the thing requested. Your output is a working app in the format the requester asked for (for example a single index.html). The "no code" rule in this folder applies to the design system files themselves, never to the app you build from them.
2. Do not open, read or follow REQUIREMENTS.MD. It is the generator spec for the design system owner, not part of the design system. Ignore the .git folder too.
3. Do not read every file. Read the files in "Reading order" below, then only the component files the requirement needs.
4. When two files disagree, the more specific file wins, except that this README and theme-variables.md win over any component file. Sections titled "Build notes (authoritative)" win over the rest of their file.
5. Never invent a color, font, radius or shadow. Use tokens from theme-variables.md. Every color token lists an sRGB fallback value: put those values in the app as the actual stylesheet variables, with the token names exactly as written.

## Reading order

| Step | File | Why |
| --- | --- | --- |
| 1 | theme-variables.md | All tokens: color (navy ramp, light, dark), type, spacing, radius, shadow, motion, layout, logo, fonts and icon sources |
| 2 | brand/logo.md and brand/logo-text-only.md, brand/logo-responsive.md | The INOVIX text logo, exact lines, colors and sizes |
| 3 | layout/holy-grail.md, layout/header.md, layout/sidebar.md, layout/footer.md, layout/main-content.md | The page shell |
| 4 | Components the requirement names, for example forms/form-field.md, forms/input.md, forms/button.md, overlays/modal.md, feedback/toast.md | Only what the page uses |
| 5 | theming/theme-toggle.md, a11y/focus.md | Theme switch and focus ring |
| 6 | contexts/ and pages/ files that match the kind of app | Only if the requirement fits one |

For each component file, read sections 2b or 4 (build notes, variants), 5 (behavior), 8 (responsive), 12 (accessibility). The 25 row state matrix is a lookup table: use it for the states the component really has.

## What a correct Inovix app looks like

- Shell: fixed navy header across the top with the INOVIX text logo at top-left (3 lines: INOVIX, SOFTWARE LABS, Engineering Intelligence. Securing the Future.), fixed collapsible left sidebar below it, fluid main region that is the only scroll area, footer with copyright and the current year. No right sidebar.
- The header is navy (#03182D) in both light and dark theme, with white text. It is never white.
- Logo is real text, never an image or icon, set in DejaVu Sans Regular, white on navy. Load DejaVu Sans from the font source in theme-variables.md or the logo will fall back to a random system font.
- Body and UI text is Inter (font source in theme-variables.md), not DejaVu Sans.
- Page background is the tinted near-white (light) or layered navy (dark). Content lives in cards: raised surface, large radius, hairline border, soft navy-tinted shadow.
- One accent color (the blue step of the navy family) for links, focus, active navigation. At most one filled primary button per region. Secondary actions are outlined or ghost.
- Icons are Lucide only, loaded from the pinned CDN build named in theme-variables.md. Never emoji, never hand drawn SVG icons.
- Both themes ship together, switched by one toggle in the header, defaulting to the OS preference on first visit and remembering the choice, with no flash on load.

## Concrete recipes for the most common requests

Simple form page (like a name and age form):
- Main shows breadcrumbs, a page title and one line of help text, then ONE card limited to --measure-reading wide, not full width.
- Inside the card: a card title, fields stacked with --space-5 between them, then a footer row inside the card with the primary button at inline-end.
- Field: label above the input (--text-sm, --weight-medium, --color-text-primary), the input below at --touch-target-comfort height, --radius-md, --color-surface-raised fill, hairline --color-border-strong, placeholder in --color-text-tertiary, helper text below in --text-sm. Focus: --color-border-focus ring with --shadow-focus-glow. Required marker is text, not color alone. Validation is inline, under the field, with an icon, the message and the error color.
- Age input is a number input with min and max and inputmode numeric. Name input has autocomplete name.
- Submit validates first, shows inline errors if any, and otherwise opens the modal. Never use alert().

Info modal:
- Centered dialog on --color-surface-overlay, --radius-lg, --shadow-xl, width fluid up to --measure-reading, over a --color-scrim backdrop at --opacity-scrim with backdrop blur from the glass tokens.
- Header row: Lucide info icon in --color-info plus the title, close button at inline-end. Body lists the submitted values as label and value pairs (label --color-text-tertiary, value --color-text-primary), not as raw JSON. Footer has one primary button.
- Behavior: focus moves into the dialog, focus is trapped, Escape and scrim click close it, focus returns to the submit button. role dialog, aria-modal true, aria-labelledby on the title. Entrance is a short fade and 8 unit rise using the motion tokens, none under reduced motion.

Menu entry: the page being built is a sidebar item, marked current, with a Lucide icon and label. Include two or three plausible sibling entries so the sidebar does not look empty, and put them in the sidebar, not in the header.

## Quality bar before you answer

- Page at 1440 wide, 768 wide and 390 wide: nothing overflows, sidebar becomes a drawer on mobile, form card stays readable.
- Header navy, logo white and legible, hamburger animates to X.
- Dark theme looks as deliberate as light: layered navy surfaces, off-white text, no pure black, no pure white.
- Every text and control meets the contrast table in theme-variables.md.
- Every interactive element has hover, active, focus-visible and disabled styles from the tokens.
- No hardcoded color outside the token variables, no emoji, no default browser button or input styling, no unstyled controls.
