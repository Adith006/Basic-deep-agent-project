# Python implementation guidance

Start by identifying the requested behavior, affected entry points, Python version, and established project conventions. Make the smallest coherent change.

## Code quality

- Use descriptive names and small functions with one clear responsibility.
- Prefer `pathlib` for new filesystem code and context managers for resources.
- Catch specific exceptions only where recovery or useful context is possible. Do not silently discard errors.
- Avoid mutable default arguments and hidden global state.
- Keep I/O at the edges so core logic is straightforward to test.

## Interfaces and validation

- Add type annotations to new public functions and complex values when they make contracts clearer.
- Validate data received from files, environment variables, APIs, or users near the boundary.
- Return values or raise documented, actionable errors; do not print from reusable library functions.

## Verification

- Test normal behavior plus meaningful boundary and failure cases.
- Run the narrowest relevant test or command first. State clearly when verification could not be run.
- Do not add dependencies, alter lockfiles, or expose secrets unless the request calls for it.
