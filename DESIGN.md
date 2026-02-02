# ADK Skill Repository Design

## Overview

This repository hosts a modular "Skill" designed to teach AI agents (including
Gemini Code Assist, Cursor, and others) how to correctly implement the Google
Agent Development Kit (ADK) across multiple programming languages.

## Architectural Goals

1. **Language Agnostic Core:** The primary entry point (`SKILL.md`) serves as
   a router, understanding the high-level ADK architecture (Agents, Workflow
   Agents, MCP, Memory) common to all implementations.
1. **Language Specificity:** Dedicated sub-skills avoid context pollution. A
   Python agent shouldn't be confused by Go struct tags.
1. **Source of Truth:** Where possible, leverage existing high-fidelity
   context files (like `llms.txt`) rather than rewriting documentation.

## Directory Structure

```text
.
├── GEMINI.md           # Meta-instructions for the Gemini CLI working on this repo
├── README.md           # User-facing documentation
└── skill/
    ├── SKILL.md        # The Master Router / General Architect
    ├── adk-python.md   # Python specific context & patterns
    ├── adk-go.md       # Go specific context & patterns
    ├── adk-ts.md       # TypeScript/JS specific context & patterns
    └── adk-java.md     # Java specific context & patterns
```

## Testing Strategy

To maintain trust in this skill, all changes must be verified:

1. **Link Validation:** All external URLs (especially to `llms.txt` or docs)
   must be verified as reachable.
1. **Code Integrity:** All code snippets embedded in markdown must be
   syntactically correct for their target language.
1. **Router Logic:** Ensure `SKILL.md` correctly links to the sub-skills and
   that the decision tree for language selection is clear.
1. **End-to-End Simulation:** When modifying a skill, simulate a user request
   (e.g., "How do I create a flow in Python?") to ensure the skill provides
   the correct guidance path.

## Standards & Conventions

1. **Markdown Formatting:** All markdown files must be formatted with
   `mdformat --wrap 78`. This ensures human readability in terminal
   environments and consistent diffs. **Exception:** Do not run `mdformat` on
   files with YAML frontmatter (like `SKILL.md`), as it may corrupt the
   metadata.
1. **External Content:** When importing `llms.txt` or `llms-full.txt` files
   from upstream repositories, preserve their original formatting to maintain
   fidelity with the source.
