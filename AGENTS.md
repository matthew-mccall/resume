# AGENTS.md

Guidance for AI coding agents working in this repository.

## Project Overview

This is a LuaLaTeX resume project. The main document is `MatthewMcCall.tex`; shared formatting and package setup live in `config.tex`. Local font files are vendored under `fonts/`, and optional embedding helpers live in `modules/` and `scripts/`.

## Repository Layout

- `MatthewMcCall.tex`: primary resume content.
- `config.tex`: typography, spacing, section formatting, custom commands, and module imports.
- `modules/`: LaTeX wrappers for embedded assets such as DOT, PlantUML, and KiCad diagrams.
- `scripts/`: Lua helpers invoked by LuaLaTeX for embedded asset generation.
- `graphs/`: Graphviz source examples/assets.
- `fonts/`: vendored fonts required by `fontspec`.

## Build And Verification

Build with `latexmk`. The underlying engine must be LuaLaTeX, not pdfLaTeX, because the project uses `fontspec` and `\directlua`.

Typical build:

```sh
latexmk MatthewMcCall.tex
```

When embedded diagrams are used, shell escape and external tools may be required:

```sh
latexmk -shell-escape MatthewMcCall.tex
```

External tools may include Graphviz, PlantUML/Java, and KiCad utilities depending on which embedding commands are present in the document.

Before finishing substantive edits, compile the resume and check for warnings that affect output, such as missing fonts, overfull boxes, missing files, or failed embedded-asset commands.

## Editing Guidelines

- Keep resume content concise and action-oriented.
- Preserve the current one-page resume intent unless the user explicitly asks for a longer document.
- Prefer editing `MatthewMcCall.tex` for content changes and `config.tex` for layout/style changes.
- Do not edit vendored font files or license files unless the user specifically asks.
- Keep LaTeX commands and spacing consistent with the surrounding file.
- Use ASCII unless the edited file already requires non-ASCII text.
- Avoid broad formatting churn; make focused changes that are easy to review.

## Style Notes

- Section headings are unnumbered and styled through `titlesec` in `config.tex`.
- Company entries should use `\company{name}{location}{date range}`.
- Bullets should remain compact; list spacing is controlled globally with `enumitem`.
- Escape LaTeX-sensitive characters in prose, for example `\&`, `\%`, and `_` where needed.
- Prefer `\LaTeX`, `C\#`, and similar existing notation patterns already used in the document.

## Generated Files

LaTeX builds may produce files such as `.aux`, `.log`, `.out`, generated PDFs, and embedded-asset outputs. Do not treat these as source unless the user asks to update or inspect generated artifacts.

## Git Safety

The worktree may contain user changes. Do not revert or overwrite unrelated changes. If an unexpected existing edit affects the requested task, inspect it and work with it; ask the user only if it makes the task impossible.
