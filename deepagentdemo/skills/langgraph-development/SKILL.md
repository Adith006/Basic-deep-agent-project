---
name: langgraph-development
description: Build, explain, review, or debug LangGraph and Deep Agents workflows, including state, nodes, edges, tools, persistence, and streaming. Use for LangGraph-specific agent orchestration work.
---

# LangGraph Development

Build workflows whose state, control flow, and tool permissions are explicit and testable.

- Confirm the installed APIs and the current graph structure before proposing code.
- Model durable state separately from transient runtime data.
- Keep nodes focused, make routing conditions explicit, and design for retries or failures where external work occurs.
- Only claim an agent can call tools, persist data, or delegate when those capabilities are configured.

Read [instruction.md](instruction.md) for graph-design guidance. Read [examples.md](examples.md) for state and routing patterns.
