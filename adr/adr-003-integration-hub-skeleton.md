---
title: 'Integration Hub Skeleton (Next.js scaffold)'
topic: 'integration-hub-skeleton'
category: 'integration'
status: 'draft'
created: '2026-03-08'
last_modified: '2026-03-08'
authors:
  - 'Architecture Review Board'
---

# Context

The platform requires a unified Integration Hub that can expose webhook endpoints, process inbound data, and route events to various downstream services (e.g., n8n, Temporal workflows). A lightweight Next.js scaffold provides rapid development, built‑in API routes, and TypeScript support.

# Decision

Create a new Next.js application in `packages/integration-hub` using the official `create-next-app` TypeScript template. The hub will expose API routes under `/api/*` for handling incoming webhooks and will delegate processing to LangGraph agents via the Temporal service.

# Consequences

| Impact                   | Details                                                                        |
| ------------------------ | ------------------------------------------------------------------------------ |
| **Developer Experience** | Standard Next.js tooling, hot‑reload, ESLint, and TypeScript out of the box.   |
| **Runtime**              | Runs in the same Docker Compose network; can be scaled independently.          |
| **Security**             | API routes can be protected with token‑based auth; secrets managed via `.env`. |
| **Future Work**          | Add GraphQL layer, integrate with existing Saleor webhook system.              |

# References

- Next.js Docs: https://nextjs.org/docs
- Existing Integration Hub study: `plans/studies/integration/study-integration-hub-draft.md`
- LangGraph + Temporal ADR 001
