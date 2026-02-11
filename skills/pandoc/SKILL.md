---
name: pandoc
description: 'Universal document converter supporting 40+ input formats and 60+ output formats. Use when converting between Markdown, HTML, LaTeX, Word (docx), PDF, EPUB, PowerPoint (pptx), reStructuredText, Org mode, and more. Supports citations, bibliographies, templates, syntax highlighting, math equations, presentations, and academic writing. Triggers: document conversion, format transformation, Markdown to PDF, create EPUB, generate slides, academic papers, cross-format documentation.'
---

# Pandoc Document Converter

A comprehensive toolkit for converting documents between formats using Pandoc, the universal document converter. Pandoc can convert between markup formats, word processing formats, ebooks, presentations, and PDFs while preserving structure and metadata.

## When to Use This Skill

Use this skill when:
- Converting documents between formats (e.g., Markdown → PDF, docx → HTML)
- Creating PDFs from Markdown, LaTeX, or HTML
- Generating presentations (reveal.js, Beamer, PowerPoint)
- Building EPUB ebooks from Markdown
- Writing academic papers with citations and bibliographies
- Creating multi-format documentation from a single source
- Converting between markup languages (Markdown, reStructuredText, Org mode, AsciiDoc)
- Generating Word documents with custom styles
- Creating standalone HTML files with embedded resources

## Prerequisites

**Required:**
- Pandoc installed (user confirmed: already installed)
- Check version: `pandoc --version`

**Optional (for specific features):**
- **PDF generation:** LaTeX distribution (TeX Live, MiKTeX) or alternative engines (wkhtmltopdf, WeasyPrint, Prince)
- **Citations:** BibTeX/BibLaTeX files or CSL JSON/YAML bibliographies
- **Custom templates:** Template files in Pandoc's template language
- **Filters:** Lua scripts or executables for custom transformations

## Core Command Patterns

### Basic Conversion

```powershell
# Pattern: Input → Output
pandoc input.md -o output.html
pandoc input.md -o output.pdf
pandoc input.docx -o output.md

# Explicit format specification
pandoc -f markdown -t html input.md -o output.html
pandoc -f html -t markdown input.html -o output.md
```

### Standalone Documents

```powershell
# Create complete HTML document (with <head>, <body>)
pandoc -s input.md -o output.html

# Standalone document with custom template
pandoc -s --template=custom.html input.md -o output.html

# List available templates
pandoc -D html
pandoc -D latex
```

### Multiple Inputs

```powershell
# Concatenate multiple files (separated by blank lines)
pandoc chapter1.md chapter2.md chapter3.md -o book.pdf

# Parse files individually
pandoc --file-scope chapter1.md chapter2.md -o book.pdf
```

## Format Support

### Input Formats (Partial List)

| Format | Extension | Usage |
|--------|-----------|-------|
| **Markdown** | `.md`, `.markdown` | `pandoc -f markdown` (default) |
| **Word** | `.docx` | `pandoc -f docx` |
| **HTML** | `.html` | `pandoc -f html` |
| **LaTeX** | `.tex` | `pandoc -f latex` |
| **reStructuredText** | `.rst` | `pandoc -f rst` |
| **Org mode** | `.org` | `pandoc -f org` |
| **EPUB** | `.epub` | `pandoc -f epub` |
| **Jupyter** | `.ipynb` | `pandoc -f ipynb` |
| **MediaWiki** | | `pandoc -f mediawiki` |
| **DocBook** | `.xml` | `pandoc -f docbook` |

Full list: `pandoc --list-input-formats`

### Output Formats (Partial List)

| Format | Extension | Usage |
|--------|-----------|-------|
| **HTML5** | `.html` | `pandoc -t html` |
| **PDF** | `.pdf` | `pandoc -o output.pdf` |
| **Word** | `.docx` | `pandoc -t docx` |
| **LaTeX** | `.tex` | `pandoc -t latex` |
| **EPUB3** | `.epub` | `pandoc -t epub` |
| **PowerPoint** | `.pptx` | `pandoc -t pptx` |
| **Beamer** | `.pdf` | `pandoc -t beamer -o slides.pdf` |
| **reveal.js** | `.html` | `pandoc -t revealjs -s` |
| **reStructuredText** | `.rst` | `pandoc -t rst` |
| **Markdown** | `.md` | `pandoc -t markdown` |

Full list: `pandoc --list-output-formats`

## Common Workflows

### 1. Markdown to PDF

