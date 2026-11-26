# theme-variables

> BUILDING AN APP? STOP. Open README.md in this folder first and follow its MUST checklist. This file is only the token reference.


Single source of truth for every visual value in the Inovix design system.

Purpose: one token file controls the whole system. A white-label rebrand swaps this one file and regenerates. Components never hardcode values; they reference tokens by name.

Token rule: every visual value in any component is a reference to a token in theme-variables.md; hardcoded values are forbidden. The generated project implements these tokens in theme-variables.scss; this document defines the tokens, not the code.

Conventions:
- Color tokens are OKLCH. Spacing and size tokens are rem. Time tokens are ms. Angle tokens are deg.
- Every token has a light value and a dark value unless the token is theme-independent.
- Default theme is light. One theme toggle flips every token at once (theming/light.md, theming/dark.md).
- Alpha is documented as a separate opacity token next to the color that uses it, never baked into component code.
- Token names are semantic, never raw: components say --color-text-secondary, not "gray-500".

## Navy ramp (theme-independent, one hue family)

One hue family at OKLCH hue 250, the exact hue of the brand navy #03182D. The ramp is defined once and is identical in both themes. Step 950 IS the brand navy (oklch(0.2049 0.0505 250) = #03182D). Every neutral in this file is tinted toward this hue, never pure grey and never pure black. Earlier drafts used hue 273.5 (violet) and an out-of-gamut step 950; both were wrong and are superseded.

sRGB fallback column: use it where OKLCH is not supported, or when a tool needs hex. OKLCH is the source of truth, the fallback is its gamut-mapped sRGB equivalent.

| Token | OKLCH | sRGB fallback | Use |
| --- | --- | --- | --- |
| --color-navy-50 | oklch(0.975 0.008 250) | #F3F7FC | Lightest tint, light theme app tint. |
| --color-navy-100 | oklch(0.95 0.014 250) | #E8EFF8 | Brand soft fill, light hover wash. |
| --color-navy-200 | oklch(0.905 0.024 250) | #D4E1EF | Light hairlines, chips. |
| --color-navy-300 | oklch(0.83 0.036 250) | #B6CADE | Disabled fills, light dividers. |
| --color-navy-400 | oklch(0.72 0.052 250) | #8CA8C5 | Muted icons on light, dark secondary text. |
| --color-navy-500 | oklch(0.6 0.07 250) | #6084A9 | Secondary text on dark, mid tone. |
| --color-navy-600 | oklch(0.49 0.09 250) | #356391 | Mid navy, charts, secondary icons. |
| --color-navy-700 | oklch(0.4 0.085 250) | #1F4A73 | Secondary action fill, strong dark borders. |
| --color-navy-800 | oklch(0.325 0.07 250) | #143656 | Header hairline, dark chips. |
| --color-navy-900 | oklch(0.26 0.06 250) | #092540 | Dark raised hover, deep fills. |
| --color-navy-950 | oklch(0.2049 0.0505 250) | #03182D | BRAND NAVY #03182D. Header, primary fill (light), logo on light. |
| --color-navy-975 | oklch(0.155 0.04 250) | #010D1C | Dark theme page base, pressed brand. |

## Color tokens, light theme (default)

| Token | OKLCH | sRGB fallback | Purpose |
| --- | --- | --- | --- |
| --color-navy | oklch(0.2049 0.0505 250) | #03182D | Brand navy #03182D (ramp step 950). Header bar in both themes, navy panels, brand text on light. |
| --color-navy-content | oklch(0.99 0 0) | #FCFCFC | Text on navy. Logo and header text. |
| --color-brand | oklch(0.2049 0.0505 250) | #03182D | Same as navy; the rebrand target. |
| --color-brand-content | oklch(0.99 0 0) | #FCFCFC | Text on brand. |
| --color-brand-strong | oklch(0.155 0.04 250) | #010D1C | Pressed brand (ramp step 975). |
| --color-brand-soft | oklch(0.95 0.014 250) | #E8EFF8 | Brand tint fill: selected rows, hover wash, chips. |
| --color-surface-base | oklch(0.985 0.004 250) | #F8FAFD | Page background. Dark: ramp step 975. |
| --color-surface-raised | oklch(1 0 0) | #FFFFFF | Cards, panels, sidebar. Raised sits above base in both themes. |
| --color-surface-sunken | oklch(0.962 0.008 250) | #EFF3F8 | Recessed areas, inputs well, footer. |
| --color-surface-overlay | oklch(1 0 0) | #FFFFFF | Modals, popovers, sheets. |
| --color-surface-inverse | oklch(0.2049 0.0505 250) | #03182D | Inverted blocks. |
| --color-text-primary | oklch(0.2049 0.0505 250) | #03182D | Body text. Light: navy. Dark: tinted off-white. |
| --color-text-secondary | oklch(0.4 0.045 250) | #354A5F | Secondary text. |
| --color-text-tertiary | oklch(0.49 0.04 250) | #4F6277 | Captions, hints, placeholders. |
| --color-text-disabled | oklch(0.66 0.02 250) | #89939E | Disabled text (exempt from contrast by WCAG, still legible). |
| --color-text-on-brand | oklch(0.99 0 0) | #FCFCFC | Text on brand fills. |
| --color-text-on-error | oklch(0.99 0 0) | #FCFCFC | Text on error fills. |
| --color-primary | oklch(0.2049 0.0505 250) | #03182D | Primary action fill. Light: navy. Dark: bright navy-family step, because navy on navy vanishes. |
| --color-primary-content | oklch(0.99 0 0) | #FCFCFC | Text on primary. |
| --color-secondary | oklch(0.4 0.085 250) | #1F4A73 | Secondary action fill. |
| --color-secondary-content | oklch(0.99 0 0) | #FCFCFC | Text on secondary. |
| --color-accent | oklch(0.5 0.16 255) | #0961BB | Single interactive accent: links, focus, active nav, selection. |
| --color-accent-hover | oklch(0.43 0.15 255) | #024E9A | Accent hover and pressed. |
| --color-accent-soft | oklch(0.95 0.03 255) | #E4F0FF | Accent tint fill: active nav item, selected chip. |
| --color-accent-content | oklch(0.99 0 0) | #FCFCFC | Text on accent fill. |
| --color-neutral | oklch(0.5 0.02 250) | #5B646F | Neutral fills. |
| --color-neutral-content | oklch(0.98 0 0) | #F8F8F8 | Text on neutral. |
| --color-info | oklch(0.5 0.11 235) | #006C97 | Info feedback. Always with icon and text. |
| --color-info-content | oklch(0.99 0 0) | #FCFCFC | Text on info. |
| --color-success | oklch(0.48 0.11 155) | #156F41 | Success feedback. |
| --color-success-content | oklch(0.99 0 0) | #FCFCFC | Text on success. |
| --color-warning | oklch(0.78 0.14 80) | #E6AC3D | Warning feedback. |
| --color-warning-content | oklch(0.25 0.04 70) | #2E1E0A | Text on warning. |
| --color-error | oklch(0.5 0.17 25) | #B02A2D | Error feedback. Muted red, never grey, never neon. |
| --color-error-content | oklch(0.99 0 0) | #FCFCFC | Text on error. |
| --color-border | oklch(0.91 0.012 250) | #DBE2E9 | Hairline borders. |
| --color-border-strong | oklch(0.78 0.02 250) | #AEB9C4 | Strong borders, dividers, input outlines (3:1 on surface). |
| --color-border-focus | oklch(0.5 0.16 255) | #0961BB | Focus ring color, same family as accent. |
| --color-selection | oklch(0.88 0.06 250) | #BADBFE | Text selection background. |
| --color-selection-text | oklch(0.2049 0.0505 250) | #03182D | Text selection foreground. |
| --color-skeleton-base | oklch(0.935 0.01 250) | #E5EAF0 | Skeleton fill. |
| --color-skeleton-shine | oklch(0.98 0.005 250) | #F6F9FC | Skeleton shimmer band. |
| --color-scrim | oklch(0.155 0.04 250) | #010D1C | Scrim base color; alpha from --opacity-scrim. |
| --color-header-bg | oklch(0.2049 0.0505 250) | #03182D | Header fill, navy in BOTH themes (rule 10). |
| --color-header-text | oklch(0.99 0 0) | #FCFCFC | Header text and icons, white on navy in BOTH themes. |
| --color-header-border | oklch(0.325 0.07 250) | #143656 | Header bottom hairline (ramp step 800). |

