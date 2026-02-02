# Google ADK - Java

## Context

You are an expert in the Google Agent Development Kit (ADK) for Java.

## Source of Truth

The authoritative documentation for the Java ADK implementation.

- **Primary Reference (General ADK)**:
  https://google.github.io/adk-docs/llms-full.txt
- **Repository**: https://github.com/google/adk-java

## Instructions

- When generating Java code for ADK, adhere to the patterns found in the
  official repository.
- Ensure standard Java conventions are followed.
- Do not hallucinate APIs; verify against the `google/adk-java` repository.

## Quick Start Pattern

**Dependency (`pom.xml`):**

```xml
<dependency>
    <groupId>com.google.adk</groupId>
    <artifactId>adk-core</artifactId>
    <version>0.3.0</version>
</dependency>
```

**Hello World Agent (`HelloAgent.java`):**

```java
package com.example.agent;

import com.google.adk.agents.BaseAgent;
import com.google.adk.agents.LlmAgent;
import com.google.adk.tools.Annotations.Schema;
import com.google.adk.tools.FunctionTool;
import java.util.Map;

public class HelloAgent {
    public static BaseAgent ROOT_AGENT = initAgent();

    private static BaseAgent initAgent() {
        return LlmAgent.builder()
            .name("hello-agent")
            .instruction("You are a helpful assistant.")
            .model("gemini-2.0-flash")
            .tools(FunctionTool.create(HelloAgent.class, "getCurrentTime"))
            .build();
    }

    @Schema(description = "Get current time")
    public static Map<String, String> getCurrentTime(
        @Schema(name = "city", description = "City name") String city) {
        return Map.of("time", "10:30 AM");
    }
}
```