```powershell
# Basic conversion (requires LaTeX)
pandoc document.md -o document.pdf

# With table of contents
pandoc document.md --toc -o document.pdf

# Custom margins and font
pandoc document.md -o document.pdf `
  -V geometry:margin=1in `
  -V fontsize=12pt

# Different PDF engine
pandoc document.md -o document.pdf --pdf-engine=xelatex
pandoc document.md -o document.pdf --pdf-engine=lualatex

# HTML → PDF (no LaTeX needed)
pandoc document.md -t html -o document.pdf --pdf-engine=weasyprint
```

### 2. Creating Presentations

#### reveal.js (HTML Slides)

```powershell
# Standalone presentation
pandoc slides.md -t revealjs -s -o slides.html

# With theme
pandoc slides.md -t revealjs -s -o slides.html `
  -V theme=moon

# Self-contained (embed all resources)
pandoc slides.md -t revealjs -s -o slides.html --embed-resources

# Incremental lists
pandoc slides.md -t revealjs -s -o slides.html -i
```

#### Beamer (LaTeX/PDF Slides)

```powershell
# Create Beamer presentation
pandoc slides.md -t beamer -o slides.pdf

# With theme
pandoc slides.md -t beamer -o slides.pdf `
  -V theme:metropolis
```

#### PowerPoint

```powershell
# Create PowerPoint presentation
pandoc slides.md -o presentation.pptx

# Custom reference template
pandoc slides.md -o presentation.pptx `
  --reference-doc=custom-template.pptx
```

**Slide delimiters:**
```markdown
# Title

## Slide 1

Content here.

## Slide 2

More content.
```

### 3. Academic Writing with Citations

```powershell
# Enable citation processing
pandoc paper.md --citeproc -o paper.pdf

# With bibliography file
pandoc paper.md --citeproc --bibliography=refs.bib -o paper.pdf

# Custom citation style (CSL)
pandoc paper.md --citeproc `
  --bibliography=refs.bib `
  --csl=apa.csl `
  -o paper.pdf

# Multiple bibliography files
pandoc paper.md --citeproc `
  --bibliography=refs1.bib `
  --bibliography=refs2.bib `
  -o paper.pdf
```

**Citation syntax in Markdown:**
```markdown
Blah blah [@smith2020, p. 33].

According to @jones2019 [pp. 10-15], ...

Multiple sources [@smith2020; @jones2019].
```

### 4. Creating EPUB Ebooks

```powershell
# Basic EPUB
pandoc book.md -o book.epub

# With metadata
pandoc book.md -o book.epub `
  --metadata title="My Book" `
  --metadata author="Your Name"

# With cover image
pandoc book.md -o book.epub `
  --epub-cover-image=cover.jpg

# Custom CSS
pandoc book.md -o book.epub --css=custom.css

# EPUB metadata file
pandoc book.md -o book.epub --epub-metadata=metadata.xml
```

### 5. Word Document Generation

```powershell
# Create Word document
pandoc document.md -o document.docx

# Custom reference document (for styles)
pandoc document.md -o document.docx `
  --reference-doc=custom-reference.docx

# Get default reference document
pandoc -o custom-reference.docx `
  --print-default-data-file reference.docx
```

### 6. Self-Contained HTML

```powershell
# Embed all images, CSS, JavaScript
pandoc document.md -s -o document.html --embed-resources

# With custom CSS
pandoc document.md -s -o document.html `
  --embed-resources `
  --css=custom.css

# With syntax highlighting
pandoc document.md -s -o document.html `
  --embed-resources `
  --syntax-highlighting=kate
```

### 7. Multi-File Projects

```powershell
# Book with chapters
pandoc metadata.yaml chapter*.md references.md `
  -o book.pdf `
  --toc `
  --number-sections

# With defaults file
pandoc -d myproject.yaml

# Metadata in separate file
pandoc document.md --metadata-file=metadata.yaml -o output.pdf
```

## Advanced Features

### Templates and Variables

```powershell
# Set template variables
pandoc document.md -o output.html `
  -V title="My Title" `
  -V author="Author Name" `
  -V date="2024-03-15"

# Custom template
pandoc document.md -s --template=mytemplate.html -o output.html

# Print default template
pandoc -D html > mytemplate.html
pandoc -D latex > mytemplate.tex
```

### Syntax Highlighting

```powershell
# List available styles
pandoc --list-highlight-styles

# Set highlighting style
pandoc document.md -o output.html --syntax-highlighting=pygments
pandoc document.md -o output.html --syntax-highlighting=kate

# Generate custom theme
pandoc -o custom.theme --print-highlight-style=pygments

# Use custom theme
pandoc document.md -o output.html --syntax-highlighting=custom.theme

# Disable highlighting
pandoc document.md -o output.html --syntax-highlighting=none
```

### Filters and Transformations