## Color tokens, dark theme

Dark is not an inversion. Surfaces are layered navy (sunken darker than base, base darker than raised, raised darker than overlay). Text is tinted off-white. The header stays brand navy with white text in both themes (rule 10).

| Token | OKLCH | sRGB fallback | Purpose |
| --- | --- | --- | --- |
| --color-navy | oklch(0.2049 0.0505 250) | #03182D | Brand navy #03182D (ramp step 950). Header bar in both themes, navy panels, brand text on light. |
| --color-navy-content | oklch(0.99 0 0) | #FCFCFC | Text on navy. Logo and header text. |
| --color-brand | oklch(0.2049 0.0505 250) | #03182D | Same as navy; the rebrand target. |
| --color-brand-content | oklch(0.99 0 0) | #FCFCFC | Text on brand. |
| --color-brand-strong | oklch(0.155 0.04 250) | #010D1C | Pressed brand (ramp step 975). |
| --color-brand-soft | oklch(0.3 0.05 250) | #192F46 | Brand tint fill: selected rows, hover wash, chips. |
| --color-surface-base | oklch(0.155 0.04 250) | #010D1C | Page background. Dark: ramp step 975. |
| --color-surface-raised | oklch(0.235 0.048 250) | #0A1F34 | Cards, panels, sidebar. Raised sits above base in both themes. |
| --color-surface-sunken | oklch(0.125 0.035 250) | #000713 | Recessed areas, inputs well, footer. |
| --color-surface-overlay | oklch(0.275 0.05 250) | #13293F | Modals, popovers, sheets. |
| --color-surface-inverse | oklch(0.985 0.004 250) | #F8FAFD | Inverted blocks. |
| --color-text-primary | oklch(0.945 0.01 250) | #E8EDF3 | Body text. Light: navy. Dark: tinted off-white. |
| --color-text-secondary | oklch(0.8 0.02 250) | #B4BFCA | Secondary text. |
| --color-text-tertiary | oklch(0.7 0.025 250) | #93A0AE | Captions, hints, placeholders. |
| --color-text-disabled | oklch(0.52 0.025 250) | #5E6A77 | Disabled text (exempt from contrast by WCAG, still legible). |
| --color-text-on-brand | oklch(0.99 0 0) | #FCFCFC | Text on brand fills. |
| --color-text-on-error | oklch(0.155 0.04 250) | #010D1C | Text on error fills. |
| --color-primary | oklch(0.76 0.11 250) | #79B6F4 | Primary action fill. Light: navy. Dark: bright navy-family step, because navy on navy vanishes. |
| --color-primary-content | oklch(0.155 0.04 250) | #010D1C | Text on primary. |
| --color-secondary | oklch(0.35 0.06 250) | #213C59 | Secondary action fill. |
| --color-secondary-content | oklch(0.945 0.01 250) | #E8EDF3 | Text on secondary. |
| --color-accent | oklch(0.76 0.11 250) | #79B6F4 | Single interactive accent: links, focus, active nav, selection. |
| --color-accent-hover | oklch(0.82 0.1 250) | #96C9FE | Accent hover and pressed. |
| --color-accent-soft | oklch(0.3 0.07 250) | #0D2F4F | Accent tint fill: active nav item, selected chip. |
| --color-accent-content | oklch(0.155 0.04 250) | #010D1C | Text on accent fill. |
| --color-neutral | oklch(0.4 0.03 250) | #3C4958 | Neutral fills. |
| --color-neutral-content | oklch(0.945 0.01 250) | #E8EDF3 | Text on neutral. |
| --color-info | oklch(0.76 0.1 235) | #6DBBE8 | Info feedback. Always with icon and text. |
| --color-info-content | oklch(0.155 0.04 250) | #010D1C | Text on info. |
| --color-success | oklch(0.76 0.13 155) | #65C98C | Success feedback. |
| --color-success-content | oklch(0.155 0.04 250) | #010D1C | Text on success. |
| --color-warning | oklch(0.83 0.13 85) | #EEC05B | Warning feedback. |
| --color-warning-content | oklch(0.2 0.03 70) | #1F1306 | Text on warning. |
| --color-error | oklch(0.72 0.15 25) | #F47B74 | Error feedback. Muted red, never grey, never neon. |
| --color-error-content | oklch(0.155 0.04 250) | #010D1C | Text on error. |
| --color-border | oklch(0.3 0.03 250) | #222F3C | Hairline borders. |
| --color-border-strong | oklch(0.44 0.04 250) | #425468 | Strong borders, dividers, input outlines (3:1 on surface). |
| --color-border-focus | oklch(0.78 0.11 250) | #80BDFB | Focus ring color, same family as accent. |
| --color-selection | oklch(0.4 0.09 250) | #1B4A76 | Text selection background. |
| --color-selection-text | oklch(0.99 0 0) | #FCFCFC | Text selection foreground. |
| --color-skeleton-base | oklch(0.26 0.035 250) | #172534 | Skeleton fill. |
| --color-skeleton-shine | oklch(0.32 0.04 250) | #233447 | Skeleton shimmer band. |
| --color-scrim | oklch(0.08 0.03 250) | #000207 | Scrim base color; alpha from --opacity-scrim. |
| --color-header-bg | oklch(0.2049 0.0505 250) | #03182D | Header fill, navy in BOTH themes (rule 10). |
| --color-header-text | oklch(0.99 0 0) | #FCFCFC | Header text and icons, white on navy in BOTH themes. |
| --color-header-border | oklch(0.325 0.07 250) | #143656 | Header bottom hairline (ramp step 800). |

