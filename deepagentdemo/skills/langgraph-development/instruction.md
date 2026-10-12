# LangGraph implementation guidance

## Design the graph first

Identify the input contract, state schema, node responsibilities, terminal conditions, and any human or tool boundaries. Prefer a simple linear graph unless conditional routing or parallel work is genuinely required.

- Define state fields with clear ownership and merge behavior.
- Make routers deterministic when possible; validate decisions that control safety-sensitive or costly actions.
- Keep prompt construction in a dedicated node or helper rather than spreading it through the graph.
- Bound loops with an explicit completion condition or iteration limit.

## Deep Agents integration

- `create_deep_agent` combines the selected model, tools, prompt, middleware, and backend; inspect its configuration instead of assuming defaults.
- A state backend governs file access/storage scope; a checkpointer governs durable conversation or graph state. Configure both deliberately when persistence is required.
- Tools are the permission boundary. Give the model concise tool descriptions and validate tool inputs before side effects.
- Use a stable `thread_id` only when continuity across invocations is intended.

## Verification

Exercise at least one successful path and one relevant alternate or failure path. Check final state and emitted messages, not just that the graph compiles.