```powershell
# Lua filter
pandoc document.md -o output.html --lua-filter=filter.lua

# JSON filter (executable)
pandoc document.md -o output.html --filter=myfilter

# Multiple filters (applied in order)
pandoc document.md -o output.html `
  --filter=filter1 `
  --lua-filter=filter2.lua `
  --citeproc
```

### Math Support

```powershell
# HTML with MathJax
pandoc math.md -s -o math.html --mathjax

# HTML with KaTeX
pandoc math.md -s -o math.html --katex

# LaTeX/PDF (native support)
pandoc math.md -o math.pdf
```

**Math syntax:**
```markdown
Inline math: $E = mc^2$

Display math:
$$
\int_0^\infty e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
$$
```

### Table of Contents

```powershell
# Add TOC
pandoc document.md --toc -o output.html

# TOC with custom depth
pandoc document.md --toc --toc-depth=2 -o output.pdf

# Numbered sections
pandoc document.md --number-sections -o output.pdf

# Both TOC and numbering
pandoc document.md --toc --number-sections -o output.pdf
```

### Defaults Files

Create `myproject.yaml`:

```yaml
from: markdown
to: html
standalone: true
toc: true
number-sections: true
syntax-highlighting: kate
variables:
  title: "My Project"
  author: "Author Name"
css:
  - styles.css
```

Use it:

```powershell
pandoc document.md -d myproject.yaml -o output.html

# Override specific options
pandoc document.md -d myproject.yaml -o output.pdf
```

## Markdown Extensions

Pandoc extends standard Markdown with many features:

### Tables

```markdown
| Right | Left | Center | Default |
|------:|:-----|:------:|---------|
|   12  | 12   |   12   | 12      |
|  123  | 123  |  123   | 123     |
|    1  | 1    |    1   | 1       |

: Table caption
```

### Fenced Divs and Spans

```markdown
::: {.warning}
This is a warning box.
:::

[Small caps text]{.smallcaps}

[Underlined text]{.underline}
```

### Footnotes

```markdown
Here is a footnote reference.[^1]

[^1]: This is the footnote.
```

### Definition Lists

```markdown
Term 1
:   Definition 1

Term 2
:   Definition 2a
:   Definition 2b
```

### Inline Formatting

```markdown
**bold** *italic* ~~strikethrough~~

H~2~O (subscript)
2^10^ (superscript)

`verbatim code`
```

## PDF Engines

| Engine | Command | Use Case |
|--------|---------|----------|
| **pdflatex** | `--pdf-engine=pdflatex` | Default, standard LaTeX |
| **xelatex** | `--pdf-engine=xelatex` | Unicode, system fonts |
| **lualatex** | `--pdf-engine=lualatex` | Lua scripting, advanced features |
| **latexmk** | `--pdf-engine=latexmk` | Automatic recompilation |
| **tectonic** | `--pdf-engine=tectonic` | Modern LaTeX, auto-downloads packages |
| **wkhtmltopdf** | `--pdf-engine=wkhtmltopdf` | HTML → PDF (no LaTeX) |
| **weasyprint** | `--pdf-engine=weasyprint` | HTML → PDF, CSS Paged Media |
| **prince** | `--pdf-engine=prince` | HTML → PDF, commercial |
| **context** | `--pdf-engine=context` | ConTeXt typesetting |
| **typst** | `--pdf-engine=typst` | Modern typesetting system |

## Troubleshooting

### "pandoc: command not found"

**Windows (PowerShell):**
```powershell
# Check if Pandoc is in PATH
$env:PATH -split ';' | Select-String pandoc

# Find Pandoc installation
Get-Command pandoc

# If not found, download from https://pandoc.org/installing.html
```

### PDF Generation Fails

```powershell
# Check LaTeX installation
pdflatex --version
xelatex --version

# Use alternative engine (no LaTeX required)
pandoc document.md -o document.pdf --pdf-engine=weasyprint

# Debug: generate LaTeX intermediate
pandoc document.md -s -o document.tex
```

### Unicode Characters Not Displaying

```powershell
# Use xelatex or lualatex
pandoc document.md -o document.pdf --pdf-engine=xelatex

# Specify font that supports Unicode
pandoc document.md -o document.pdf `
  --pdf-engine=xelatex `
  -V mainfont="DejaVu Sans"
```

### Images Not Found

```powershell
# Use absolute paths or ensure relative paths are correct
pandoc document.md -o output.pdf

# Specify resource path
pandoc document.md -o output.pdf --resource-path=.:images:assets

# Extract embedded images from docx
pandoc input.docx --extract-media=media -o output.md
```

### Citations Not Working

```powershell
# Ensure --citeproc is specified
pandoc paper.md --citeproc --bibliography=refs.bib -o paper.pdf

# Check bibliography file format
# Supported: .bib (BibTeX), .json (CSL JSON), .yaml (CSL YAML)

