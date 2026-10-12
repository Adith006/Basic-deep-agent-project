# AWS implementation guidance

## Establish context

Before selecting services or writing infrastructure, identify the workload type, traffic profile, data classification, recovery objectives, Region constraints, integration points, and budget sensitivity. State any assumptions that materially affect the design.

## Security and permissions

- Use IAM roles and short-lived credentials in workloads; do not embed long-lived credentials.
- Grant only the actions, resources, and conditions the workload needs.
- Encrypt sensitive data in transit and at rest. Use a secrets manager or parameter store for application secrets.
- Separate development, staging, and production configuration and access.

## Reliability and operations

- Design idempotent handlers for retries and duplicate event delivery.
- Define logging, metrics, alarms, and correlation identifiers for production workloads.
- Tag resources consistently for owner, application, environment, and cost allocation when the project's conventions exist.
- Use infrastructure as code for repeatable resources; preview changes before applying them.

## Cost and delivery

- Choose scaling and retention policies intentionally. Call out recurring-cost drivers and relevant service limits.
- Do not run deployment, deletion, or account-level changes without the requested authorization and a clearly identified target.
