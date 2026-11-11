# Jordi Montornés CV source

The CV is authored as a fixed two-page A4 HTML document and rendered to PDF with **WeasyPrint 68.0**.

## Files

- `cv.html` — source and all CSS styling.
- `generate.sh` — builds the PDF.
- `requirements.txt` — pins the WeasyPrint version used for the original PDF.

## Setup on Linux Mint

A Python virtual environment is recommended:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
```

If `venv` is not installed:

```bash
sudo apt install python3-venv
```

## Generate the PDF

```bash
./generate.sh
```

or directly:

```bash
weasyprint cv.html Jordi_Montornes_CV.pdf
```

## Editing

All design is contained near the top of `cv.html` in the `<style>` section.

Useful selectors:

- `.header` — dark top header and its padding.
- `.name` — candidate name.
- `.role` — subtitle below the name.
- `.content` — page margins/padding below the header.
- `.section-title` — section headings and divider line.
- `.expertise-grid` — 2-column expertise cards.
- `.expertise` — expertise card appearance.
- `.job-title`, `.job-date`, `.company` — experience headings.
- `li` — experience bullet typography and spacing.
- `.two-col` — two-column lower half of page 2.

The page size is fixed by:

```css
@page { size: A4; margin: 0; }
.page { width:210mm; height:297mm; overflow:hidden; }
```

Because the layout is explicitly constrained to two pages, if you add substantial text it may be clipped rather than automatically creating a third page. If that happens, reduce content or spacing, or remove `height:297mm` / `overflow:hidden` while editing to diagnose the overflow.

## Colors

The main palette currently uses:

- Header / primary text: `#17324d`
- Accent blue: `#5f9fb8`
- Divider blue: `#8fb7c9`
- Expertise background: `#f4f8fa`
- Main body text: `#1f2933`

## Reproducibility

The original PDF was rendered with WeasyPrint 68.0. Keeping the pinned version in `requirements.txt` should make future renders closely match the original.
