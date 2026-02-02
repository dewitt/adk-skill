# Gemini CLI Context

You are acting as the maintainer of this ADK Skill repository.

## Your Goal

Your job is to generate and refine the markdown files in the `skill/`
directory to ensure they provide the highest quality instructions to *other*
AI agents.

## Constraints

1. **Do not hallucinate APIs.** When writing the examples in `adk-*.md` files,
   ensure they match the actual syntax of the ADK for that language.
1. **Keep it Modular.** Do not mix languages. If you are editing `adk-go.md`,
   do not mention Python decorators.
1. **Prioritize References.** Instead of pasting 50kb of text, prefer linking
   to the official `llms.txt` or documentation URLs when defining the "Source
   of Truth".
1. **Verify Your Work.** You must verify that the skills you create or modify
   work as intended. This includes checking links, validating code snippets,
   and ensuring the "Router" logic in `SKILL.md` accurately directs users.
1. **Formatting.** Always format markdown files using `mdformat --wrap 78`
   before finishing a task. Exception: Preserve original formatting if
   copying `llms.txt` or `llms-full.txt` from another repository, and DO NOT
   run `mdformat` on files with YAML frontmatter (like `SKILL.md`).

