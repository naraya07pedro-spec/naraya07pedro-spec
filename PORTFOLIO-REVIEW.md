# Portfolio review map

Reviewed 2026-10-04 after the Python runtime merged and main CI passed. Source, visible run state and CI take precedence over titles, interface copy or filenames.

| Public repository | Role | Open first | Boundary |
| --- | --- | --- | --- |
| [Profile](https://github.com/naraya07pedro-spec/naraya07pedro-spec) | Recruiter evidence index | [README](README.md) | Client scope remains Level E. |
| [Agent Runtime Python](https://github.com/naraya07pedro-spec/agent-runtime-python) | Flagship Python/agent reliability proof | [Process-death test](https://github.com/naraya07pedro-spec/agent-runtime-python/blob/main/tests/failure_injection/test_process_death.py) → [ownership races](https://github.com/naraya07pedro-spec/agent-runtime-python/blob/main/tests/concurrency/test_ownership.py) → [main CI](https://github.com/naraya07pedro-spec/agent-runtime-python/actions/runs/37224729577) | Executable sandbox/reference; no production or live model-quality claim. |
| [VAREVANT](https://github.com/naraya07pedro-spec/varevant.com) | Flagship n8n source + runtime evidence + delivery surface | [n8n review pack](https://github.com/naraya07pedro-spec/varevant.com/tree/main/n8n) | Historical source/path associations plus labeled real n8n recovery reproduction; exact historical snapshot unverified. |
| [Production Integration Reference](https://github.com/naraya07pedro-spec/production-integration-reference) | Strong backend/reliability proof | Handler → SQL reservation → tests/CI | Synthetic reference; separate historical screenshot gallery. |
| [BIMMCA Intelligence](https://github.com/naraya07pedro-spec/bimmca-intelligence) | Supporting application proof | Browser source → tests → architecture | Consumer only; ingestion, database policies and metric provenance unverified. |
| [3D Assets](https://github.com/naraya07pedro-spec/3d-assets) | Archived asset storage | Asset README | De-emphasized for automation roles. |

The n8n pack stays in VAREVANT. The maintained backend reference remains separate from its older VAREVANT source copy. The Python runtime is a separate bounded execution reference; it does not retroactively establish stronger guarantees for historical n8n workflows. No website redesign was introduced.

## Reviewer paths

**30 seconds:** profile headline → Python runtime evidence table → TypeScript reliability review → VAREVANT source and saved recovery report.

**Python engineering review:** [reliability semantics](https://github.com/naraya07pedro-spec/agent-runtime-python/blob/main/docs/reliability-model.md) → late-worker race → subprocess recovery → [limits](https://github.com/naraya07pedro-spec/agent-runtime-python/blob/main/docs/limitations.md). Main CI verified 211 passing tests, 12/12 deterministic evals, migrations, Docker bootstrap and measured admission at commit `c1f7b899273759ace6b54f34c5fdaeebe9cd4ce2`; this is an artifact result, not a career-history or production-scale claim.

**Five-minute n8n review:** full-canvas overview → V6 matching signals/false branch → V19 historical observations, exact archived node diff, and same-input real n8n reproduction → original claim/error controls and offline tests → concurrency limits → backend SQL/CI → client evidence level.

## Evidence completion

| Gap | Current result | Boundary |
| --- | --- | --- |
| Source → execution | [STRONG V6 workflow/path match](https://github.com/naraya07pedro-spec/varevant.com/blob/main/n8n/runtime-evidence/SOURCE-TO-EXECUTION.md) | Private workflow-ID equality, source positions and visible stop branch. Exact executed Code-node bodies/version unavailable. |
| Failure → patch → passing path | [Reproduced handler recovery](https://github.com/naraya07pedro-spec/varevant.com/blob/main/n8n/runtime-evidence/RECOVERY-CASE.md) | Archived V19 → V19.1 patch rerun in real n8n with identical synthetic input and saved Error/Success snapshots. EXACT for the test; historical imported variant, replay and final Success remain unavailable. |
| Full-canvas visual | [Sanitized original V7 canvas](https://github.com/naraya07pedro-spec/varevant.com/blob/main/n8n/runtime-evidence/images/full-canvas-v7.webp) | Editor topology overview from another revision; small labels, no execution claim. |
| Client technical handoff | [Client notes](CLIENT-WORK.md) remain Level E after full accessible-filesystem and earlier remote searches | No attributable accepted technical handoff or public client system mapping found. |
| Video/PDF | [Review and publication decision](https://github.com/naraya07pedro-spec/varevant.com/blob/main/n8n/runtime-evidence/SEARCH-AND-GAPS.md) | Safe crops possible; separate workflow does not close the priority source/recovery/client gaps. |
| Metadata/pins | [Exact manual steps and copy](GITHUB-DISCOVERABILITY.md) | Current connector cannot change repository metadata or pins; no completed change claimed. |

## Exact material still needed

The [search record and USER MATERIAL REQUIRED table and filesystem access limits](https://github.com/naraya07pedro-spec/varevant.com/blob/main/n8n/runtime-evidence/SEARCH-AND-GAPS.md) specify only: saved V6 execution with its embedded source; saved V19.1 passing-handler execution with final status; and one accepted, public-safe implementation/handoff excerpt for each client. No additional full-canvas image or generic promotional video is needed.