## Opacity tokens

| Token | Light | Dark | Purpose |
| --- | --- | --- | --- |
| --opacity-glass-bg | 0.72 | 0.65 | Glass fill alpha. |
| --opacity-glass-border | 0.50 | 0.12 | Glass border alpha. |
| --opacity-scrim | 0.45 | 0.60 | Modal scrim alpha. |
| --opacity-disabled | 0.38 | 0.38 | Disabled element alpha. |
| --opacity-focus-ring | 0.50 | 0.60 | Focus ring alpha. |
| --opacity-hover | 0.06 | 0.10 | Hover tint alpha over surfaces. |
| --opacity-pressed | 0.12 | 0.16 | Pressed tint alpha. |
| --opacity-selected | 0.10 | 0.14 | Selected tint alpha. |
| --opacity-skeleton-shine | 0.60 | 0.45 | Shimmer band alpha. |
| --opacity-logo-alpha | 0.9882 | 0.9882 | Legacy source alpha 252/255; solid preferred, never below this. |

## Spacing tokens (8px scale, no magic numbers)

| Token | rem | px at 16px root | Use |
| --- | --- | --- | --- |
| --space-0 | 0 | 0 | Reset. |
| --space-1 | 0.25rem | 4 | Tight gaps, icon-to-text. |
| --space-2 | 0.5rem | 8 | Inline gaps, chip padding-x. |
| --space-3 | 0.75rem | 12 | Field padding, list row gap. |
| --space-4 | 1rem | 16 | Card padding, section gap. |
| --space-5 | 1.25rem | 20 | Panel padding. |
| --space-6 | 1.5rem | 24 | Card padding, modal padding. |
| --space-8 | 2rem | 32 | Section padding. |
| --space-10 | 2.5rem | 40 | Page section gap. |
| --space-12 | 3rem | 48 | Large section gap. |
| --space-16 | 4rem | 64 | Page top/bottom. |
| --space-20 | 5rem | 80 | Hero spacing. |
| --space-24 | 6rem | 96 | Max page spacing. |
| --space-gutter | clamp(1rem, 4vw, 3rem) | fluid | Holy Grail gutter (layout/holy-grail.md). |
| --space-section | clamp(2rem, 6vw, 5rem) | fluid | Gap between whole marketing or landing sections only. NEVER use it as a gap inside the app shell main region, and never between breadcrumbs, title, subtitle and card. |
| --space-inline | clamp(0.75rem, 2vw, 1.5rem) | fluid | Inline element gaps. |
| --space-safe-top | env(safe-area-inset-top, 0px) | device | Notch, status bar. |
| --space-safe-right | env(safe-area-inset-right, 0px) | device | Gesture edge. |
| --space-safe-bottom | env(safe-area-inset-bottom, 0px) | device | Home indicator. |
| --space-safe-left | env(safe-area-inset-left, 0px) | device | Gesture edge. |

Margin and padding rule: only --space-* tokens. No bare numbers in components. Scale is 4-based through --space-24; beyond it, compose.

## Radius tokens

| Token | Value | Use |
| --- | --- | --- |
| --radius-none | 0 | Sharp edges, table cells, hairlines. |
| --radius-xs | 0.125rem | Badges, tiny chips. |
| --radius-sm | 0.25rem | Inputs, buttons small. |
| --radius-md | 0.5rem | Buttons, fields, cards small. |
| --radius-lg | 1rem | Cards, panels, modals. |
| --radius-xl | 1.5rem | Sheets, drawers, hero panels. |
| --radius-2xl | 2rem | Marketing panels. |
| --radius-full | 999rem | Pills, avatars, fab. |
| --radius-selector | 0.25rem | Selectors (checkbox, radio, tab). |
| --radius-field | 0.5rem | Form fields. |
| --radius-box | 1rem | Boxes, cards. |
| --radius-chip | 999rem | Chips, pills. |
| --radius-pill | 999rem | Pill-shaped elements, alias of --radius-chip kept for legacy callers. |

