# AGENTS.md

This project uses the Karpathy LLM Wiki pattern.

**Primary schema**: see [CLAUDE.md](CLAUDE.md).

All agents (Claude Code, Cursor, Codex, etc.) should follow the rules in CLAUDE.md:
- Never modify `raw/`
- Own and maintain `wiki/`
- Support ingest / query / lint workflows
- Use `[[wikilinks]]`

Read CLAUDE.md at the start of every session.
