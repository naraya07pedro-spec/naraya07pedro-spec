# Technical interview cheat sheet

Evan Naraya — Python agent runtimes, TypeScript integrations, n8n and reliable workflow systems. Lead with the action boundary, then state what the evidence proves.

| Topic | Useful explanation and actual example |
| --- | --- |
| Python agent execution | [Runtime design notes](https://github.com/naraya07pedro-spec/agent-runtime-python/blob/main/docs/interview-notes.md): persisted dispatch intent, lease-token fencing, exact action approval, typed tool policy, read-only reconciliation, deterministic evals. Real subprocess exits test recovery after claim and after provider success. |
| n8n and JSON | Node mode is part of the item contract. V19 and V9 per-item nodes need one json object; test fallback and no-send paths. |
| API architecture | Validate intake, preserve event identity, reserve before side effects, persist outcome. Backend reference is separate from V6 Sheets orchestration. |
| Webhooks and authentication | Reference verifies HMAC over raw bytes before JSON parsing. A query filter is not auth; historical outcome webhook auth is unverified. |
| Idempotency versus dedup | Idempotency protects the same immutable event across replay. Dedup groups recipient/business identities. Neither implies exactly-once delivery. |
| Concurrency and races | Static-data snapshots can both grant a lease. Sheets reread/claim is not atomic. PostgreSQL unique INSERT picks one reservation winner. |
| PostgreSQL | Parameterized queries, unique event key, RESERVED/SENT/FAILED state; real contention tests run in disposable DB CI. |
| Supabase | BIMMCA queries Gemini rows and refetches on change; coalesces events, shows empty/stale states. RLS and ingestion are outside public proof. |
| Retries and rate limits | Classify 408/429/5xx/transport separately from permanent errors. Bound attempts with backoff/jitter; The TypeScript reference does not coordinate Retry-After; the Python runtime preserves it for classified model/read retries and reconciles every uncertain write. |
| State machines | Distinguish selected, attempted, provider-accepted and committed. NO_SEND is valid; SEND-UNKNOWN requires reconciliation. |
| Partial failure and recovery | Accepted action plus failed commit must stay blocked. Reference markSent fault leaves RESERVED; reconcile before release or retry. |
| Logging and observability | Fixed categories without secrets/payloads in reference logs. A green node is not delivery; saved final execution beats a transient CLI status. |
| LLM boundaries | Model drafts are followed by deterministic shape/copy gates and fallback. Lexical validation is not fact checking; review labels are not enforced approval. |
| Testing and CI | Archived Code fixtures, same-input real-n8n reproduction, HTTP tests, PostgreSQL contention, signed E2E demo; distinguish each scope. |
| Configuration | Cloud $env denial was observed; V3 source removes those reads. No verified expired-token recovery or proven VPS uptime. |

**Python reference demonstration:** walk through the delayed old-worker race and explain why an absent provider lookup never authorizes replay. Show the test and name the availability tradeoff; do not present it as a historical client incident.

**Strongest historical cases:** V19 handler return contract; V2 Cloud configuration; V10.1 worker identity. **Other source-backed cases:** V9 clean no-send; daily action-state preservation. **Client boundary:** Geget Gigit/EZUmrah private scope statements; MAXY scoping, not accepted implementation.

[Flagship](https://github.com/naraya07pedro-spec/varevant.com/blob/main/n8n/FLAGSHIP-CASE-STUDY.md) · [Incident catalog](https://github.com/naraya07pedro-spec/varevant.com/tree/main/n8n/incidents) · [Backend reference](https://github.com/naraya07pedro-spec/production-integration-reference) · [Story bank](INTERVIEW-STORY-BANK.md)
