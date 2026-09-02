# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A personal, file-based archive of Dante Alighieri's *Divina Commedia* — not a software project. There is no git repository, no build system, and no code to compile, lint, or test. Work here consists of organizing, renaming, and cross-referencing PDFs, images, and Markdown notes.

## Structure

- `Inferno/`, `Purgatorio/`, `Paradiso/` — one folder per cantica, each meant to contain a `N° Canto/` subfolder per canto (e.g. `Inferno/9° Canto/`). Only `Inferno/` is currently populated (Canti 1–12); `Purgatorio/` and `Paradiso/` are empty and should follow the same per-canto folder convention when filled in.
- Inside each `N° Canto/` folder: the original PDFs for that canto (full text, `_Parafrasi` paraphrase, `_Terzina` terzina-by-terzina) plus a Markdown riassunto (see naming rule below).
- `Riassunto dei canti/` — source Markdown riassunti (currently `1° Canto.md` … `12° Canto.md`), written before being copied into their corresponding `Inferno/N° Canto/` folder. Also holds `I Cerchi dell'Inferno.html` and `page_design.html`.
- `Ars - Gabriele Dell'Otto/` — artwork images keyed by canto/cantica in the filename (e.g. `Canto_10_Farinata-...jpg`, `Paradiso_Canto_01-...jpg`).
- `Immagini/` — general illustrative images (portraits, character art) not tied to a specific canto.
- `weebly/` — PDFs exported from an external Weebly site: cantica-level guides (`Cantiche/`), the day-by-day journey chronology (`Cronologia del viaggio dantesco/`), and author material (`L'autore/`).

## Conventions

- **Canto commentary filenames use the short form `<Cantica>, Canto <RomanNumeral>.md`** (e.g. `Inferno, Canto XIII.md`), even when the file's H1 carries a longer subtitle (e.g. `# Inferno, Canto XIII — La selva dei suicidi: il pianto di Pier della Vigna`). Canto V is the one exception: its file has no H1 at all, only an H2, so its filename (`Galeotto fu il libro e chi lo scrisse.md`) follows that H2 instead.
- Canto folder names use the ordinal-with-degree-sign format: `1° Canto`, `2° Canto`, … `34° Canto`.
- PDF filenames follow `Canto_<RomanNumeral>_<Slug>[.pdf | _Parafrasi.pdf | _Terzina.pdf]`.
- `Inferno/13° Canto/Inferno, Canto XIII.md` (plus its source `content.txt` in the same folder) is the canonical structural reference for the canto-commentary format — narrative sections, "Il senso del canto", "Riassunto". The **`canto-md` skill** (`.claude/skills/canto-md/`) generates new canto commentary files in this exact format from raw canto text.