## Shadow tokens (elevation scale, colored, inner, focus glow)

| Token | Value | Use |
| --- | --- | --- |
| --shadow-xs | 0 1px 2px rgb(3 24 45 / 0.06) | Raised hairline elements. |
| --shadow-sm | 0 1px 3px rgb(3 24 45 / 0.08), 0 1px 2px rgb(3 24 45 / 0.04) | Cards at rest. |
| --shadow-md | 0 4px 6px rgb(3 24 45 / 0.07), 0 2px 4px rgb(3 24 45 / 0.05) | Hover lift, dropdowns. |
| --shadow-lg | 0 10px 15px rgb(3 24 45 / 0.08), 0 4px 6px rgb(3 24 45 / 0.05) | Popovers, command palette. |
| --shadow-xl | 0 20px 25px rgb(3 24 45 / 0.10), 0 8px 10px rgb(3 24 45 / 0.06) | Modals, drawers. |
| --shadow-colored-brand | 0 8px 24px rgb(3 24 45 / 0.25) | Brand-tinted elevation, primary CTA hover. |
| --shadow-colored-accent | 0 8px 24px rgb(9 97 187 / 0.30) | Accent glow, active nav, navy-family accent. |
| --shadow-inner | inset 0 1px 2px rgb(3 24 45 / 0.06) | Inset fields, pressed wells. |
| --shadow-inner-strong | inset 0 2px 4px rgb(3 24 45 / 0.10) | Sunken panels. |
| --shadow-focus-glow | 0 0 0 3px rgb(9 97 187 / 0.35) | Focus glow ring, accent hue. |
| --shadow-scrim | 0 0 0 9999px var(--scrim-fill) | Scrim via shadow, optional. |
| --scrim-fill | rgb(1 13 28 / 0.45) | Ready to use scrim color with alpha baked in. Use directly as the backdrop background. Never wrap it in another color function. |

Shadows use rgb() with alpha so they are valid CSS exactly as written. Copy them verbatim. Do not convert them to hex with a slash, that is invalid CSS and the shadow silently disappears.

Dark theme overrides (a navy tinted shadow is invisible on navy, so dark uses black):

| Token | Dark value |
| --- | --- |
| --shadow-xs | 0 1px 2px rgb(0 0 0 / 0.30) |
| --shadow-sm | 0 1px 3px rgb(0 0 0 / 0.40), 0 1px 2px rgb(0 0 0 / 0.25) |
| --shadow-md | 0 4px 6px rgb(0 0 0 / 0.35), 0 2px 4px rgb(0 0 0 / 0.25) |
| --shadow-lg | 0 10px 15px rgb(0 0 0 / 0.40), 0 4px 6px rgb(0 0 0 / 0.30) |
| --shadow-xl | 0 20px 25px rgb(0 0 0 / 0.50), 0 8px 10px rgb(0 0 0 / 0.35) |
| --shadow-focus-glow | 0 0 0 3px rgb(121 182 244 / 0.55) |
| --scrim-fill | rgb(0 2 7 / 0.60) |

Elevation mapping: level 0 none, level 1 --shadow-xs, level 2 --shadow-sm, level 3 --shadow-md, level 4 --shadow-lg, level 5 --shadow-xl. Components take a level, never a raw shadow.

## Z-index tokens (stacking scale)

| Token | Value | Layer |
| --- | --- | --- |
| --z-base | 0 | Page content. |
| --z-raised | 10 | Cards, raised rows. |
| --z-sticky | 20 | Sticky headers inside scroll regions. |
| --z-sidebar | 25 | Fixed sidebar, below the header. |
| --z-header | 30 | Holy Grail header. |
| --z-dropdown | 40 | Dropdowns, menus, combobox lists. |
| --z-sticky-content | 50 | Sticky table headers, sticky toolbars. |
| --z-overlay | 60 | Scrim, backdrop. |
| --z-drawer | 65 | Mobile sidebar drawer and drawers, above the scrim. |
| --z-modal | 70 | Modals, dialogs, confirm, prompt. |
| --z-popover | 80 | Popovers, tooltips parent. |
| --z-toast | 90 | Toaster stack. |
| --z-tooltip | 100 | Tooltips. |
| --z-max | 200 | Tour spotlight, session expiry, captcha wall. |

Stacking context rule: each overlay component creates its own context; children never leak past --z-max. Drawer and sheet stack below modal; toast above all; tooltip topmost.

## Typography tokens

Families:

| Token | Value | Use |
| --- | --- | --- |
| --font-ui | "Inter", system-ui, "Segoe UI", Roboto, "Helvetica Neue", sans-serif | All UI text. Inter, loaded from the font source below. DejaVu Sans is NOT installed on most devices, so it can never be the UI face. |
| --font-display | "Inter", system-ui, sans-serif | Display uses the same family at heavier weights and tighter tracking. |
| --font-mono | "DejaVu Sans Mono", ui-monospace, monospace | Code, numbers, tabular data. |

Weights 100-900: --weight-thin 100, --weight-extralight 200, --weight-light 300, --weight-regular 400 (logo and body default), --weight-medium 500, --weight-semibold 600, --weight-bold 700, --weight-extrabold 800, --weight-black 900.

Optical sizing: --font-optical-sizing: auto where the variable font supports it; fixed 400 optical for the logo per brand/logo-typography.md.

Variable font policy: ship variable DejaVu Sans when the platform offers it; static 400/700 subset as the floor; never synthesize bold or italic.

Fluid type scale (clamp, fluid at every step):

