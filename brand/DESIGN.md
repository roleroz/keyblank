# Keyblank design language

Direction: **Layout blue**. Version 1, 2026-11-10.

Keyblank cuts short-lived credentials to order for AI agents. The look comes from
the machine shop: metal coated in blue layout dye, with the cut scribed into it
before any material is removed. Everything is drawn like a part on a drawing
sheet: one blue, pale scribed lines, condensed capitals, square corners.

## Contents of this folder

```
DESIGN.md              this file
tokens/tokens.css      CSS custom properties, light and dark
tokens/tokens.json     the same values for any other language
logo/*.svg             vector logos (text is outlined, no font needed)
logo/favicon.ico       16, 32 and 48 px
logo/png/              raster exports
```

## Logo

The mark is a key blade seen from the side. The left half is still blank. The
right half has been cut. A dashed line shows where the blank edge used to be.

| File | Use |
|---|---|
| `keyblank-lockup-horizontal-*.svg` | Default. README header, docs header, web UI top bar |
| `keyblank-lockup-stacked-*.svg` | Square or tall spaces: splash, title page |
| `keyblank-mark-*.svg` | Where the name is already nearby |
| `keyblank-wordmark-*.svg` | Where the mark is already nearby |
| `keyblank-icon.svg` | App icon and repo avatar, 48 px and up |
| `favicon.svg`, `favicon.ico` | Browser tabs and anything under 48 px |
| `keyblank-social-preview.svg` | Repo social preview, 1280 x 640 |

Each logo comes in three colors:

| Suffix | Color | Put it on |
|---|---|---|
| `-blue` | Layout blue `#1E3F94` | Sheet, white, any light background |
| `-light` | Scribe `#E4ECF8` | Layout blue, ink, any dark background |
| `-ink` | Ink `#0F1E44` | One-color print or where blue is unavailable |

### Geometry

The mark sits on a 96 x 44 grid.

- The blank half is 44 wide. The cut half is 52 wide.
- There are four cuts. The first three are 12 wide and the last is 16. Their
  depths are 18, 8, 24 and 12.
- The dashed line runs along the original top edge of the cut half. It is 1.5
  thick with a 4 on, 4 off dash.
- The wordmark is IBM Plex Sans Condensed SemiBold in capitals, tracked 0.1 em.
  In the horizontal lockup its cap height is three quarters of the blade height
  and it sits on the blade's bottom edge.

The favicon is a separate drawing on a 16 px grid with three cuts and no dashed
line, so every edge lands on a pixel. Use it instead of shrinking the mark.

### Rules

