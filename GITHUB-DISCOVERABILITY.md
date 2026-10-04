# GitHub discoverability: audited settings and exact manual steps

Audited 2026-10-04 after the Python runtime merged. Repository descriptions/topics were read. The connected GitHub tools do not expose repository-metadata or profile-pinning writes, so these settings have **not been changed**. The public profile showed repository cards including archived `3d-assets`; a custom pin order could not be verified through the connector.

README first-screen links lead to the Python runtime, TypeScript integration reference and VAREVANT source/recovery pack. Keep the evidence-led profile headline.

## Repository About settings

Open each repository → **About gear** → edit Description and Topics → **Save changes**. Enter each topic as a separate tag. The [official topic instructions](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/classifying-your-repository-with-topics) describe that control.

| Repository | Description to paste | Topics to use |
| --- | --- | --- |
| [agent-runtime-python](https://github.com/naraya07pedro-spec/agent-runtime-python) | Keep the current description: Production-style Python runtime for bounded AI agents: tool execution, state, retries, guardrails, observability, and failure recovery. | Add `python`, `fastapi`, `pydantic`, `postgresql`, `agent-runtime`, `ai-agents`, `idempotency`, `failure-recovery`, `evals`, `observability`; topics are currently empty. |
| [varevant.com](https://github.com/naraya07pedro-spec/varevant.com) | n8n workflow engineering, API integrations, tested control logic, failure handling, and bounded AI automation. | `n8n`, `workflow-automation`, `api-integration`, `webhooks`, `automation`, `ai-agents`, `postgresql`, `supabase`, `reliability-engineering`, `javascript` |
| [production-integration-reference](https://github.com/naraya07pedro-spec/production-integration-reference) | Runnable TypeScript/PostgreSQL reference for signed webhooks, idempotency, retries, and safe external side effects. | `typescript`, `postgresql`, `webhooks`, `idempotency`, `api-integration`, `retries`, `integration-testing`, `backend` |
| [bimmca-intelligence](https://github.com/naraya07pedro-spec/bimmca-intelligence) | Supabase-backed AI monitoring and decision-support dashboard with documented automation architecture. | Existing `ai-monitoring`, `api-integration`, `automation`, `dashboard`, `javascript`, `postgresql`, `supabase` already fit; no change needed. |
| [naraya07pedro-spec](https://github.com/naraya07pedro-spec/naraya07pedro-spec) | Evan Naraya — AI Automation & Systems Engineering: Python, TypeScript, APIs, and reliable workflow systems. | Optional `python`, `typescript`, `automation`, `api-integration`, `portfolio` |

The VAREVANT and TypeScript descriptions are optional refinements; their existing descriptions and topics are already relevant. The runtime description is already appropriate and needs only topics. Profile description/topics are currently empty. VAREVANT's homepage is already `https://varevant.com`; keep it. The backend and BIMMCA homepage fields are empty; no unverified live-demo URL is proposed.

## Pins

1. Open [Evan's profile](https://github.com/naraya07pedro-spec).
2. Click **Customize your pins** in the Popular repositories/Pinned area.
3. Select `agent-runtime-python`, `production-integration-reference`, `varevant.com`, and `bimmca-intelligence`; optionally include `naraya07pedro-spec`.
4. Click **Save pins**.
5. Drag the pins by their upper-right handles into that order, then visually check the first row.

The [official pin instructions](https://docs.github.com/en/account-and-profile/how-tos/profile-customization/pinning-items-to-your-profile) describe selection and dragging. Keep archived assets out of the automation review's first row.

## Verify afterward

Refresh the public repository pages and profile. Check the About text/topics, homepage and pin order. These are manual settings pending Evan's action; published README/navigation improvements are separate from them.