| Token | Value | Use |
| --- | --- | --- |
| --text-2xs | clamp(0.5625rem, 0.5rem + 0.2vw, 0.625rem) | Micro labels, kbd hints. |
| --text-xs | clamp(0.625rem, 0.575rem + 0.2vw, 0.75rem) | Captions, badges. |
| --text-sm | clamp(0.75rem, 0.7rem + 0.2vw, 0.875rem) | Secondary text, table cells. |
| --text-base | clamp(0.875rem, 0.8rem + 0.3vw, 1rem) | Body. |
| --text-lg | clamp(1rem, 0.9rem + 0.4vw, 1.125rem) | Lead paragraphs. |
| --text-xl | clamp(1.125rem, 1rem + 0.5vw, 1.25rem) | Card titles. |
| --text-2xl | clamp(1.25rem, 1.1rem + 0.6vw, 1.5rem) | Section titles. |
| --text-3xl | clamp(1.5rem, 1.25rem + 0.9vw, 1.875rem) | Page titles. |
| --text-4xl | clamp(1.875rem, 1.5rem + 1.2vw, 2.25rem) | Hero titles. |
| --text-5xl | clamp(2.25rem, 1.75rem + 1.6vw, 3rem) | Marketing display. |
| --text-display | clamp(2.5rem, 2rem + 2.5vw, 4.5rem) | Landing display. |

Line height: --leading-none 1, --leading-tight 1.25, --leading-snug 1.375, --leading-normal 1.5, --leading-relaxed 1.625, --leading-loose 2. Per-script overrides live in i18n/line-height.md.

Tracking: --tracking-tighter -0.05em, --tracking-tight -0.025em, --tracking-normal 0, --tracking-wide 0.025em, --tracking-wider 0.05em, --tracking-widest 0.1em.

Font sources (load these, do not assume they are installed). Pin versions.

| Face | Source | Weights |
| --- | --- | --- |
| Inter (UI) | CDN stylesheet: https://cdn.jsdelivr.net/npm/@fontsource/inter@5.3.0/index.css plus 500.css, 600.css, 700.css in the same folder | 400, 500, 600, 700 |
| DejaVu Sans (logo only) | CDN stylesheet: https://cdn.jsdelivr.net/npm/@fontsource/dejavu-sans@5.3.0/400.css | 400 |
| DejaVu Sans Mono (code) | System mono fallback is acceptable | 400 |

A single-file app links these stylesheets in the head. The logo must never render in a fallback face: wait for the DejaVu Sans stylesheet before showing the lockup, or hold the lockup invisible up to --duration-fast, then show it.

Font loading strategy and FOIT/FOUT policy: preload the 400 face, async-load 700; font-display swap with a metric-matched fallback so layout never shifts; FOIT window must not exceed --duration-fast; FOUT is tolerated over FOIT; fallback stack always rendered, never blank.

## Motion tokens

Durations (ms):

| Token | Value | Use |
| --- | --- | --- |
| --duration-instant | 0 | State swaps, theme flip under reduced motion. |
| --duration-fast | 150 | Hover, focus ring, small feedback. |
| --duration-normal | 250 | Disclosures, dropdowns, toggles. |
| --duration-slow | 400 | Modal enter, drawer slide. |
| --duration-slower | 700 | Page transitions, hero reveals. |
| --duration-skeleton-shimmer | 1400 | Skeleton shimmer sweep. |
| --duration-toast | 4000 | Toast dwell before auto-dismiss. |
| --duration-tooltip-delay | 300 | Tooltip appear delay. |
| --duration-debounce-input | 250 | Input debounce default. |

Easings:

| Token | Value | Use |
| --- | --- | --- |
| --ease-standard | cubic-bezier(0.4, 0, 0.2, 1) | Default. |
| --ease-accelerate | cubic-bezier(0.55, 0.06, 0.68, 0.19) | Exit. |
| --ease-decelerate | cubic-bezier(0.22, 1, 0.36, 1) | Enter. |
| --ease-in-out | cubic-bezier(0.65, 0, 0.35, 1) | Bidirectional moves. |
| --ease-spring | spring(stiffness 300, damping 30, mass 1) | Tilt, overshoot reveals; physics params, documented not coded. |
| --ease-bounce | spring(stiffness 500, damping 12) | Playful confirm. |

Other motion tokens: --stagger-step 40ms (list stagger), --motion-will-change-policy (transform and opacity only; will-change only during active animation, removed after), --motion-gpu-rule (animate transform/opacity only; never layout properties), --motion-reduced (when prefers-reduced-motion: all durations become --duration-instant, springs become instant set, shimmer stops, autoplay off), --motion-flip-policy (FLIP only for list reorder, never on scroll).

Animation library tokens: entrance --motion-enter (fade + rise 8px, --duration-normal, --ease-decelerate), exit --motion-exit (fade + sink, --duration-fast, --ease-accelerate), page --motion-page (slide + fade, --duration-slow), layout --motion-layout (shared-axis move, --duration-normal, --ease-in-out).

## Breakpoint tokens

| Token | px | rem | Name |
| --- | --- | --- | --- |
| --bp-xs | 320 | 20 | Tiny portrait. |
| --bp-sm | 640 | 40 | Mobile landscape / small tablet. |
| --bp-md | 768 | 48 | Tablet portrait. |
| --bp-lg | 1024 | 64 | Tablet landscape / small desktop. |
| --bp-xl | 1280 | 80 | Desktop. |
| --bp-2xl | 1536 | 96 | Large desktop. |

Band names: --bp-band-mobile below --bp-sm, --bp-band-tablet --bp-sm to --bp-lg minus 1, --bp-band-desktop --bp-lg and up. Fluid rule: clamp() with tokens, never display:none as the only response; collapse then stack then hide, in that order.

## Cursor tokens

