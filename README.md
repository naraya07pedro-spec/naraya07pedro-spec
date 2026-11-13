# Evan Naraya

**Backend & Integration Engineer** · Python · TypeScript · Applied AI Systems

Based in Magelang, Indonesia (UTC+7). Open to international remote engineering roles and contracts.

I build Python and TypeScript systems where an API call is only one part of the job: requests need validation, state needs persistence, approvals need boundaries, and failures need a recovery path.

**[Engineering portfolio](https://evannaraya.com/)** · **[CV](https://evannaraya.com/cv/)** · **[LinkedIn](https://www.linkedin.com/in/evannaraya)** · **[Email](mailto:evannarayahp@gmail.com)**

## Selected engineering work

**Start here:** [Exact-revision engineering evidence and reviewer paths](ENGINEERING-EVIDENCE.md). Each link separates implementation, tests, current-as-of-13-November CI and unverified production claims.

| Priority | Project | Implementation and reproducible review |
| --- | --- | --- |
| **Flagship 1** | **[Bounded Agent Runtime](https://github.com/naraya07pedro-spec/agent-runtime-python)** | Python / FastAPI / PostgreSQL: durable intent, tenant permissions, approvals, worker fencing and uncertain-effect reconciliation. [Main CI at `976d2d8`](https://github.com/naraya07pedro-spec/agent-runtime-python/actions/runs/43427999254) · [failure tests](https://github.com/naraya07pedro-spec/agent-runtime-python/blob/976d2d8f39133fb6f2c1f5bbe194d0222014eb00/tests/failure_injection/test_process_death.py). The separate v2 archive retains **261 tests / 90.01% coverage**; those figures are not claimed for current main. |
| **Flagship 2** | **[Production Integration Reference](https://github.com/naraya07pedro-spec/production-integration-reference)** | TypeScript / PostgreSQL: timestamp-bound HMAC, server-bound trusted source, atomic reservation, classified retries honoring bounded provider Retry-After, bounded provider responses and reconciliation limits. [Main CI at `e7f7bf6`](https://github.com/naraya07pedro-spec/production-integration-reference/actions/runs/43471682523) · [real database contention tests](https://github.com/naraya07pedro-spec/production-integration-reference/blob/e7f7bf68b24beb675557c04e09f7064d411f5dae/tests/db/postgres.test.ts). [Disposable PostgreSQL reviewer smoke](https://github.com/naraya07pedro-spec/production-integration-reference/blob/e7f7bf68b24beb675557c04e09f7064d411f5dae/scripts/reviewer-smoke.mjs) is now tested on main; provider-enforced idempotency remains an external contract. |
| **Flagship 3** | **[Full-Stack AI Operations Console](https://github.com/naraya07pedro-spec/fullstack-ai-operations-console)** | Next.js / Fastify / Prisma / PostgreSQL: versioned workflows, owner/role authorization, human approval, leased workers and recovery. [Main CI at `046d6c7`](https://github.com/naraya07pedro-spec/fullstack-ai-operations-console/actions/runs/43428368237) · [negative-case tests](https://github.com/naraya07pedro-spec/fullstack-ai-operations-console/blob/046d6c7f062d88fb811491537e97849a33d4b610/tests/integration/system.test.ts). HTTP triage is a deterministic sandbox, not a live production LLM. |
| **Candidate** | **[RepoPilot AI](https://github.com/naraya07pedro-spec/repopilot-ai)** | Local-first, review-first coding proposals with bounded execution and manual publication gates. [Main CI at `0936be4`](https://github.com/naraya07pedro-spec/repopilot-ai/actions/runs/43424724046) · [draft release candidate](https://github.com/naraya07pedro-spec/repopilot-ai/pull/10). No general hostile-code sandbox or autonomous production publication claim. |
| **Supporting** | **[Knowledge Workflow Runtime](https://github.com/naraya07pedro-spec/varevant.com/tree/main/examples/agentic-systems-lab/knowledge-runtime)** | FastAPI / pgvector / MCP, source versioning and citation validation. [Historical synthetic retrieval verification](https://github.com/naraya07pedro-spec/varevant.com/blob/829711f66a3b65f7d8e819a6c3144b7f2d044a57/examples/agentic-systems-lab/knowledge-runtime/docs/verification.md); not a live search-quality or production-use assertion. |

## Professional work

**VAREVANT | Independent AI Automation & Backend Engineer** (Jul 2026–present; owner-described professional scope)

I work on API integration and workflow automation where authorization, validation and recovery matter.

- **PT Geget Gigit, Indonesia:** a marketing-automation and decision-workflow engagement described by the project owner.
- **EZUmrah, Malaysia:** an end-to-end operational workflow integration engagement described by the project owner.

**Evidence boundary:** the two client descriptions are self-reported scope, **not independently confirmed client-origin handoffs or ROI measurements**. The separate [client evidence notes](CLIENT-WORK.md) explain precisely what can and cannot be published. Public flagship tests demonstrate reference engineering, not either customer's deployment, performance or revenue.

## Technical focus

**Backend and integrations:** Python, FastAPI, Pydantic, SQLAlchemy, TypeScript, Fastify, REST APIs, webhooks, PostgreSQL, Supabase, Prisma and n8n.

**AI applications:** model-provider adapters, structured LLM outputs, durable agent state, local inference, retrieval, MCP and human approval boundaries.

**Reliability:** idempotency, authorization checks, transactional state, lease fencing, bounded retry, ambiguous-outcome reconciliation, testing and GitHub Actions.

## Engineering approach

- **Persist intent before side effects.** Timeouts and interrupted requests do not always mean an action failed.
- **Bound authority.** Generated proposals are not automatically authorized executions.
- **Prove the specific behavior.** A passing fixture test is useful evidence, but it is not a claim of production traffic, scale or zero failures.

**Explore the [live portfolio](https://evannaraya.com/) or [contact me](mailto:evannarayahp@gmail.com).**
