# Python examples

## Validate at the boundary

```python
from collections.abc import Mapping


def read_timeout(config: Mapping[str, object]) -> int:
    value = config.get("timeout_seconds", 30)
    if not isinstance(value, int) or value <= 0:
        raise ValueError("timeout_seconds must be a positive integer")
    return value
```

## Preserve error context

```python
from pathlib import Path


def load_text(path: Path) -> str:
    try:
        return path.read_text(encoding="utf-8")
    except OSError as exc:
        raise RuntimeError(f"Could not read {path}") from exc
```
