---
name: adk-skill
description: Teaches AI agents how to correctly implement the Google Agent Development Kit (ADK) across Python, Go, TypeScript, and Java.
---

## Description

This skill enables AI agents to correctly implement the Google Agent
Development Kit (ADK) across multiple programming languages. It acts as a
router, directing the agent to the specific language context needed for the
task.

## High-Level Architecture

The ADK provides a unified framework for building AI agents, centered around
these core concepts:

1. **Agents**: Autonomous entities (`LlmAgent`) that observe the world and act
   upon it using tools.
1. **Workflow Agents**: Deterministic controllers (`SequentialAgent`,
   `ParallelAgent`, `LoopAgent`) for orchestration.
1. **Model Context Protocol (MCP)**: A standard for connecting AI models to
   data and tools.
1. **Sessions & Memory**: Mechanisms for managing short-term conversation
   context and long-term user recall.

## Usage

When a user requests assistance with the Google ADK:

1. **Identify the Programming Language**: Determine if the user is working
   with Python, Go, TypeScript/JS, or Java.
1. **Consult Specific Guides**:
   - For **Python**, refer to `adk-python.md`.
   - For **Go**, refer to `adk-go.md`.
   - For **TypeScript/JavaScript**, refer to `adk-ts.md`.
   - For **Java**, refer to `adk-java.md`.
1. **Cross-Language Concepts**: For general architectural questions not
   specific to a language, refer to the definitions above and the general ADK
   documentation.
