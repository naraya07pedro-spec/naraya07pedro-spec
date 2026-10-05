# AI Automation & Systems Engineering — Python · TypeScript · APIs

**Evan Naraya** · Indonesia · Remote

I build agent runtimes and API-connected workflows around explicit state, validated actions and inspectable recovery paths. Review the Python/PostgreSQL agent runtime, the TypeScript integration reference, and VAREVANT’s historical n8n source with a separately reproduced recovery test.

## Thirty second review

| Time | Open | What it establishes |
| --- | --- | --- |
| 0–10 seconds | [Python agent runtime: source, tests and CI](https://github.com/naraya07pedro-spec/agent-runtime-python) | Tenant-bound access, fenced ownership, persistent approvals and tested process/database recovery |
| 10–20 seconds | [TypeScript integration reliability](https://github.com/naraya07pedro-spec/production-integration-reference/blob/main/docs/RELIABILITY-REVIEW.md) | Signed intake, immutable identity, PostgreSQL contention, retries and partial-failure tests |
| 20–30 seconds | [VAREVANT architecture and repairs](https://github.com/naraya07pedro-spec/varevant.com/blob/main/n8n/FLAGSHIP-CASE-STUDY.md) · [saved n8n recovery report](https://github.com/naraya07pedro-spec/varevant.com/blob/main/n8n/runtime-evidence/reproduced-recovery/recorded/report.json) | Historical orchestration source and same-input reproduced recovery; exact historical production recovery remains unverified |

## Engineering ownership to inspect

- **Python agent runtime:** FastAPI/Pydantic contracts, PostgreSQL state and events, tenant authorization, fenced leases, persistent approvals and bounded read-only reconciliation. [Process-death tests](https://github.com/naraya07pedro-spec/agent-runtime-python/blob/main/tests/failure_injection/test_process_death.py) · [tenant isolation tests](https://github.com/naraya07pedro-spec/agent-runtime-python/blob/main/tests/security/test_tenants.py) · [database interruption/restore drill](https://github.com/naraya07pedro-spec/agent-runtime-python/blob/main/scripts/recovery_drill.py) · [verified v2 main CI](https://github.com/naraya07pedro-spec/agent-runtime-python/actions/runs/37262739926). The GitHub adapter uses synthetic contract tests; live authenticated provider recovery and live model quality remain unverified. Admission measurements describe the CI runner, not production capacity.

- **n8n:** historical 117-node graph, 60 JavaScript Code nodes, live rereads, claim/commit checks, suppression, bounce handling and deterministic copy gates. Counts describe source structure.
- **Debugging:** per-item fallback and no-send contract repairs, Cloud environment compatibility and worker identity across queue reads. [Five traceable cases and supporting tests](https://github.com/naraya07pedro-spec/varevant.com/tree/main/n8n/incidents).
- **TypeScript integrations:** raw-byte HMAC, reservation before HTTP side effects, bounded classified retries, persisted states and real PostgreSQL/signed E2E checks in CI. Reference/demo implementation.
- **Supabase:** [BIMMCA consumer](https://github.com/naraya07pedro-spec/bimmca-intelligence) and [refresh-state hardening](https://github.com/naraya07pedro-spec/bimmca-intelligence/blob/main/docs/DEBUGGING-CASE.md); backend ingestion remains outside public proof.

## Client and implementation scope

PT Geget Gigit, Indonesia: AI-powered CMO automation for marketing operations. EZUmrah, Malaysia: end-to-end automation/integration for an Umrah travel business. These are self-reported private engagement scopes; public internal/reference work is separate. MAXY Academy is reported outbound implementation scoping, not a verified completed build. [Client scope and evidence](CLIENT-WORK.md).

**Core:** Python · FastAPI · Pydantic · TypeScript · JavaScript · n8n · REST APIs · Webhooks · PostgreSQL · Supabase · agent runtimes · stateful workflows · failure recovery · deterministic evals · observability · testing · GitHub CI

[Agent-runtime design reasoning](https://github.com/naraya07pedro-spec/agent-runtime-python/blob/main/docs/interview-notes.md) · [Interview stories](INTERVIEW-STORY-BANK.md) · [Technical cheat sheet](TECHNICAL-CHEAT-SHEET.md) · [Portfolio review](PORTFOLIO-REVIEW.md)

[evan@varevant.com](mailto:evan@varevant.com) · [LinkedIn](https://www.linkedin.com/in/evannaraya) · [varevant.com](https://varevant.com)

Historical captures, archived code, reproduced tests and private engagement scope are labeled separately. Experience began in 2026. No production volume, uptime, ROI, client acceptance or exactly-once delivery claim is implied.
