# Google ADK Skill

This repository hosts a modular "Skill" designed to teach AI agents (including
Gemini Code Assist, Cursor, and others) how to correctly implement the Google
Agent Development Kit (ADK) across multiple programming languages.

## Purpose

The goal is to provide high-fidelity, context-aware instructions to AI coding
assistants, ensuring they:

1. Understand the high-level ADK architecture (Agents, Workflow Agents, MCP,
   Sessions & Memory).
1. Use the correct language-specific patterns (Python, Go, TS/JS, Java).
1. Reference the official sources of truth rather than hallucinating APIs.

## Usage

AI Agents consuming this skill should start at
[skill/SKILL.md](skill/SKILL.md), which acts as the router to
language-specific guides.

## Structure

- `skill/SKILL.md`: The Master Router / General Architect.
- `skill/adk-python.md`: Python specific context & patterns.
- `skill/adk-go.md`: Go specific context & patterns.
- `skill/adk-ts.md`: TypeScript/JS specific context & patterns.
- `skill/adk-java.md`: Java specific context & patterns.
