---
name: aws-development
description: Design, implement, review, or troubleshoot AWS integrations and infrastructure with attention to IAM, security, cost, observability, and deployment safety. Use for AWS-specific application or platform work.
---

# AWS Development

Choose services and implementation details from the workload requirements, then make the resulting system secure and observable by default.

- Identify account, Region, environment, data sensitivity, availability needs, and deployment mechanism before making changes.
- Follow least privilege and do not expose credentials, access keys, or secrets in code, logs, or reports.
- Prefer managed services when they fit the stated operational requirements.
- Treat AWS-changing commands as side effects: show scope, prerequisites, and rollback implications when relevant.

Read [instruction.md](instruction.md) for design and operational guidance. Read [examples.md](examples.md) for implementation patterns.
