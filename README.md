# Evan Naraya

**Backend & AI Systems Engineer** · APIs · Integrations · Agent Orchestration

Based in Magelang, Indonesia (UTC+7). Open to international remote engineering roles and contracts.

I build Python and TypeScript systems where an API call is only one part of the job: requests need validation, state needs persistence, approvals need boundaries, and failures need a recovery path.

**[Engineering portfolio](https://evannaraya.com/)** · **[CV](https://evannaraya.com/cv/)** · **[LinkedIn](https://www.linkedin.com/in/evannaraya)** · **[Email](mailto:evannarayahp@gmail.com)**

## Selected engineering work

| Project | Implementation and evidence |
| --- | --- |
| **[RepoPilot AI](https://github.com/naraya07pedro-spec/repopilot-ai)** | Local-first coding proposal workflow with provider adapters, persistent review state, approval-bound changes and a recorded real CPU-model inference. [Release candidate PR #10](https://github.com/naraya07pedro-spec/repopilot-ai/pull/10). Local workspace and patch export are being validated; arbitrary code execution and autonomous publication remain disabled. |
| **[Bounded Agent Runtime](https://github.com/naraya07pedro-spec/agent-runtime-python)** | Python / FastAPI / PostgreSQL. Persisted dispatch intent, tenant boundaries, lease fencing, approvals, and uncertainty reconciliation. [Archived v2 verification](https://github.com/naraya07pedro-spec/agent-runtime-python/tree/f664908dcf5075616cdb9d469208529c3a69b078/evidence/v2) includes 261 passing tests. |
| **[Production Integration Reference](https://github.com/naraya07pedro-spec/production-integration-reference)** | TypeScript / PostgreSQL. Signed webhook intake, atomic event reservation and bounded retries. [Concurrency test](https://github.com/naraya07pedro-spec/production-integration-reference/blob/355e853fbb8af03b37b3b62eee20389e84c3e02e/tests/db/postgres.test.ts) exercises 12 duplicate requests against a controlled downstream fixture. |
| **[Full-Stack AI Operations Console](https://github.com/naraya07pedro-spec/fullstack-ai-operations-console)** | Next.js / Fastify / Prisma. Workflow versions, permissions, human approvals, leased workers and recovery. Tests use a deterministic HTTP sandbox, not a live production LLM. |
| **[Knowledge Workflow Runtime](https://github.com/naraya07pedro-spec/varevant.com/tree/6420665ccf54a6246278ca5c6a04781e94f42261/examples/agentic-systems-lab/knowledge-runtime)** | FastAPI / pgvector / MCP. Versioned retrieval, citation revalidation, deletion handling and permission-scoped tools. [Verification](https://github.com/naraya07pedro-spec/varevant.com/blob/6420665ccf54a6246278ca5c6a04781e94f42261/examples/agentic-systems-lab/knowledge-runtime/docs/verification.md) includes 12 synthetic retrieval cases. |

## Professional work

**VAREVANT | Independent AI Automation & Backend Engineer** (Jul 2026–present)

I develop integration and workflow automation for operational processes, including validation, deterministic controls and recovery paths.

- **PT Geget Gigit, Indonesia:** built LinkedIn, email and website outreach/follow-up workflows. The engagement contributed to approximately **2× lead volume**, as reported by the client/project owner.
- **EZUmrah, Malaysia:** integrated **21+ operational workflows** into a centralized AI-assisted command center to improve coordination, exception visibility and process monitoring.

Client engagement outcomes are described from project experience; confidential customer systems and credentials are not public.

## Technical focus

**Backend and integrations:** Python, FastAPI, Pydantic, SQLAlchemy, TypeScript, Fastify, REST APIs, webhooks, PostgreSQL, Supabase, Prisma and n8n.

**AI applications:** model-provider adapters, structured LLM outputs, durable agent state, local inference, retrieval, MCP and human approval boundaries.

**Reliability:** idempotency, authorization checks, transactional state, lease fencing, bounded retry, ambiguous-outcome reconciliation, testing and GitHub Actions.

## Engineering approach

- **Persist intent before side effects.** Timeouts and interrupted requests do not always mean an action failed.
- **Bound authority.** Generated proposals are not automatically authorized executions.
- **Prove the specific behavior.** A passing fixture test is useful evidence, but it is not a claim of production traffic, scale or zero failures.

**Explore the [live portfolio](https://evannaraya.com/) or [contact me](mailto:evannarayahp@gmail.com).**
