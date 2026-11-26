# INOVIX logo spec (source reference)

Source: "INOVIX-Logo-Blueprint-and-Specifications", 29 October 2026.

Mode: GENERATOR-only reference. The design system owner parses this in generator mode to build the design system. In consumer mode (a dev says "Follow this design system:" / "use this design system" / "design system:" and points at the design system directory) the AI MUST IGNORE this file, REQUIREMENTS.MD and any other generator spec: it uses ONLY the generated component MD files. See REQUIREMENTS.MD rule 26.

STALE on dark backgrounds: corrected 2026-11-14, verbatim: "dark bg is navy blue (i ddidnt update logo file i think)... combo is white / navy-blue and ofcurese logo is text only! no image!" The dark-bg sections below predate that correction and are SUPERSEDED by REQUIREMENTS.MD rule 10 + rule 25. This file is the raw source on disk; the generator reads REQUIREMENTS.MD, not this file.

## What the source spec actually says

- Logo is TEXT ONLY. Never an image, icon, or graphic mark. No SVG/PNG/JPG/WebP logo file anywhere.
- 3 lines: wordmark "INOVIX" / descriptor "SOFTWARE LABS" / tagline "Engineering Intelligence. Securing the Future.".
- Typeface: DejaVu Sans Regular (400) on all 3 lines.
- Units are construction units "u", not pixels or millimeters. Scale all geometry and strokes together.
- Geometry: wordmark 100 u nominal, outline 1.1 u, descriptor 15 u, tagline 12 u; wordmark glyph advance 13 u after previous glyph ink width; layout width 336.56 u; baselines: wordmark 0 u, descriptor -34 u, tagline -63 u; descriptor custom-spaced to match wordmark width; tagline normal spacing, centered by visible ink bounds.
- Colors: exactly two, white #FFFFFF and navy #03182D (source alpha 252/255 = 98.82%, solid preferred).
- Dark background = navy blue.

## Superseded by REQUIREMENTS.MD (do not use)

- Letter-split variants (white INOVI + navy X, or navy INOVI + white X, navy outlines, navy descriptor/tagline): transparent-bg print-style lockups, FAIL on a solid navy header. Superseded: no two-tone letter split, no navy outline, no navy descriptor or tagline on any navy surface.
- Any "logo mark", "wordmark lockup", or image-based logo reading: wrong, the logo is text only.

## Current combo rule (from REQUIREMENTS.MD rule 10)

- On navy (header, dark theme, navy panels): ALL logo text is white.
- On light or white surfaces: ALL logo text is navy.
- The swap is a token decision tied to theme + surface, never a per-page guess.

## Not approved in the source (provisional, flagged "pending brand approval" in REQUIREMENTS.MD)

- Clear-space, min-size, dark-background standards, print standards.