# Debug citations
pandoc paper.md --citeproc --bibliography=refs.bib -t native
```

### Custom Styles Not Applied (Word)

```powershell
# Create reference document from Pandoc's default
pandoc -o custom-reference.docx --print-default-data-file reference.docx

# Edit styles in Word (don't modify structure)
# Use it:
pandoc document.md -o output.docx --reference-doc=custom-reference.docx
```

## Quick Reference: Common Conversions

### Markdown → Formats

```powershell
# HTML
pandoc doc.md -s -o doc.html

# PDF
pandoc doc.md -o doc.pdf

# Word
pandoc doc.md -o doc.docx

# EPUB
pandoc doc.md -o doc.epub

# LaTeX
pandoc doc.md -s -o doc.tex

# reveal.js slides
pandoc slides.md -t revealjs -s -o slides.html
```

### Other Formats → Markdown

```powershell
# Word → Markdown
pandoc doc.docx -o doc.md

# HTML → Markdown
pandoc page.html -o page.md

# LaTeX → Markdown
pandoc doc.tex -o doc.md

# EPUB → Markdown
pandoc book.epub -o book.md
```

### Format → Format

```powershell
# HTML → PDF
pandoc page.html -o page.pdf

# Word → HTML
pandoc doc.docx -s -o doc.html

# LaTeX → Word
pandoc doc.tex -o doc.docx

# reStructuredText → HTML
pandoc doc.rst -s -o doc.html
```

## Command-Line Options Reference

### Frequently Used Options

| Option | Purpose | Example |
|--------|---------|---------|
| `-o FILE` | Output file | `pandoc doc.md -o doc.pdf` |
| `-s, --standalone` | Complete document | `pandoc -s doc.md -o doc.html` |
| `-f FORMAT` | Input format | `pandoc -f html -t markdown` |
| `-t FORMAT` | Output format | `pandoc -t latex doc.md` |
| `--toc` | Table of contents | `pandoc --toc doc.md -o doc.pdf` |
| `--toc-depth=N` | TOC depth | `pandoc --toc --toc-depth=2` |
| `--number-sections` | Number headings | `pandoc --number-sections` |
| `-V KEY=VAL` | Set variable | `pandoc -V title="My Doc"` |
| `--metadata=KEY:VAL` | Set metadata | `pandoc --metadata author="Name"` |
| `--template=FILE` | Custom template | `pandoc --template=custom.html` |
| `--css=FILE` | CSS stylesheet | `pandoc --css=style.css` |
| `--pdf-engine=ENGINE` | PDF engine | `pandoc --pdf-engine=xelatex` |
| `--citeproc` | Process citations | `pandoc --citeproc --bibliography=refs.bib` |
| `--bibliography=FILE` | Bibliography | `pandoc --bibliography=refs.bib` |
| `--csl=FILE` | Citation style | `pandoc --csl=apa.csl` |
| `--syntax-highlighting=STYLE` | Code highlighting | `pandoc --syntax-highlighting=kate` |
| `--embed-resources` | Self-contained | `pandoc --embed-resources` |
| `--lua-filter=FILE` | Lua filter | `pandoc --lua-filter=filter.lua` |
| `--reference-doc=FILE` | Style reference | `pandoc --reference-doc=ref.docx` |
| `-d FILE` | Defaults file | `pandoc -d project.yaml` |

### List Commands

```powershell
# List supported input formats
pandoc --list-input-formats

# List supported output formats
pandoc --list-output-formats

# List supported extensions for a format
pandoc --list-extensions=markdown

# List syntax highlighting styles
pandoc --list-highlight-styles

# List syntax highlighting languages
pandoc --list-highlight-languages
```

### Print Defaults

```powershell
# Print default template
pandoc -D html
pandoc -D latex
pandoc -D epub

# Print default data file
pandoc --print-default-data-file reference.docx
pandoc --print-default-data-file reference.odt
pandoc --print-default-data-file epub.css

# Print highlight style as JSON
pandoc --print-highlight-style=pygments > custom.theme
```

## Resources

- **Official Documentation:** <https://pandoc.org/MANUAL.html>
- **Installation:** <https://pandoc.org/installing.html>
- **Demos:** <https://pandoc.org/demos.html>
- **Lua Filters:** <https://pandoc.org/lua-filters.html>
- **Templates:** <https://github.com/jgm/pandoc-templates>
- **User Contributions:** <https://github.com/jgm/pandoc/wiki/User-contributed-templates>
- **Citation Styles:** <https://www.zotero.org/styles>
- **CSL Documentation:** <https://citationstyles.org/>

## Version Information

This skill covers Pandoc version 2.x and 3.x features. Check your version:

```powershell
pandoc --version
```