- Clear space: keep one cut width (an eighth of the mark's width) free on every
  side. The SVG files already include a third of that as padding.
- Minimum size: 48 px wide for the mark, 120 px wide for the horizontal lockup.
  Below that, use the favicon.
- Only the three colors above. No gradients, outlines, shadows or rotation.
- Do not redraw the cuts, drop the dashed line from the full mark, or set the
  name in another typeface.

### In a README

```html
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="docs/brand/logo/keyblank-lockup-horizontal-light.svg">
  <img src="docs/brand/logo/keyblank-lockup-horizontal-blue.svg" alt="Keyblank" width="320">
</picture>
```

## Color

One hue does almost all the work. Blue is the brand, the ink is a darker blue,
and the neutrals are tinted blue.

| Token | Hex | Role |
|---|---|---|
| `blue` | `#1E3F94` | Layout blue. Brand surfaces, links and accents on light |
| `blueDeep` | `#16306F` | Code blocks, raised surfaces on dark |
| `ink` | `#0F1E44` | Body text on light, page background on dark |
| `muted` | `#4A5A80` | Secondary text on light |
| `rule` | `#B9C7E2` | 1 px rules and borders on light. Not for text |
| `scribe` | `#E4ECF8` | The logo on blue, tinted fills |
| `sheet` | `#F3F6FB` | Page background on light, body text on dark |
| `wash` | `#C9D7F2` | Secondary text on dark |
| `sky` | `#9DB8F0` | Accent on dark: prompts, links, highlights |

Credential states have their own colors. They are the only non-blue colors in
the system, so they stand out.

| State | On light | On dark |
|---|---|---|
| live | `#1F7A4D` | `#6FCF97` |
| expiring | `#8A5A00` | `#E5B454` |
| revoked | `#B3261E` | `#F59A90` |

The three state colors are close in lightness, so color alone will not separate
them for everyone. Always print the state word next to the color.

### Contrast

Measured WCAG contrast ratios. Body text needs 4.5.

| Text | Background | Ratio |
|---|---|---|
| ink | sheet | 15.0 |
| muted | sheet | 6.3 |
| blue | sheet | 8.8 |
| scribe | blue | 8.1 |
| sheet | blueDeep | 11.5 |
| wash | blueDeep | 8.6 |
| sky | blueDeep | 6.3 |
| sky | ink | 8.2 |
| live, expiring, revoked (light values) | sheet | 4.9, 5.5, 6.0 |
| live, expiring, revoked (dark values) | blueDeep | 6.6, 6.5, 5.9 |
| live, expiring, revoked (dark values) | ink | 8.6, 8.5, 7.7 |

## Type

| Family | Use |
|---|---|
| IBM Plex Sans Condensed | Headings, labels, UI text, body |
| IBM Plex Mono | Commands, output, code, hex values, anything a terminal prints |

- Weights: 400 for body, 500 for emphasis, 600 for headings and the wordmark.
- Titles and small labels are uppercase and tracked 0.08 em, like the title
  block on a drawing. Body text is sentence case with no extra tracking.
- Only the wordmark uses 0.1 em tracking.
- Sizes in px: 12, 14, 17, 22, 30, 44. Body is 17 because the condensed face
  reads small.

Both families are open source (SIL Open Font License). Load them from Google
Fonts, or self-host with the `@fontsource/ibm-plex-sans-condensed` and
`@fontsource/ibm-plex-mono` packages:

```html
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Condensed:wght@400;500;600&family=IBM+Plex+Mono:wght@400;500;600&display=swap">
```

## Shape and layout

- Spacing is on a 4 px grid: 4, 8, 12, 16, 24, 32, 48.
- Corners are square. The largest radius anywhere is 2 px.
- Separate things with 1 px rules in `rule`, not with shadows or filled cards.
- No gradients and no drop shadows.
- Flat blue panels are the one large-area color. Use them for headers and
  title pages, not behind body text.

Two motifs from the logo can be reused:

- **Dimension line.** A thin line with a tick at each end and at each division,
  as on the social preview. Use it to label a span: a TTL, a section, a range.
- **Dashed edge.** A dashed line means "this is where it was" or "not cut yet".
  Use it for pending grants, expired credentials and empty states. Do not use
  dashes as plain decoration.

## Terminal

The CLI is where Keyblank is seen most, so it follows the same rules.

Command names are not decided yet. These rules cover how output looks, whatever
the commands end up being called.

### Output

A listing of live credentials would look like this:

```
agent-07   ssh nas         live       24m left
agent-03   github repo     expiring    2m left
```

- Lowercase, no punctuation at line ends, no emoji, no banners or box drawing.
- One credential per line, in aligned columns, so the output can be piped to
  `awk` or `cut`.
- A confirmation line starts with what happened, in the past tense.
- Never print a secret value unless the command exists to print it.
- Errors go to stderr, start with `keyblank:` and name the next step.

### Terminal colors

Use 24-bit color where the terminal supports it and the 256-color fallback
otherwise. Honor `NO_COLOR` and turn color off when stdout is not a terminal.

| Element | Hex | 256-color |
|---|---|---|
| Prompt and headings | `#9DB8F0` | 111 |
| Secondary detail | `#C9D7F2` | 189 |
| live | `#6FCF97` | 114 |
| expiring | `#E5B454` | 179 |
| revoked | `#F59A90` | 210 |

Primary text uses the terminal's own foreground color. Do not set a background.

## Writing

- The name is **Keyblank** in prose and `keyblank` in code. The wordmark is the
  only place it appears in capitals.
- Write short sentences with exact numbers: "expires in 30 minutes", not
  "expires soon".
- Tagline, where one is needed: "Credentials cut to order."
