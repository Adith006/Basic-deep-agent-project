# Deep Agents Project Guidance

This file is loaded as part of the system prompt whenever an agent is created
in the demo notebooks. Keep these notes factual and relevant to this project.

## Architecture

- Deep Agents are built on LangGraph. `create_deep_agent` assembles a graph
  around the selected chat model, tools, system prompt, middleware, and
  configured state backend.
- The model chooses actions, while tools define what the agent can actually do.
  Only rely on tools that are provided to the agent or enabled by its
  configuration.
- Deep Agents commonly include planning, filesystem, and subagent capabilities
  through middleware. Their exact availability and behavior depend on the
  installed Deep Agents version and the graph configuration.
- A backend determines how agent files are accessed and stored. For example,
  a state backend scopes files to graph state, a filesystem backend works with
  disk, and a store backend uses a LangGraph store. Do not assume that one
  backend provides another backend's persistence or access behavior.
- Graph invocation and persistence are related but distinct: durable
  conversation state depends on the configured checkpointer and thread
  configuration; a backend alone does not guarantee conversation history.

## Working Guidelines

- Treat the task-specific system prompt as the source of the agent's role and
  response requirements; use this file as shared architectural context.
- Be explicit about assumptions, enabled tools, backend behavior, and
  persistence when explaining or changing an agent.
- Delegate only when a task can be split into independent work, and synthesize
  the results before responding.
- Prefer the smallest change that fits the existing notebook and project
  patterns. Do not claim that an agent can access files, services, or memory
  unless its tools and configuration support that capability.
