# Evan Naraya

**Software Engineer · Backend & Integration · Python/FastAPI · TypeScript · PostgreSQL**

I build backend and full-stack systems with explicit authorization, durable state, and recoverable failure paths. My public projects are engineering references with reproducible tests—not claims of customer scale or production traffic.

**Indonesia (UTC+7) · Open to remote software engineering and integration roles that hire from Indonesia**

[Portfolio](https://evannaraya.netlify.app/) · [LinkedIn](https://www.linkedin.com/in/evannaraya/) · [Email](mailto:evannarayahp@gmail.com)

## Start here — four projects to inspect

| Project | Engineering work | Fastest evidence |
| --- | --- | --- |
| **[Evan Naraya Portfolio](https://github.com/naraya07pedro-spec/evan-naraya-portfolio)** | Portfolio showcase, release readiness verification, SHA256 integrity audits, and automated native test suites | [Verification proof](https://github.com/naraya07pedro-spec/evan-naraya-portfolio#%EF%B8%8F-reliability-engineering--automated-verification) · [tests](https://github.com/naraya07pedro-spec/evan-naraya-portfolio/tree/main/tests) · [CI](https://github.com/naraya07pedro-spec/evan-naraya-portfolio/actions/workflows/quality.yml) |
| **[Full-Stack AI Operations Console](https://github.com/naraya07pedro-spec/fullstack-ai-operations-console)** · [portfolio demo](https://evannaraya.netlify.app/#operations-console) | Next.js/React frontend; Fastify API; PostgreSQL/Prisma; separate worker; sessions, versioned workflows, approvals, leases, retries and recovery | [Architecture](https://github.com/naraya07pedro-spec/fullstack-ai-operations-console/blob/main/docs/ARCHITECTURE.md) · [evidence](https://github.com/naraya07pedro-spec/fullstack-ai-operations-console/blob/main/docs/EVIDENCE.md) · [CI runs](https://github.com/naraya07pedro-spec/fullstack-ai-operations-console/actions/workflows/verify.yml) |
| **[Bounded Agent Runtime](https://github.com/naraya07pedro-spec/agent-runtime-python)** | Python/FastAPI/PostgreSQL runtime with tenant authorization, persistent approvals, lease-fenced workers and bounded reconciliation after uncertain external effects | [Architecture](https://github.com/naraya07pedro-spec/agent-runtime-python/blob/main/docs/architecture.md) · [failure-injection tests](https://github.com/naraya07pedro-spec/agent-runtime-python/tree/main/tests/failure_injection) · [v2 evidence](https://github.com/naraya07pedro-spec/agent-runtime-python/tree/main/evidence/v2) |
| **[Production Integration Reference](https://github.com/naraya07pedro-spec/production-integration-reference)** | TypeScript/PostgreSQL signed webhook intake, durable identity before side effects, controlled retries and persisted outcomes | [Reliability review](https://github.com/naraya07pedro-spec/production-integration-reference/blob/main/docs/RELIABILITY-REVIEW.md) · [tests](https://github.com/naraya07pedro-spec/production-integration-reference/tree/main/tests) · [CI](https://github.com/naraya07pedro-spec/production-integration-reference/actions/workflows/ci.yml) |

## Live CI status — [evan-naraya-portfolio](https://github.com/naraya07pedro-spec/evan-naraya-portfolio/actions/workflows/quality.yml)

[![Portfolio quality — evan-naraya-portfolio](https://github.com/naraya07pedro-spec/evan-naraya-portfolio/actions/workflows/quality.yml/badge.svg)](https://github.com/naraya07pedro-spec/evan-naraya-portfolio/actions/workflows/quality.yml)

## Live CI status — [fullstack-ai-operations-console](https://github.com/naraya07pedro-spec/fullstack-ai-operations-console/actions/workflows/verify.yml)

[![Verify and package evidence — fullstack-ai-operations-console](https://github.com/naraya07pedro-spec/fullstack-ai-operations-console/actions/workflows/verify.yml/badge.svg)](https://github.com/naraya07pedro-spec/fullstack-ai-operations-console/actions/workflows/verify.yml)

## Live CI status — [agent-runtime-python](https://github.com/naraya07pedro-spec/agent-runtime-python/actions/workflows/verify.yml)

[![verify — agent-runtime-python](https://github.com/naraya07pedro-spec/agent-runtime-python/actions/workflows/verify.yml/badge.svg)](https://github.com/naraya07pedro-spec/agent-runtime-python/actions/workflows/verify.yml)

## Live CI status — [production-integration-reference](https://github.com/naraya07pedro-spec/production-integration-reference/actions/workflows/ci.yml)

[![CI — production-integration-reference](https://github.com/naraya07pedro-spec/production-integration-reference/actions/workflows/ci.yml/badge.svg)](https://github.com/naraya07pedro-spec/production-integration-reference/actions/workflows/ci.yml)

**Verification:** Portfolio 10/10 native tests passed. Console final reviewed commit `654ce3b`: 58/58 system checks, 10 native and 10 Docker browser cases, 10 Docker smoke checks. Bounded Agent Runtime preserved v2 archive: 261 tests, 90.01% coverage. Counts belong to their documented revisions, not automatically to every future change.

![Authentic Full-Stack AI Operations Console screenshot](https://raw.githubusercontent.com/naraya07pedro-spec/evan-naraya-portfolio/main/assets/projects/operations-console/dashboard.png)

*Console uses synthetic data and a deterministic HTTP sandbox. It does **not** run a production LLM; the application has not been separately deployed as a live backend service. The linked portfolio page is live.*

## Other engineering work

- [Knowledge Workflow Runtime](https://github.com/naraya07pedro-spec/varevant.com/tree/main/examples/agentic-systems-lab/knowledge-runtime) — FastAPI, PostgreSQL/pgvector, citations, MCP and OCR. The verified 7 October 2026 revision recorded 134 tests; default retrieval is lexical/extractive.
- [VAREVANT Workflow Engineering](https://github.com/naraya07pedro-spec/varevant.com/tree/main/n8n) — n8n/JavaScript controls for routing, suppression, duplicate prevention, execution ownership and recovery; historical sanitized 117-node export.
- **Client engagements (private):** EZUmrah (Malaysia), six connected travel-operations workflows; PT Geget Gigit (Indonesia), AI-assisted marketing workflow integration. Public reference repositories are separate from these engagements. [Scope notes](CLIENT-WORK.md).

## How I approach backend work

Validate inputs and authority before external effects. Persist identity before dispatch. Distinguish retryable failure from ambiguous results. Test concurrent requests, process termination, cross-tenant access and recovery. Record the limitations alongside the passing tests.

**Stack:** Python · FastAPI · TypeScript · Fastify · Node.js · PostgreSQL · Prisma · SQLAlchemy · React/Next.js · Docker · GitHub Actions · pytest · Vitest · Playwright · REST APIs · webhooks · n8n

Experience since 2026. No invented tenure, production usage, uptime or business ROI.
