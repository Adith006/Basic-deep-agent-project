# AWS examples

## Least-privilege policy shape

Scope permissions to the exact resource and action rather than using a wildcard:

```json
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": ["s3:GetObject"],
    "Resource": "arn:aws:s3:::example-private-bucket/reports/*"
  }]
}
```

Add only the actions and conditions demonstrated by the workload.

## Idempotent event handling

```python
def process_event(event_id: str, repository) -> None:
    if repository.was_processed(event_id):
        return
    repository.apply_business_change(event_id)
    repository.mark_processed(event_id)
```

In production, make the state transition atomic or use a datastore operation that prevents concurrent duplicate processing.
