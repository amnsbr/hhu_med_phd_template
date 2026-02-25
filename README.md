This repository is a LaTeX thesis template for cumulative PhD theses in the style used by the Faculty of Medicine at Heinrich Heine University Düsseldorf.

The top-level file is `main.tex`. Most of the writing happens in the chapter `.tex` files inside the subfolders. The template is currently filled with placeholder text using `\lipsum`. Replace `\lipsum` commands with your own text.

Loosely adapted from: https://www.overleaf.com/latex/templates/phd-thesis-template/kbqspqtswjqx

> **Note:** This template is based on faculty/thesis guidelines available as of **February 2026**.  
> Official requirements can change, so always check the latest guidelines and updates yourself.

## Usage

1. Update personal metadata in `frontmatter/titlepage.tex`.
2. Replace placeholder text in all front matter files under `frontmatter/`.
3. Add/clean your references in `example.bib` (rename it and update `\addbibresource{...}` in `main.tex`). See below for more details.
4. Write your chapter text in:
   - `intro/intro.tex`
   - `discussion/discussion.tex`
   - `ackn/ackn.tex`
5. Update study information in:
   - `study1/study1.tex`
   - `study2/study2.tex`
   - `study3/study3.tex`
   - It is also possible to add more studies by adding more subfolders and updating `main.tex`.
6. Add publication PDFs. Note that for both submission and printing, the publication PDFs are not included in the thesis PDF. To include them, uncomment the `\usepackage{pdfpages}` line in `main.tex` and comment out the `\usepackage[demo]{pdfpages}` line. Otherwise, `\usepackage[demo]{pdfpages}` is used to render empty placeholders instead of full PDFs.
   - `study1/study1.pdf`
   - `study2/study2.pdf`
   - `study3/study3.pdf`
   - It is also possible to add more studies by adding more subfolders and updating `main.tex`.
7. Update chapter titles in `main.tex` (for example `\chapter{Study 1: Title}`).
8. Compile into PDF (e.g. using overleaf or any other LaTeX editor).

## Project structure and where content goes

### `main.tex`

Use `main.tex` to control:
- Package configuration and global layout,
- Chapter order,
- Chapter titles and labels,
- Inclusion of study PDFs,
- Bibliography and acknowledgment placement.

### Front matter (`frontmatter/`)

- `frontmatter/titlepage.tex`: Thesis title, your name, formal title, year.
- `frontmatter/committee.tex`: Defense committee details. This page is for the printed library version after defense, and is omitted for submission (comment it out in `main.tex`).
- `frontmatter/dedications.tex`: Optional dedication or quote.
- `frontmatter/publications.tex`: List of included publications (journal papers/manuscripts).
- `frontmatter/zusammenfassung.tex`: German abstract.
- `frontmatter/abstract.tex`: English abstract.
- `frontmatter/abbreviations.tex`: List of abbreviations.

### Main text chapters

- `intro/intro.tex`: Introduction, ethics approval, and aims of the thesis.
- `study1/study1.tex`, `study2/study2.tex`, `study3/study3.tex`: Bibliographic information and own contribution for each study. I also included impact factor of the journal, but that is not required.
- `discussion/discussion.tex`: Discussion.

### Back matter

- `ackn/ackn.tex`: Acknowledgments.
- Bibliography is generated from the `.bib` resource defined in `main.tex`.

## Citations and bibliography (`example.bib`)

`main.tex` currently loads:
- `\usepackage[backend=biber,style=apa]{biblatex}`
- `\addbibresource{example.bib}`

It also defines a temporary citation command `\citetemp{...}` that can be used while drafting the text, and can later be replaced with `\cite{...}` once references are ready. `\citetemp{...}` simply puts a placeholder in the text and does not add a citation to the bibliography.

Recommended workflow:
1. Organize references in a (sub)collection in Zotero.
2. Use Better BibTeX plugin. Set it up to ignore fields "note,rights,copyright,langid,keywords,file,month,urldate,issn,abstract". Also “When an item has both …” → select DOI.
3. Export the thesis collection as Better BibTeX (not BibLaTeX).
4. Save/export to `example.bib` (or another file and update `\addbibresource{...}` accordingly).
5. Replace any temporary `\citetemp{...}` markers with `\cite{...}` once references are ready.