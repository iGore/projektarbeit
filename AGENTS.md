# AGENTS.md

## Purpose

This repository contains a German-language LaTeX project report about a multi-agent system for automated code migration using Spec-Driven Development and Agentic Workflow Orchestration.

## Repository layout

- `main.tex`: main LaTeX entrypoint
- `kapitel/kapitel1.tex` to `kapitel/kapitel6.tex`: chapter files included by `main.tex`
- `anhang.tex`, `acronym.tex`, `literatur.bib`: appendix, acronyms, bibliography
- `abbildungen/`: image assets, including `FH_Dortmund-logo.png`
- `.github/workflows/`: GitHub Actions for PDF build, tagging, and releases
- `README.md`: canonical project overview / expose text

## Working rules

- Preserve the existing LaTeX chapter structure unless the user explicitly asks for a reorganization.
- Treat this as a German academic paper throughout; default language for report prose is German.
- Keep German prose in German; keep technical identifiers and code terms in English where appropriate.
- Prefer small, targeted edits over broad rewrites.
- Do not edit ignored working files such as `Inhaltsverzeichnis.md`, `Links.md`, `.opencode/`, `Notizen/`, or `Lektüre/` unless the user explicitly asks.
- Use ASCII when practical in code/config files, but keep proper German spelling in user-facing Markdown and LaTeX content.
- In LaTeX report content, use proper German umlauts and special characters (ä, ö, ü, Ä, Ö, Ü, ß) instead of ASCII substitutions like `ae`, `oe`, `ue`, or `ss`, unless a technical identifier requires ASCII.
- Write commit messages in German and describe the concrete content changes in the project report briefly (e.g., which chapter/section was expanded, revised, or corrected, and in what way).

## Build and verification

On macOS with MacTeX installed, use:

```bash
PATH="/Library/TeX/texbin:$PATH" latexmk -pdf -interaction=nonstopmode -file-line-error main.tex
```

Notes:

- The project uses `biblatex` with `biber` backend.
- The generated PDF is `main.pdf`.
- Current builds may emit non-fatal warnings for undefined acronym references and empty bibliography output when no citations are present.

## GitHub automation

- `.github/workflows/latex-pdf.yml`: builds `main.pdf` on push, PR, and manual runs, then uploads it as an artifact.
- `.github/workflows/release-pdf.yml`: builds and releases `main.pdf` on `v*` tag pushes.
- `.github/workflows/tag-and-release-main.yml`: creates an automatic tag and release for pushes to `main`.

## Content conventions

- The active logo in `main.tex` is `abbildungen/FH_Dortmund-logo.png`.
- `README.md` is the canonical expose text; `Exposé.md` has been removed to avoid duplicate maintenance.
- The LaTeX section hierarchy should stay aligned with the intended report outline in the chapter files.

## Research sources

- NotebookLM source for literature and source mapping: `https://notebooklm.google.com/notebook/d8eb3353-0d7e-43e8-8649-6bc42c2a9c9f`
- Use the NotebookLM source to identify which references support sections such as Reverse Engineering, Spec-Driven Development, MCP, Context Engineering, evaluation criteria, and the Bachelorarbeit outlook.