| Token | Keyword | Use |
| --- | --- | --- |
| --cursor-default | default | Rest state. |
| --cursor-pointer | pointer | Clickable. |
| --cursor-text | text | Editable text. |
| --cursor-grab | grab | Draggable at rest. |
| --cursor-grabbing | grabbing | Drag in progress. |
| --cursor-not-allowed | not-allowed | Disabled, blocked. |
| --cursor-progress | progress | Busy, still interactive. |
| --cursor-wait | wait | Busy, blocked. |
| --cursor-cell | cell | Cell selection. |
| --cursor-crosshair | crosshair | Precision pick. |
| --cursor-move | move | Move target. |
| --cursor-zoom-in | zoom-in | Zoomable in. |
| --cursor-zoom-out | zoom-out | Zoomable out. |
| --cursor-help | help | Help target. |
| --cursor-custom-* | asset token | Custom cursors reference an asset token, never a file path. |

Disabled and loading rule: disabled elements take --cursor-not-allowed; loading interactive elements take --cursor-progress; loading non-interactive regions take --cursor-wait.

## Sound tokens

Policy: sound default OFF. No autoplay. Per-event token, never a file path in a component. Respect --sound-enabled, user mute, OS mute, and prefers-reduced-motion (reduced motion silences non-essential sound). Volume token --sound-volume default 0.5, range 0 to 1. Haptic equivalent documented per event in micro-interactions/haptic.md.

| Event token | Duration token | Default | Haptic pair |
| --- | --- | --- | -- |
| --sound-success | --sound-duration-medium | OFF | --haptic-medium |
| --sound-error | --sound-duration-long | OFF | --haptic-heavy |
| --sound-warning | --sound-duration-medium | OFF | --haptic-light |
| --sound-notification | --sound-duration-medium | OFF | --haptic-light |
| --sound-toggle | --sound-duration-short | OFF | --haptic-light |
| --sound-click | --sound-duration-short | OFF | none |
| --sound-upload-complete | --sound-duration-long | OFF | --haptic-medium |
| --sound-message | --sound-duration-short | OFF | --haptic-light |

| Token | Value |
| --- | --- |
| --sound-enabled | false |
| --sound-volume | 0.5 |
| --sound-duration-short | 120ms |
| --sound-duration-medium | 250ms |
| --sound-duration-long | 500ms |
| --sound-mute-user | true (user mute wins over everything) |
| --sound-mute-os | respected, read-only |
| --sound-motion-gate | prefers-reduced-motion silences non-essential events |

## Haptic tokens

| Token | Value | Use |
| --- | --- | --- |
| --haptic-enabled | false | Default off. |
| --haptic-light | 10ms | Toggles, chips. |
| --haptic-medium | 25ms | Success, send. |
| --haptic-heavy | 50ms | Errors, destructive confirm. |
| --haptic-selection | 8ms | Stepper ticks, slider notches. |

## Grid, layout, chrome tokens

| Token | Value | Use |
| --- | --- | --- |
| --grid-columns | 12 | Holy Grail main grid. |
| --grid-gutter | clamp(1rem, 3vw, 2rem) | Column gutter, fluid. |
| --grid-margin | clamp(1rem, 5vw, 3rem) | Page margin, fluid. |
| --grid-max-width | none | No fixed maximum; fluid system. |
| --measure-reading | clamp(45ch, 60ch, 75ch) | Reading measure. |
| --header-height | clamp(4rem, 8vh, 4.75rem) | Fixed header height. Tall enough for the 3 line logo lockup. |
| --sidebar-width-expanded | clamp(16rem, 20vw, 20rem) | Sidebar open. |
| --sidebar-width-collapsed | clamp(4rem, 5vw, 4.5rem) | Sidebar collapsed. |
| --sidebar-animation | var(--duration-normal) var(--ease-standard) | Slide in/out. |
| --footer-min-height | 3rem | Footer floor. |
| --scrollbar-width | 0.5rem | Scrollbar thumb. |
| --scrollbar-thumb | var(--color-border-strong) | Thumb rest. |
| --scrollbar-thumb-hover | var(--color-text-tertiary) | Thumb hover. |
| --scrollbar-track | transparent | Track. |
| --scrollbar-corner | var(--color-surface-sunken) | Corner. |

Glassmorphism tokens (rule 14), light and dark values in one table:

| Token | Light | Dark | Purpose |
| --- | --- | --- | --- |
| --glass-bg | var(--color-surface-base) at --opacity-glass-bg | var(--color-surface-base) at --opacity-glass-bg | Glass fill, translucent. |
| --glass-blur | 0.75rem | 0.75rem | Backdrop blur radius. |
| --glass-border | 1px solid var(--color-border) at --opacity-glass-border | 1px solid var(--color-border) at --opacity-glass-border | Hairline highlight edge. |
| --glass-shadow | var(--shadow-md) | var(--shadow-md) | Depth under glass. |
| --glass-saturate | saturate(180%) | saturate(180%) | Backdrop color boost. |
| --glass-inner-light | inset 0 1px 0 oklch(1 0 0 / 0.5) | inset 0 1px 0 oklch(0.99 0 0 / 0.08) | Subtle inner light edge. |
| --glass-fallback | var(--color-surface-raised) | var(--color-surface-raised) | Solid surface when blur or alpha unsupported, forced-colors, high contrast, reduced transparency. |

Glass is enhancement only: content must read with glass disabled, text contrast never drops below AA, and the fallback token replaces blur, alpha and saturate in one swap.

## Icon tokens (Lucide only)

| Token | Value | Use |
| --- | --- | --- |
| --icon-set | Lucide | Only free professional set allowed. |
| --icon-size-sm | 1rem | Inline icons. |
| --icon-size-md | 1.25rem | Buttons, nav. |
| --icon-size-lg | 1.5rem | Headings, empty states. |
| --icon-size-xl | 2rem | Illustrations. |
| --icon-stroke-thin | 1.5 | Default. |
| --icon-stroke-regular | 2 | Emphasis. |
| --icon-stroke-thick | 2.5 | Active. |
| --icon-gap | var(--space-2) | Icon-to-label gap. |

