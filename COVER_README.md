# LaTeX Cover Implementation

This directory contains LaTeX implementations that mimic the design of `cover2.pdf`.

## Files Created

### 1. `cover_standalone.tex`
**Complete standalone document** - Most faithful reproduction of the PDF.
- Compile directly with: `pdflatex cover_standalone.tex`
- Produces a single-page cover in A4 format
- Uses TikZ for precise positioning

### 2. `FrontBackMatter/cover_page.tex`
**Reusable macro** - For integration into existing documents.
- Include in your main document's preamble
- Call `\makecover` where you want the cover to appear
- Requires TikZ, xcolor, and graphicx packages

### 3. `cover.tex`
**Basic version** - Simplified alternative.

## Color Specification

- **Red color**: RGB(153, 0, 0) - defined as `\definecolor{coverred}{RGB}{153,0,0}`

## Logo Placement

The cover requires three logo images:

1. **logo1.png** - Top left corner (e.g., UAB logo)
2. **logo2.png** - Top right corner (e.g., CREAF logo)
3. **logo3.png** - Center (main circular emblem)

### Expected Logo Locations

Place your logo files in one of these locations:
- `Figures/cover/logo1.png`
- `Figures/cover/logo2.png`
- `Figures/cover/logo3.png`

Or update the paths in the `.tex` files accordingly.

## Design Elements

The cover includes:
- **Red header bar** (2.5cm height) with university name in white
- **Red footer bar** (2cm height) with author info in white
- **White middle section** with:
  - Three logos positioned strategically
  - Faculty and department information
  - Main title in red (customizable)
  - Subtitle/description
- **Optional decorative lines** (can be removed if not in original)

## Customization

Edit these sections in the files:

1. **Header text** - Line ~67 (university name)
2. **Department info** - Lines ~72-77
3. **Main title** - Lines ~88-93
4. **Author & footer info** - Lines ~99-107

## Usage with Main Document

To integrate into your existing `tfm.tex`:

```latex
\documentclass{...}

% Add required packages
\usepackage{tikz}
\usepackage{xcolor}
\usepackage{graphicx}

% Include the cover macro
\input{FrontBackMatter/cover_page.tex}

\begin{document}

% Generate the cover
\makecover

% Rest of your document
...

\end{document}
```

## Compilation

Standard LaTeX compilation:
```bash
pdflatex cover_standalone.tex
pdflatex cover_standalone.tex  # Compile twice for TikZ positioning
```

Or with your main document:
```bash
pdflatex tfm.tex
```

## Notes

- The design uses TikZ's `remember picture, overlay` for absolute positioning
- Sans-serif font (Helvetica/helvet) is used throughout
- All measurements are approximate and can be fine-tuned
- If logos appear too large/small, adjust the `height=` or `width=` parameters
- Page margins are set to 0 for full bleed coverage

## Troubleshooting

**Logo not found**: Update the path to your logo files in the `.tex` file.

**Positioning off**: Adjust `xshift` and `yshift` values in the `\node` commands.

**Font issues**: Install the `helvet` LaTeX package or use another sans-serif font.

**Colors don't match**: Verify RGB values and color space (RGB vs CMYK).
