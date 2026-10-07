# Evan Naraya — Automation, Integration & Backend Engineering

**Python / FastAPI · n8n · TypeScript · PostgreSQL · REST APIs · AI-assisted systems**

I build automation and backend systems around the parts that usually break once workflows become real: duplicate events, partial commits, retries, stale state, approval boundaries, external API uncertainty, long-running jobs, retrieval lifecycle, and recovery.

**Based in Indonesia · Remote / international work**

---

## Start here — 60 second technical review

| Project | What I built | Evidence to inspect |
|---|---|---|
| **[Bounded Agent Runtime](https://github.com/naraya07pedro-spec/agent-runtime-python)** | Python/FastAPI + PostgreSQL runtime with explicit state, tenant authorization, persistent approvals, fenced workers, bounded reconciliation, crash recovery and observability | **261 passing tests**, **90.01% coverage** in the preserved v2 evidence archive, plus real process-death, PostgreSQL interruption and concurrency tests |
| **[Production Integration Reference](https://github.com/naraya07pedro-spec/production-integration-reference)** | TypeScript/PostgreSQL webhook integration with raw-byte HMAC, durable event identity, atomic reservation, bounded retries and persisted outcomes | Runnable code, HTTP/database tests, signed E2E checks and CI |
| **[VAREVANT Workflow Engineering](https://github.com/naraya07pedro-spec/varevant.com/tree/main/n8n)** | n8n orchestration with live re-checks, suppression, deduplication, claim/verify controls, failure classification and recovery-oriented tests | Historical **117-node** graph, **60 JavaScript Code nodes**, incident cases and saved recovery evidence |
| **[Agentic Automation Systems Lab](https://github.com/naraya07pedro-spec/varevant.com/tree/main/examples/agentic-systems-lab)** | Independent n8n/AI portfolio engineering: effect authorization, bounded polling, RAG lifecycle, redacted observability, model routing and subworkflow contracts | **24 passing tests**, **3 validated n8n workflow JSONs**, six independently implemented contracts |

---

## What I work on

- **Advanced n8n / automation:** deterministic vs agentic boundaries, effect authorization, bounded async jobs, RAG lifecycle, modular subworkflows, recovery-oriented workflow design
- **Automation & integration:** n8n, REST APIs, webhooks, JSON, third-party services, CRM/revenue workflows
- **Backend systems:** Python, FastAPI, Pydantic, TypeScript, JavaScript, PostgreSQL, Supabase
- **Reliability:** idempotency, deduplication, retries, state machines, concurrency boundaries, reconciliation, failure recovery
- **AI-assisted workflows:** structured outputs, tool/function calling, bounded agents, deterministic guardrails, human approval boundaries, model routing and audit-safe observability
- **Delivery:** testing, CI, debugging, VPS operations, technical documentation and implementation handoff

---

## Flagship engineering proof

### 1) Python / FastAPI — Bounded Agent Runtime
**Repository:** [agent-runtime-python](https://github.com/naraya07pedro-spec/agent-runtime-python)

Built to answer one hard question: **what should happen when an external action may have succeeded but the worker dies before the result is committed?**

The runtime persists dispatch intent before external I/O, fences stale workers, stores approvals, tracks ambiguous outcomes separately, and uses bounded read-only reconciliation instead of blind write retries.

**Review these first:**
- [Architecture](https://github.com/naraya07pedro-spec/agent-runtime-python/blob/main/docs/architecture.md)
- [Process-death tests](https://github.com/naraya07pedro-spec/agent-runtime-python/blob/main/tests/failure_injection/test_process_death.py)
- [Tenant isolation tests](https://github.com/naraya07pedro-spec/agent-runtime-python/blob/main/tests/security/test_tenants.py)
- [Database interruption / restore drill](https://github.com/naraya07pedro-spec/agent-runtime-python/blob/main/scripts/recovery_drill.py)

### 2) TypeScript / PostgreSQL — Production Integration Reference
**Repository:** [production-integration-reference](https://github.com/naraya07pedro-spec/production-integration-reference)

A runnable integration reference covering signed webhook intake, immutable event identity, PostgreSQL reservation before side effects, classified retries, partial-failure handling and persisted outcomes.

**Review these first:**
- [Reliability review](https://github.com/naraya07pedro-spec/production-integration-reference/blob/main/docs/RELIABILITY-REVIEW.md)
- [Handler](https://github.com/naraya07pedro-spec/production-integration-reference/blob/main/src/handler.ts)
- [Database reservation](https://github.com/naraya07pedro-spec/production-integration-reference/blob/main/src/idempotency.ts)
- [Tests](https://github.com/naraya07pedro-spec/production-integration-reference/tree/main/tests)

### 3) n8n — Workflow Engineering & Failure Recovery
**Repository:** [varevant.com / n8n](https://github.com/naraya07pedro-spec/varevant.com/tree/main/n8n)

Historical workflow source and testable repair cases around error-path contracts, worker identity, no-send behavior, state preservation, uncertain external actions and runtime compatibility.

**Review these first:**
- [Flagship case study](https://github.com/naraya07pedro-spec/varevant.com/blob/main/n8n/FLAGSHIP-CASE-STUDY.md)
- [Incident catalog](https://github.com/naraya07pedro-spec/varevant.com/tree/main/n8n/incidents)
- [Failure modes](https://github.com/naraya07pedro-spec/varevant.com/blob/main/n8n/FAILURE-MODES.md)
- [Saved recovery evidence](https://github.com/naraya07pedro-spec/varevant.com/blob/main/n8n/runtime-evidence/reproduced-recovery/recorded/report.json)


### 4) Agentic Automation Systems Lab — Advanced n8n / AI Systems Engineering
**Repository:** [Agentic Automation Systems Lab](https://github.com/naraya07pedro-spec/varevant.com/tree/main/examples/agentic-systems-lab)

Advanced n8n/AI architecture work converted into independently implemented, credential-free engineering evidence. The lab focuses on recurring system concerns I repeatedly handle across automation work: external-effect boundaries, async jobs, retrieval lifecycle, observability, model selection and explicit subworkflow contracts.

**Current proof:**
- six reusable JavaScript contracts for effect authorization, bounded polling, RAG lifecycle, observability, model routing and parent/child workflow boundaries;
- **24 passing tests**;
- **3 validated n8n workflow JSONs**;
- hardened rules for deadline-bounded polling, lifecycle-aware retrieval, deterministic write authorization, structured workflow boundaries and secret-safe audit events;
- explicit separation between source-derived patterns and personally implemented/tested work.

**Review first:** [Lab README](https://github.com/naraya07pedro-spec/varevant.com/tree/main/examples/agentic-systems-lab) → [source audit](https://github.com/naraya07pedro-spec/varevant.com/blob/main/examples/agentic-systems-lab/docs/SOURCE-AUDIT.md) → [verification record](https://github.com/naraya07pedro-spec/varevant.com/blob/main/examples/agentic-systems-lab/docs/VERIFICATION.md)

---

## Selected client work

**PT Geget Gigit — Indonesia**  
AI-powered CMO automation for recurring marketing operations.

**EZUmrah — Malaysia**  
End-to-end automation and integration system spanning six core workflows plus shared orchestration.

Client implementations are private. Public repositories above are separate engineering references and internal/historical evidence; they do not substitute for client acceptance or business-result claims. [Client scope notes](CLIENT-WORK.md).

---

## Supporting project

**[BIMMCA Intelligence](https://github.com/naraya07pedro-spec/bimmca-intelligence)** — Supabase-backed browser consumer for sampled AI recommendation metrics, with defensive refresh behavior and offline tests. Public proof covers the consumer layer; ingestion and backend provenance are outside the repository.

---

## How I think about engineering

I prefer a small number of explicit rules over hidden automation magic:

1. **Validate before acting.**
2. **Persist identity before side effects.**
3. **Separate retryable failure from ambiguous outcome.**
4. **Keep AI judgment bounded by deterministic controls.**
5. **Make failures inspectable and recoverable.**
6. **Test the failure path, not only the happy path.**

---

## Contact

- **Email:** [evan@varevant.com](mailto:evan@varevant.com)
- **LinkedIn:** https://www.linkedin.com/in/evannaraya
- **Website:** https://varevant.com
- **GitHub:** https://github.com/naraya07pedro-spec

**Open to remote Automation, Integration, Implementation and Python/API engineering work.**

<sub>Public claims are scoped to what the linked source, tests and CI establish. Experience began in 2026; no production scale, uptime or client ROI is implied by reference repositories.</sub>
