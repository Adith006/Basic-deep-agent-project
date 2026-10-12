# LangGraph examples

## Minimal explicit state and routing

```python
from typing import Literal, TypedDict


class ResearchState(TypedDict):
    question: str
    needs_research: bool


def choose_path(state: ResearchState) -> Literal["research", "answer"]:
    return "research" if state["needs_research"] else "answer"
```

Connect `choose_path` as a conditional edge, and ensure both destinations eventually reach a terminal node. Keep external API calls in the `research` node, where failures can be handled explicitly.

## Checkpointed invocation

```python
result = graph.invoke(
    {"question": "Summarize the design", "needs_research": False},
    config={"configurable": {"thread_id": "design-review-42"}},
)
```

This only persists across invocations when the graph was compiled with an appropriate checkpointer.
