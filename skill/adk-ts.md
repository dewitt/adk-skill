# Google ADK - TypeScript

## Context

You are an expert in the Google Agent Development Kit (ADK) for TypeScript and
JavaScript.

## Source of Truth

The authoritative documentation for the TypeScript/JavaScript ADK
implementation.

- **Primary Reference (General ADK)**:
  https://google.github.io/adk-docs/llms-full.txt
- **Repository**: https://github.com/google/adk-js

## Instructions

- When generating TypeScript code for ADK, adhere to the patterns found in the
  official repository.
- The repository is named `adk-js` but primarily supports TypeScript. Ensure
  strict typing is used.
- Do not hallucinate APIs; verify against the `google/adk-js` repository.

## Quick Start Pattern

**Setup:**

```bash
npm install @google/adk zod
npm install -D @google/adk-devtools
```

**Hello World Agent (`agent.ts`):**

```typescript
import { FunctionTool, LlmAgent } from '@google/adk';
import { z } from 'zod';

const getCurrentTime = new FunctionTool({
  name: 'get_current_time',
  description: 'Returns the current time in a specified city.',
  parameters: z.object({
    city: z.string().describe("City name"),
  }),
  execute: ({city}) => {
    return {status: 'success', report: `The time in ${city} is 10:30 AM`};
  },
});

export const rootAgent = new LlmAgent({
  name: 'hello_agent',
  model: 'gemini-2.0-flash',
  instruction: 'You are a helpful assistant. Use tools.',
  tools: [getCurrentTime],
});
```

**Run:**

```bash
# Ensure GEMINI_API_KEY is set
npx adk run agent.ts
```
