# 012 – Agent Orchestration Engine

**Wave:** 2 (depends on Temporal service and ADR framework)
**Assignable to:** core development team
**Estimated effort:** 3–4 days

---

## Objective

Implement the runtime that coordinates LangGraph agents, leveraging the Temporal service for durability and state persistence. This engine will expose a simple HTTP API for launching agent workflows and will be the backbone for all autonomous sub‑agents (MCP, n8n integrations, etc.).

## Tasks

1. **Create `packages/agent-orchestration`** as a new TypeScript package.
2. Add a thin Express/Koa server that proxies requests to the Temporal client SDK.
3. Implement helper utilities to translate LangGraph graph definitions into Temporal workflows.
4. Write unit tests covering workflow registration and execution flow.
5. Add Dockerfile and compose service definition (will reuse the `temporal` service for state).
6. Document usage in `docs/adr/adr-001-docker-orchestration.md` (already references this component).

## Acceptance Criteria

- The service starts alongside `temporal` in `docker-compose.dev.yml`.
- Able to launch a simple "ping‑pong" LangGraph workflow that persists state across container restarts.
- All unit tests pass (`pnpm test packages/agent-orchestration`).
- README with quick‑start instructions added.

## References

- ADR 001 – Docker Orchestration
- Temporal Python SDK docs
- LangGraph documentation
