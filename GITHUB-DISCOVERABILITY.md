# GitHub metadata and discovery: verified gaps and owner actions

**Fresh metadata read: 13 November 2026.** GitHub's repository API was used to inspect descriptions, topics and homepage fields. The **pinned items and their order were not inspected**. The connected GitHub integration here can read metadata but does not expose a safe repository metadata or profile-pin write operation. Recommendations below have **not been applied** to the About UI.

## Prioritized corrections

| Repository | Actual observed discrepancy | Recommended owner edit |
| --- | --- | --- |
| [RepoPilot AI](https://github.com/naraya07pedro-spec/repopilot-ai) | About description claims it turns issues into tested PRs with **secure execution**, although isolated general-purpose execution and autonomous publication are not release-verified. | Description: `Experimental review-first GitHub coding workflow with bounded fixture checks, approval gates, and human-controlled PR publication.` Do not label it a production autonomous agent. |
| [Operations Console](https://github.com/naraya07pedro-spec/fullstack-ai-operations-console) | Has `fastapi` topic, but implemented API is **Fastify**; README and code are Next.js, TypeScript, Prisma/PostgreSQL. | Remove `fastapi` topic. Prefer `fastify`, `nextjs`, `postgresql`, `prisma`, `typescript`, `api-integration` if supported by GitHub topics. |
| [Integration Reference](https://github.com/naraya07pedro-spec/production-integration-reference) | About topics include `fastapi` and `python` although its advertised runtime/contract is TypeScript and Node.js. | Remove `fastapi`; evaluate whether `python` accurately represents any substantive shipped code before removing it. Suggested description: `TypeScript/PostgreSQL integration reference with signed webhooks, atomic deduplication, bounded retries and reconciliation tests.` |
| [Portfolio repo](https://github.com/naraya07pedro-spec/evan-naraya-portfolio) | Description says `Live at evannaraya.netlify.app`, while README identifies `evannaraya.com` as canonical. | Verify the actual DNS/host before changing About description/homepage. Do **not** infer production-readiness from source canonical tags. |
| [VARYN](https://github.com/naraya07pedro-spec/VARYN) | Description starts with typo `ALocal-first`. | Replace with `Experimental local-first Windows AI workspace with owner-approved LLM routing and durable tasks; source/release scope documented per tag.` No claim of a signed release. |
| [Agent Runtime](https://github.com/naraya07pedro-spec/agent-runtime-python) | Topics were populated at latest read with Python, FastAPI, PostgreSQL, idempotency, concurrency, reliability and others. An October note saying topics were empty is **obsolete**. | Keep verified matching topics; no cosmetic edit needed. |

**Why this matters:** wrong framework tags reduce search accuracy; an overly broad description increases the gap between reviewer expectations and what the code/CI has actually established.

## Profile pin recommendation (not an observed pin state)

1. [Bounded Agent Runtime](https://github.com/naraya07pedro-spec/agent-runtime-python)
2. [Production Integration Reference](https://github.com/naraya07pedro-spec/production-integration-reference)
3. [Full-Stack AI Operations Console](https://github.com/naraya07pedro-spec/fullstack-ai-operations-console)
4. [RepoPilot AI](https://github.com/naraya07pedro-spec/repopilot-ai), explicitly marked release candidate
5. [VAREVANT engineering pack](https://github.com/naraya07pedro-spec/varevant.com)
6. [Portfolio source](https://github.com/naraya07pedro-spec/evan-naraya-portfolio), after release/asset review

These are recommendations, not proof of current pin placement. Avoid treating a preview-only repo or archived assets as a separate flagship.

## Manual UI boundary

Visit a repository, open its **About** editor, correct Description/Topics and save. On the GitHub profile, use **Customize your pins** and check final public order. Do not auto-apply settings to unrelated/private repos, change repository visibility, or promise a profile-pin state without reading the UI.

For working, exact-revision engineering evidence rather than metadata, use [ENGINEERING-EVIDENCE.md](ENGINEERING-EVIDENCE.md). Every claim about CI status in that file is dated and tied to a source commit.
