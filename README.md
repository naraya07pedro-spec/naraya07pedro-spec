# Evan Naraya

**Automation & Integration Engineer**  
Indonesia · Open to remote and international technical roles

I build reliable workflow automation, API integrations, backend orchestration, and controlled AI-assisted systems. My focus is practical implementation: turning operational requirements into systems that are inspectable, testable, and safer to run.

[![Website](https://img.shields.io/badge/Website-varevant.com-0A0A0A?style=flat-square)](https://varevant.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Evan%20Naraya-0A0A0A?style=flat-square)](https://www.linkedin.com/in/evannaraya)
[![Email](https://img.shields.io/badge/Email-evan%40varevant.com-0A0A0A?style=flat-square)](mailto:evan@varevant.com)
[![Remote](https://img.shields.io/badge/Open%20to-Remote%20Technical%20Roles-0A0A0A?style=flat-square)](#open-to)

## Engineering focus

- **API & webhook integration** — request/response flows, validation, routing, failure handling, and system-to-system handoffs.
- **Workflow automation** — n8n-oriented orchestration, deterministic gates, state transitions, retries, and operational safeguards.
- **Backend systems** — JavaScript, PostgreSQL/Supabase-backed state, structured payloads, and implementation logic.
- **Reliable AI-assisted workflows** — AI is bounded by validation, confidence thresholds, permissions, and human-review fallbacks.
- **Technical QA & documentation** — making behavior reviewable through tests, architecture notes, production-safety boundaries, and handoff documentation.

**Core technical surface:** JavaScript · Node.js · REST APIs · Webhooks · PostgreSQL · Supabase · n8n orchestration · Git · JSON · deterministic validation · retries · deduplication · logging patterns · human approval boundaries

## Selected engineering work

| Project | What it demonstrates | Review |
| --- | --- | --- |
| **Reliable Lead Routing** | Testable Node.js reference implementation for normalization, validation, suppression, region gates, idempotency, bounded classification, manual-review fallback, and retry behavior. | [README](https://github.com/naraya07pedro-spec/varevant.com/tree/main/examples/reliable-lead-routing) · [Code](https://github.com/naraya07pedro-spec/varevant.com/blob/main/examples/reliable-lead-routing/workflow.js) · [Tests](https://github.com/naraya07pedro-spec/varevant.com/blob/main/examples/reliable-lead-routing/workflow.test.js) |
| **BIMMCA Intelligence** | Supabase-backed monitoring and decision-support application fed by a structured n8n monitoring architecture. | [Repository](https://github.com/naraya07pedro-spec/bimmca-intelligence) |
| **VAREVANT Engineering** | Public engineering surface for workflow automation, backend integration, bounded AI systems, technical review, production-safety thinking, and white-label implementation. | [Repository](https://github.com/naraya07pedro-spec/varevant.com) · [Technical Review](https://github.com/naraya07pedro-spec/varevant.com/blob/main/docs/TECHNICAL-REVIEW.md) |

## Five-minute technical review path

If you are reviewing my work for an engineering role, this is the fastest path:

1. **Inspect the implementation:** [`examples/reliable-lead-routing/`](https://github.com/naraya07pedro-spec/varevant.com/tree/main/examples/reliable-lead-routing)
2. **Run the tests:** `node --test examples/reliable-lead-routing/workflow.test.js`
3. **Review system decisions:** [`docs/TECHNICAL-REVIEW.md`](https://github.com/naraya07pedro-spec/varevant.com/blob/main/docs/TECHNICAL-REVIEW.md)
4. **Review production boundaries:** [`docs/PRODUCTION-SAFETY.md`](https://github.com/naraya07pedro-spec/varevant.com/blob/main/docs/PRODUCTION-SAFETY.md)
5. **Inspect a Supabase-backed application:** [`bimmca-intelligence`](https://github.com/naraya07pedro-spec/bimmca-intelligence)

## How I approach implementation

```text
Understand the current process
        ↓
Identify the failure / bottleneck
        ↓
Separate deterministic controls from probabilistic logic
        ↓
Build the smallest reliable implementation
        ↓
Test failure paths, retries, duplicates, and fallbacks
        ↓
Document assumptions and production boundaries
```

I prefer systems where critical rules remain deterministic and AI is used only where interpretation adds value. That means hard gates, validation, suppression, idempotency, permissions, and safety checks should not depend on model output.

## What I can contribute

- Building and debugging API / webhook integrations
- Implementing operational workflows and internal automation
- Connecting SaaS tools, databases, and backend services
- Designing deterministic validation and routing logic
- Investigating failure paths and improving reliability
- Creating technical documentation and handoff material
- Supporting implementation-heavy customer or developer workflows

## Open to

I am particularly interested in remote roles such as:

- **Integration Engineer / Integration Specialist**
- **Implementation Engineer / Technical Implementation**
- **Technical Support Engineer / Developer Support**
- **Automation Engineer / Workflow Automation**
- **Technical Operations / Solutions Implementation**

I am based in Indonesia and open to global remote teams, APAC roles, and international contractor arrangements where eligible.

## Public proof boundaries

The repositories linked above intentionally expose reviewable engineering patterns without publishing credentials, private client data, confidential workflow exports, or unsupported client/outcome claims.

---

**Best place to start:** [Reliable Lead Routing reference implementation](https://github.com/naraya07pedro-spec/varevant.com/tree/main/examples/reliable-lead-routing)  
**Business / engineering site:** [varevant.com](https://varevant.com)  
**LinkedIn:** [linkedin.com/in/evannaraya](https://www.linkedin.com/in/evannaraya)  
**Contact:** [evan@varevant.com](mailto:evan@varevant.com)
