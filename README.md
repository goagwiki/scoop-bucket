# Scoop bucket: goagwiki

Install [**agwiki**](https://github.com/goagwiki/agwiki), the **agent-based wiki** CLI, on Windows with [Scoop](https://scoop.sh/).

**agwiki** is a Rust CLI for markdown wikis: **`init`**, **`ingest`** (via **`aikit run --events`**), **`validate`** (links + orphans), and **`export-skill`** (Agent Skill bundle under `skill/`).

## Installation

### Option 1: add bucket (recommended)

Enables `scoop update agwiki`:

```powershell
scoop bucket add goagwiki https://github.com/goagwiki/scoop-bucket
scoop install agwiki
```

### Option 2: direct manifest

```powershell
scoop install https://raw.githubusercontent.com/goagwiki/scoop-bucket/main/bucket/agwiki.json
```

Updates are not tracked automatically with this method.

## Usage notes

- **`ingest`**, **`validate`**, and **`export-skill`** accept **`-C` / `--wiki-root`** (content repo with `wiki/`); if omitted, the current working directory is used.
- **`ingest`** requires **`<wiki-root>\ingest.md`** (copy from the [agwiki template](https://github.com/goagwiki/agwiki/blob/main/prompts/ingest.md) if needed). Placeholders **`{{INGEST_PATH}}`** and **`{{WIKI_ROOT}}`** are expanded by `agwiki`.
- Install **`aikit`** and ensure it is on `PATH`. **`ingest`** uses **`aikit run --events`** (NDJSON on stdout). **`-a` / `--agent` is required**; **`-m`** and **`--stream`** match `aikit run`.

## Usage examples

```powershell
agwiki --version

agwiki init C:\path\to\new-wiki

agwiki ingest -C C:\path\to\wiki -a opencode C:\path\to\wiki\raw\note.md

agwiki validate -C C:\path\to\wiki
agwiki validate --format json

agwiki export-skill -C C:\path\to\wiki --prune
```

Run `agwiki <subcommand> --help` for full flags and embedded examples.

## Upgrading

```powershell
scoop update agwiki
```

## Uninstalling

```powershell
scoop uninstall agwiki
scoop bucket rm goagwiki
```

## Links

- [agwiki on GitHub](https://github.com/goagwiki/agwiki)
- [Homebrew tap (macOS / Linux)](https://github.com/goagwiki/homebrew-cli)
