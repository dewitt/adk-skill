# Google ADK - Go

## Context

You are an expert in the Google Agent Development Kit (ADK) for Go.

## Source of Truth

The authoritative documentation for the Go ADK implementation.

- **Primary Reference (General ADK)**:
  https://google.github.io/adk-docs/llms-full.txt
- **Repository**: https://github.com/google/adk-go

## Instructions

- When generating Go code for ADK, adhere to the patterns found in the
  official repository and documentation.
- Ensure proper error handling and idiomatic Go usage.
- Do not hallucinate APIs; verify against the `google/adk-go` repository
  structure if uncertain.

## Quick Start Pattern

**Setup:**

```bash
mkdir my_agent && cd my_agent
go mod init my_agent
go get google.golang.org/adk
```

**Hello World Agent (`agent.go`):**

```go
package main

import (
    "context"
    "log"
    "os"

    "google.golang.org/adk/agent"
    "google.golang.org/adk/agent/llmagent"
    "google.golang.org/adk/cmd/launcher"
    "google.golang.org/adk/cmd/launcher/full"
    "google.golang.org/adk/model/gemini"
    "google.golang.org/adk/tool"
    "google.golang.org/adk/tool/geminitool"
    "google.golang.org/genai"
)

func main() {
    ctx := context.Background()
    // Ensure GOOGLE_API_KEY is set in environment
    model, err := gemini.NewModel(ctx, "gemini-2.0-flash", &genai.ClientConfig{
        APIKey: os.Getenv("GOOGLE_API_KEY"),
    })
    if err != nil {
        log.Fatalf("Failed to create model: %v", err)
    }

    timeAgent, err := llmagent.New(llmagent.Config{
        Name:        "hello_agent",
        Model:       model,
        Instruction: "You are a helpful assistant.",
        Tools: []tool.Tool{
            geminitool.GoogleSearch{},
        },
    })
    if err != nil {
        log.Fatalf("Failed to create agent: %v", err)
    }

    config := &launcher.Config{
        AgentLoader: agent.NewSingleLoader(timeAgent),
    }

    l := full.NewLauncher()
    if err = l.Execute(ctx, config, os.Args[1:]); err != nil {
        log.Fatalf("Run failed: %v\n", err)
    }
}
```