Icon source (single-file apps): Lucide UMD build from CDN, pinned: https://unpkg.com/lucide@1.73.0/dist/umd/lucide.min.js, then render icons from data attributes. Never draw icons by hand, never use emoji or other sets.

Icon policy: name by Lucide name, size by token, stroke by token, icon-only buttons need aria-label plus tooltip, icon never carries meaning alone without text or aria-label.

## Touch and pointer tokens

| Token | Value | Use |
| --- | --- | --- |
| --touch-target-min | 2.75rem | 44px minimum, every target. |
| --touch-target-comfort | 3rem | Preferred. |
| --pointer-fine | hover:hover and pointer:fine | Hover effects allowed. |
| --pointer-coarse | pointer:coarse | Enlarge targets, drop hover-only paths. |

## Logo tokens (rule 10, rule 25; full spec in brand/)

| Token | Value | Use |
| --- | --- | --- |
| --logo-font-family | "DejaVu Sans" | All three lines. |
| --logo-font-weight | 400 | Regular, all lines. |
| --logo-unit | u | Construction units, not px or mm; ratios only, never absolute sizes. |
| --logo-wordmark-size | clamp(1.25rem, 1rem + 0.8vw, 1.5rem) | Wordmark "INOVIX" in the header, nominal 100u. Larger lockups (login, print) override this token only. |
| --logo-descriptor-size | max(var(--logo-min-font-size), calc(var(--logo-wordmark-size) * 0.15)) | "SOFTWARE LABS", 15u ratio, never below the min font size. |
| --logo-tagline-size | max(var(--logo-min-font-size), calc(var(--logo-wordmark-size) * 0.12)) | Tagline, 12u ratio, never below the min font size. In a header lockup the floor wins, so the 100:15:12 ratio only holds on large lockups. Provisional, pending brand approval. |
| --logo-tagline-text | "Engineering Intelligence. Securing the Future." | Line 3 literal tagline; swap here for a white-label rebrand. |
| --logo-outline-weight | 0.011em | 1.1u stroke, scaled with size. |
| --logo-advance | 0.13em | Wordmark glyph advance, 13u after previous ink width. |
| --logo-layout-width | 336.56u | Full lockup width, construction only. |
| --logo-baseline-descriptor | -0.34em | Descriptor baseline, 34u below wordmark. |
| --logo-baseline-tagline | -0.63em | Tagline baseline, 63u below. |
| --logo-baseline-word | 0em | Wordmark baseline, lockup origin. |
| --logo-tracking | 0em | Base tracking; tagline uses normal spacing. |
| --logo-tracking-tight | -0.02em | Tight logotype tracking for dense lockups; provisional pending brand approval. |
| --logo-tracking-wide | 0.4em | Descriptor line tracking, custom-spaced to match wordmark width; provisional pending brand approval. |
| --logo-on-navy | oklch(0.99 0 0) | White on navy surfaces. |
| --logo-on-light | var(--color-navy-950) | Navy on light surfaces, anchor step. |
| --logo-clear-space | 1 x-height | Provisional, pending brand approval. |
| --logo-min-font-size | 0.625rem | 10px floor for descriptor and tagline. Provisional, pending brand approval. |
| --logo-touch-target | 2.75rem x 2.75rem | 44px square. |

Combo rule: on navy (header, dark theme, navy panels) all logo text is --logo-on-navy; on light or white surfaces all logo text is --logo-on-light. The swap is a token decision tied to theme plus surface, never a per-page guess.

## Chart tokens (series, per theme)

| Token | Light | Light sRGB | Dark | Dark sRGB |
| --- | --- | --- | --- | --- |
| --chart-1 | oklch(0.4 0.085 250) | #1F4A73 | oklch(0.53 0.085 250) | #446F9B |
| --chart-2 | oklch(0.72 0.15 65) | #E48E26 | oklch(0.85 0.15 65) | #FFBF81 |
| --chart-3 | oklch(0.62 0.12 180) | #039C89 | oklch(0.75 0.12 180) | #3DC6B1 |
| --chart-4 | oklch(0.55 0.17 30) | #C13E2E | oklch(0.68 0.17 30) | #EF6856 |
| --chart-5 | oklch(0.75 0.1 235) | #6AB8E4 | oklch(0.88 0.1 235) | #ACE0FE |
| --chart-6 | oklch(0.6 0.13 345) | #B55D92 | oklch(0.73 0.13 345) | #E185BA |
| --chart-7 | oklch(0.86 0.15 100) | #E8D34F | oklch(0.86 0.15 100) | #E8D34F |
| --chart-8 | oklch(0.5 0.03 250) | #576574 | oklch(0.63 0.03 250) | #7C8B9B |
| --chart-9 | oklch(0.52 0.15 290) | #6A55B8 | oklch(0.65 0.15 290) | #8F7CE3 |
| --chart-10 | oklch(0.66 0.13 130) | #77A246 | oklch(0.79 0.13 130) | #9FCB6F |
| --chart-11 | oklch(0.45 0.1 200) | #026266 | oklch(0.58 0.1 200) | #048B91 |
| --chart-12 | oklch(0.7 0.08 20) | #CC8B8A | oklch(0.83 0.08 20) | #F7B3B2 |

Series order is color-blind safe (blue, orange, teal, vermilion, sky, magenta, yellow, slate, then fills). Use series 1 to 4 first. Never rely on color alone: pair with markers, dash patterns or direct labels.

Chart rules: color-by-series only, never by category name; axis, grid, legend, tooltip and label colors come from surface/text/border tokens; dark/light swap is the token swap; print-friendly variants desaturate to grayscale tokens; empty/error/loading states use skeleton tokens.

## Contrast table (rule 28f)

Measured WCAG 2.x contrast ratios computed from the sRGB fallbacks above (generated by script, not estimated). Body text target AAA 7:1 where feasible, AA 4.5:1 minimum everywhere, UI components and focus indicators 3:1 minimum. Disabled text is exempt from WCAG contrast but must stay legible.

