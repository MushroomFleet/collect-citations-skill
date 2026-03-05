# collect-citations-skill

A Claude AI skill that processes citation reports produced by the [citation-needed skill](https://github.com/MushroomFleet/citation-needed-skill) into polished, numbered citation appendices — and optionally applies inline citation markers and factual corrections back into your source documents.

---

## Overview

`collect-citations` is the second stage in a two-skill citation pipeline:

```
citation-needed  →  collect-citations
   (verify)            (compile & apply)
```

1. **[citation-needed](#)** searches the web to verify factual claims in your documents, producing a `-citations.md` report with confirmed sources, near misses, and unverified claims.
2. **collect-citations** (this skill) reads that report and produces:
   - A clean numbered citation appendix (`[base]-citations-list.md`)
   - Optionally, a corrected version of your source document with inline citation markers and suggested fixes applied (`[base]-corrected.md`)

---

## Two Modes

| Mode | Input | Output | Description |
|------|-------|--------|-------------|
| **Mode 1** | `[base]-citations.md` | `[base]-citations-list.md` | Always runs — builds numbered appendix |
| **Mode 2** | `[base]-citations.md` + `[base].md` | `[base]-corrected.md` | Optional — applies markers and corrections to source |

---

## Installation

### Claude.ai (Web / Desktop)

Upload the `.skill` file directly through the Claude interface:

1. Download `collect-citations.skill` from the [Releases](#) page
2. In Claude.ai, go to **Settings → Skills**
3. Upload the `.skill` file

The `.skill` file is a standard ZIP archive — Claude.ai handles installation automatically.

### Claude Code (CLI)

For terminal-based Claude Code installations, unzip the `.skill` file into your commands directory:

```bash
# Navigate to your Claude commands directory
cd ~/.claude/commands/

# Unzip the skill archive directly here
unzip /path/to/collect-citations.skill
```

This places `collect-citations/SKILL.md` at `~/.claude/commands/collect-citations/SKILL.md`, making the skill available in all Claude Code sessions.

---

## Usage

### Compile a citation appendix (Mode 1)

```
collect citations from chapter1-citations.md
```

Produces: `chapter1-citations-list.md`

### Apply citations to source document (Mode 1 + 2)

```
apply citations from chapter1-citations.md to chapter1.md
```

Produces: `chapter1-citations-list.md` and `chapter1-corrected.md`

### Batch processing

```
collect citations from all -citations.md files in this directory
```

---

## Pipeline Example

```
my-essay.md
    │
    ▼  citation-needed skill
my-essay-citations.md          ← verified claims, near misses, unverified
    │
    ▼  collect-citations skill
my-essay-citations-list.md     ← numbered appendix
my-essay-corrected.md          ← source with [1][2] markers + corrections
```

---

## Requirements

- Claude Code (CLI) or Claude.ai with Skills enabled
- The [citation-needed skill](#) is required upstream to generate compatible `-citations.md` input files

---

## 📚 Citation

### Academic Citation

If you use this codebase in your research or project, please cite:

```bibtex
@software{collect_citations_skill,
  title = {Collect Citations Skill: Citation compilation and application skill for Claude AI},
  author = {[Drift Johnson]},
  year = {2025},
  url = {https://github.com/MushroomFleet/collect-citations-skill},
  version = {1.0.0}
}
```

### Donate:

[![Ko-Fi](https://cdn.ko-fi.com/cdn/kofi3.png?v=3)](https://ko-fi.com/driftjohnson)
