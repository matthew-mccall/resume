# Matthew McCall Resume

This repository contains the LuaLaTeX source for Matthew McCall's resume. The main resume content lives in `MatthewMcCall.tex`, with shared typography, spacing, and helper commands in `config.tex`.

## Repository layout

- `MatthewMcCall.tex` - primary resume source.
- `config.tex` - shared packages, fonts, spacing, section styles, and custom commands.
- `fonts/` - vendored fonts used by `fontspec`.
- `modules/` - optional LaTeX wrappers for embedded assets such as Graphviz DOT, PlantUML, and KiCad diagrams.
- `scripts/` - Lua helper scripts used by LuaLaTeX for embedded asset generation.
- `graphs/` - Graphviz source examples and assets.
- `out/` - build output directory when configured by local tooling.

## Prerequisites

Install a TeX distribution with LuaLaTeX and `latexmk`, such as TeX Live or MacTeX. This project must be built with LuaLaTeX because it uses `fontspec` and Lua helpers.

The required fonts are included in `fonts/`, so no separate font installation should be necessary.

Optional embedded diagrams may require additional tools depending on which commands are used in the document:

- Graphviz for DOT diagrams.
- Java and PlantUML for PlantUML diagrams.
- KiCad utilities for KiCad-generated assets.

## Build the resume

From the repository root, run:

```sh
latexmk MatthewMcCall.tex
```

If embedded diagrams need external commands, enable shell escape:

```sh
latexmk -shell-escape MatthewMcCall.tex
```

The generated PDF and auxiliary LaTeX files are build artifacts and should not be edited by hand.

## Editing the resume

- Edit `MatthewMcCall.tex` for resume content changes.
- Edit `config.tex` for formatting, typography, spacing, or command changes.
- Keep entries concise and action-oriented.
- Preserve the one-page resume layout unless intentionally making a longer version.
- Escape LaTeX-sensitive characters in prose, such as `\&`, `\%`, and `_`.

Company entries use the shared command:

```tex
\company{Name}{Location}{Date range}
```

## Troubleshooting

- If the build fails with font errors, confirm that LuaLaTeX is being used instead of pdfLaTeX.
- If diagram generation fails, rerun with `-shell-escape` and confirm the required external tool is installed.
- If the PDF layout changes unexpectedly, check for overfull boxes or spacing warnings in the LaTeX log.

## License

See `LICENSE` for license information.