Light theme, text and indicators on surfaces (WCAG ratio, sRGB fallbacks):

| Foreground | surface-base | surface-raised | surface-sunken | surface-overlay | brand-soft | accent-soft |
| --- | --- | --- | --- | --- | --- | --- |
| --color-text-primary | 17.13 | 17.91 | 16.07 | 17.91 | 15.47 | 15.53 |
| --color-text-secondary | 8.75 | 9.15 | 8.21 | 9.15 | 7.90 | 7.93 |
| --color-text-tertiary | 6.00 | 6.28 | 5.63 | 6.28 | 5.42 | 5.44 |
| --color-accent | 5.84 | 6.11 | 5.48 | 6.11 | 5.27 | 5.29 |
| --color-error | 6.25 | 6.53 | 5.86 | 6.53 | 5.64 | 5.66 |
| --color-success | 5.94 | 6.21 | 5.57 | 6.21 | 5.36 | 5.38 |
| --color-info | 5.59 | 5.85 | 5.25 | 5.85 | 5.05 | 5.07 |
| --color-border-focus | 5.84 | 6.11 | 5.48 | 6.11 | 5.27 | 5.29 |

Light theme, content on filled surfaces:

| Fill | Content token | Ratio |
| --- | --- | --- |
| --color-primary | --color-primary-content | 17.46 |
| --color-accent | --color-accent-content | 5.95 |
| --color-secondary | --color-secondary-content | 8.96 |
| --color-error | --color-error-content | 6.37 |
| --color-success | --color-success-content | 6.05 |
| --color-warning | --color-warning-content | 7.91 |
| --color-info | --color-info-content | 5.70 |
| --color-header-bg | --color-header-text | 17.46 |

Dark theme, text and indicators on surfaces (WCAG ratio, sRGB fallbacks):

| Foreground | surface-base | surface-raised | surface-sunken | surface-overlay | brand-soft | accent-soft |
| --- | --- | --- | --- | --- | --- | --- |
| --color-text-primary | 16.58 | 14.17 | 17.16 | 12.59 | 11.61 | 11.61 |
| --color-text-secondary | 10.46 | 8.94 | 10.82 | 7.94 | 7.32 | 7.32 |
| --color-text-tertiary | 7.33 | 6.26 | 7.58 | 5.56 | 5.13 | 5.13 |
| --color-accent | 9.12 | 7.80 | 9.44 | 6.93 | 6.39 | 6.38 |
| --color-error | 7.37 | 6.30 | 7.63 | 5.60 | 5.16 | 5.16 |
| --color-success | 9.56 | 8.17 | 9.89 | 7.26 | 6.70 | 6.69 |
| --color-info | 9.23 | 7.89 | 9.54 | 7.01 | 6.46 | 6.46 |
| --color-border-focus | 9.85 | 8.41 | 10.18 | 7.48 | 6.89 | 6.89 |

Dark theme, content on filled surfaces:

| Fill | Content token | Ratio |
| --- | --- | --- |
| --color-primary | --color-primary-content | 9.12 |
| --color-accent | --color-accent-content | 9.12 |
| --color-secondary | --color-secondary-content | 9.62 |
| --color-error | --color-error-content | 7.37 |
| --color-success | --color-success-content | 9.56 |
| --color-warning | --color-warning-content | 10.68 |
| --color-info | --color-info-content | 9.23 |
| --color-header-bg | --color-header-text | 17.46 |

Reading the tables: text-primary and text-secondary pass AAA on every surface in both themes; text-tertiary, accent, semantic colors and the focus ring pass AA 4.5:1 on every surface they ship on in both themes (focus indicator needs only 3:1). Every filled surface pairs with its content token at 4.5:1 or better.

## White-label override section

A white-label rebrand swaps exactly these tokens; nothing else changes:

| Token | Swap to |
| --- | --- |
| --color-navy, --color-brand, --color-brand-strong, --color-primary | Client brand base, OKLCH. |
| --color-brand-content, --color-primary-content, --color-navy-content | Text on the new brand base. |
| --color-brand-soft | New brand tint fill. |
| --color-accent | Client accent. |
| --chart-1 through --chart-12 | Client series palette, both themes. |
| --logo-on-navy, --logo-on-light | Logo combo colors per surface. |
| --shadow-colored-brand, --shadow-colored-accent | Client-tinted elevation. |
| --glass-bg, --glass-border | Client glass tint. |
| --font-ui, --font-display | Client family stack (logo family stays DejaVu Sans per rule 10 unless the owner overrides the logo tokens too). |
| --color-navy-50 through --color-navy-975 | Client ramp, one hue, step 950 = brand base. Every other color token derives from it. |
| --color-header-bg, --color-header-text, --color-header-border | Header surface. |

Rule: one token file swap, full regenerate. Components must never reference a raw color; a rebrand that requires touching a component file is a token-design bug.

## Token naming conventions

- --color-*: colors, OKLCH, semantic names.
- --space-*: spacing, rem, 8px scale.
- --radius-*: corners, rem.
- --shadow-*: elevation, token-composed.
- --z-*: stacking, integers.
- --text-*, --leading-*, --tracking-*, --weight-*, --font-*: type.
- --duration-*, --ease-*, --stagger-*, --motion-*: motion.
- --bp-*: breakpoints.
- --cursor-*: cursors.
- --sound-*, --haptic-*: sound and haptics.
- --grid-*, --header-*, --sidebar-*, --footer-*, --scrollbar-*, --glass-*, --skeleton-*, --icon-*, --touch-*, --safe-*: structural.
- --logo-*: logo only.
- --chart-*: chart series.
- --opacity-*: alpha.

Every component file repeats this sentence verbatim in its Token usage section: "Token rule: every visual value in this component is a reference to a token in theme-variables.md; hardcoded values are forbidden."
