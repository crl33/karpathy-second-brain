# Karpathy Second Brain

A ready-to-use implementation of Andrej Karpathy's LLM Wiki pattern: turn Claude Code (or any LLM agent) + an Obsidian vault into a compounding personal knowledge base.

> Obsidian is the IDE. The LLM is the programmer. The wiki is the codebase.

Instead of re-deriving answers from raw documents on every query (classic RAG), the LLM incrementally builds and maintains a persistent, interlinked wiki. Knowledge compounds. The graph in Obsidian becomes a living map of your thinking.

## Why this works

- **Persistent & compounding**: Insights are compiled once and kept current.
- **LLM as maintainer**: Cross-linking, summaries, contradiction detection, and indexing happen automatically.
- **You own the files**: Plain Markdown. No vendor lock-in. Works offline.
- **Obsidian graph view**: Visualize the network of ideas in real time as the LLM builds it.

Inspired by Karpathy's [LLM Wiki gist](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) and the viral "second brain" setups using Claude Code.

## Quick Start

1. **Clone this repo** (or use it as a template):
   ```bash
   git clone https://github.com/crl33/karpathy-second-brain.git my-brain
   cd my-brain
   ```

2. **Open as an Obsidian vault**:
   - Install [Obsidian](https://obsidian.md) (free)
   - Open the folder as a vault
   - Enable the Graph View (Ctrl/Cmd + G) to watch the network grow

3. **Point Claude Code at the vault**:
   ```bash
   # Inside the vault directory
   claude
   ```
   Claude Code automatically reads `CLAUDE.md`.

4. **Start using it**:
   - Drop files, PDFs, articles, or transcripts into `raw/`
   - Or paste a URL / text and say: **"ingest this"**
   - Ask questions: the LLM reads the wiki (not the raw sources) and answers with citations
   - Periodically say: **"lint the wiki"** for health checks

## Directory Structure

```
.
├── CLAUDE.md          # Schema — the LLM's operating manual (read this first)
├── raw/               # Immutable sources (you add, LLM never modifies)
├── wiki/              # LLM-owned knowledge layer
│   ├── index.md       # Master catalog (LLM updates on every ingest)
│   ├── log.md         # Chronological activity log
│   ├── overview.md    # High-level synthesis
│   ├── sources/       # One summary per ingested source
│   ├── entities/      # People, orgs, tools, products
│   ├── concepts/      # Ideas, frameworks, methods
│   ├── analyses/      # Syntheses, comparisons, filed answers
│   └── ...
└── .gitignore
```

## Core Operations

| Command / Action | What happens |
|------------------|--------------|
| **ingest** (or drop file in `raw/` + "ingest") | LLM reads source, creates summary, updates/creates entity & concept pages, cross-links everything, updates index + log |
| **Ask a question** | LLM reads `index.md` first, then relevant pages, synthesizes answer with `[[wikilinks]]`. Offers to file good answers back into the wiki |
| **lint** | Scans for contradictions, orphans, stale claims, missing links. Proposes fixes |

## Tips

- Keep Obsidian open next to your terminal. Watch the graph light up as Claude adds links.
- Use Obsidian's Web Clipper browser extension to dump articles straight into `raw/`.
- The system works with any agent that respects `CLAUDE.md` / `AGENTS.md` (Claude Code, Cursor, Codex, etc.).
- Everything is Git-versioned. Commit often.

## Customization

Edit `CLAUDE.md` to add domain-specific page types (e.g. `projects/`, `people/`, `decisions/`). The LLM will adapt.

## License

MIT — do whatever you want with it. Credit to Andrej Karpathy for the original pattern.
