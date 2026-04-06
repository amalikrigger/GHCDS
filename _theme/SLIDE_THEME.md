# GHCDS Slide Theme Guide

All PowerPoints for this course should follow these rules so every deck looks like part of the same class.

---

## Color Palette

| Role | Color | Hex | Usage |
|---|---|---|---|
| Primary Dark | Navy | `1E2761` | Title slides, dark backgrounds, headings |
| Primary Accent | Purple | `764BA2` | Accent shapes, decorative circles |
| Secondary Accent | Blue | `667EEA` | Links, secondary accents, circle badges |
| Light Background | Off-White | `F0F0FF` | Content slide backgrounds |
| Card Background | White | `FFFFFF` | Content cards, tables |
| Light Accent | Ice Blue | `CADCFC` | Subtitles, muted text on dark backgrounds |
| Success | Green | `10B981` | Positive indicators, terminal prompts |
| Warning | Yellow | `F59E0B` | Caution items |
| Danger | Red | `EF4444` | Critical items |
| Body Text | Dark Slate | `1E293B` | Paragraph text on light backgrounds |
| Muted Text | Gray | `64748B` | Captions, footnotes |

---

## Fonts

| Element | Font | Size | Weight |
|---|---|---|---|
| Slide title | Trebuchet MS | 32-42pt | Bold |
| Card/section header | Calibri | 16-18pt | Bold |
| Body text | Calibri | 13-14pt | Regular |
| Code snippets | Consolas | 10-14pt | Regular |
| Captions/footnotes | Calibri | 10-12pt | Regular, italic |
| Subtitles | Calibri | 14-18pt | Italic |

---

## Slide Structure

Every deck follows this pattern:

1. **Title Slide** — Navy background, decorative purple + blue circles (top-right, bottom-left), big bold title, italic subtitle, "Computer Science & Robotics | Grades 7-12" footer
2. **Content Slides** — Off-white background (`F0F0FF`), white cards with subtle shadows, colored top-bar accents on cards
3. **Code Slides** — Dark background (`1E1E1E`) for terminal/code mockups with green prompt text and white commands
4. **Vocabulary Slide** — Table with navy header row, alternating white/light purple rows
5. **Closing Slide** — Navy background with decorative circles, numbered roadmap or key takeaways

---

## Card Style

All content cards use:
- Background: white (`FFFFFF`)
- Shadow: `type: outer, blur: 6, offset: 2, angle: 135, color: 000000, opacity: 0.15`
- Colored top bar: 0.06-0.08" tall rectangle at the top of the card in an accent color
- No rounded corners (use `RECTANGLE`, not `ROUNDED_RECTANGLE`)

---

## Layout Rules

- 0.8" left margin for titles and content
- 0.5" minimum from all slide edges
- Cards arranged in grids (2-4 columns) with 0.3" gaps
- Arrows between flow items use `→` character in gray (`64748B`), 24-28pt
- Decorative circles use `OVAL` shape with 50-60% transparency

---

## Slide Backgrounds

| Slide Type | Background |
|---|---|
| Title | Navy (`1E2761`) |
| Content | Off-White (`F0F0FF`) |
| Code/Terminal | Dark (`1E1E1E`) or Navy (`1E2761`) |
| Key Concept / Emphasis | Navy (`1E2761`) |
| Vocabulary | Off-White (`F0F0FF`) |
| Closing | Navy (`1E2761`) |

---

## Terminal Mockup Style

When showing terminal/command line content:
- Background: `1E1E1E`
- Prompt (`$` or `pi@raspberrypi:~ $`): Green (`10B981`)
- Commands: White (`FFFFFF`)
- Output: Ice Blue (`CADCFC`)
- Dimmed text (passwords, etc.): Gray (`64748B`)
- Font: Consolas, 13-14pt

---

## Do NOT

- Use accent lines under titles
- Use Tailwind or external CDN references in slides
- Use `#` prefix in hex colors (PptxGenJS will break)
- Reuse shadow/option objects across multiple shapes
- Use different color palettes per deck — always use this palette
- Default to bullet-heavy text slides — every slide needs a visual element
