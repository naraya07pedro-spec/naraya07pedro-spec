# Evan Naraya

**Automation & Integration Engineer** · Indonesia · Open to remote roles

Workflow automation, API/webhook integrations, and database-backed state, with an emphasis on validation, failure handling, debugging, and tests.

[Website](https://varevant.com) · [LinkedIn](https://www.linkedin.com/in/evannaraya) · [Contact](mailto:evan@varevant.com)

## Engineering proof

| Start here | What you can inspect |
| --- | --- |
| **1. [Production Integration Reference](https://github.com/naraya07pedro-spec/production-integration-reference)** | TypeScript webhook handler, HMAC verification, PostgreSQL idempotency, bounded retries, [tests](https://github.com/naraya07pedro-spec/production-integration-reference/tree/main/tests), and [CI](https://github.com/naraya07pedro-spec/production-integration-reference/actions/workflows/ci.yml). |
| **2. [VAREVANT engineering](https://github.com/naraya07pedro-spec/varevant.com)** | [Runnable lead-routing reference](https://github.com/naraya07pedro-spec/varevant.com/tree/main/examples/reliable-lead-routing): deterministic gates, bounded classification, manual-review fallback, and retry behavior. [Technical review guide](https://github.com/naraya07pedro-spec/varevant.com/blob/main/docs/TECHNICAL-REVIEW.md). |
| **3. [BIMMCA Intelligence](https://github.com/naraya07pedro-spec/bimmca-intelligence)** | JavaScript dashboard with a Supabase query and Realtime subscription. The public code covers the browser consumer; upstream ingestion and database policies require separate evidence. |

## Reliability and evidence

[Historical n8n screenshots](https://github.com/naraya07pedro-spec/production-integration-reference/tree/main/docs/evidence) show separate VAREVANT workflow paths, a successful manual test, execution history, and a visible failure. They do not validate the flagship's inactive synthetic n8n JSON.

The flagship also includes a [debugging case grounded in commit history](https://github.com/naraya07pedro-spec/production-integration-reference/blob/main/docs/debugging-case.md), real PostgreSQL CI tests, and a signed synthetic HTTP demo.

These artifacts support inspection of implementation and debugging decisions. They do not establish production traffic, uptime, client impact, or business outcomes.
