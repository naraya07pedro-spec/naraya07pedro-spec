# Interview story bank

Practice anchors for Evan Naraya. Use the short answer as a starting point, then explain the actual source when asked. The longer answers aim for 90–120 seconds at an unhurried pace. Do not memorize a result that the evidence does not support.

Historical editor observations, inferred source bindings, executed synthetic tests, repository repairs and client scoping are labeled separately. Five traceable historical/reported repair cases anchor the bank; no claim of ten production incidents is made.


## 1 Tell me about a difficult automation failure

**Evidence type:** Historical failure plus reproduced engine recovery. [Inspect the evidence](https://github.com/naraya07pedro-spec/varevant.com/blob/main/n8n/incidents/incident-01-handler-contract.md).

### Short answer 30 to 45 seconds

One failure was in an n8n error handler, so the fallback itself was breaking. The node ran once per item, but the archived code returned an array. I changed it to one json object and kept the original context. In a separate pinned n8n test, the same input failed before the change and reached saved success afterward. That proves the repair mechanism. I keep it separate from the historical screenshot because I do not have that exact saved execution.

### Deep answer 90 to 120 seconds

The useful detail is that the error was not the original search failure. The branch intended to handle that failure also broke. I checked the node mode and output shape before changing the surrounding graph. The archived V19 handler ran once per item but returned an array containing a json object. The V19.1 repair returns the object directly, clears stale search HTML and marks the search failure while preserving the rest of the item.

For verification, I used one synthetic input in a five-node workflow with pinned n8n. I changed only the handler body. I then read the final saved execution state from the test database rather than relying on the CLI's temporary running status. The before execution is error; the after execution is success, and the context is preserved.

There is a boundary I would explain clearly: the historical screenshot and reproduced engine report different validator messages. Also, a later historical green path ends with no candidate. It does not prove a successful send. My evidence supports the contract repair and the reproduced recovery, not an exact reconstruction of a production incident. I would now make the expected item contract explicit and test both the normal and fallback paths before import.

### Follow up questions

**Why?** The fallback must obey the same runtime contract as the normal path.

**What was the root cause?** An array was returned from a per-item Code node.

**What tradeoff did you make?** I changed one handler instead of replacing the graph.

**What would you change now?** Add return-contract checks before import, including error paths.

**How did you verify the fix?** Same input, one changed body, final saved Error and Success records.

**How did you prevent recurrence?** Keep source-contract tests and the pinned engine recovery in CI.

## 2 Tell me about a duplicate execution problem

**Evidence type:** Historical state-loss repair; duplicate action not proved. [Inspect the evidence](https://github.com/naraya07pedro-spec/varevant.com/blob/main/n8n/incidents/incident-05-daily-state.md).

### Short answer 30 to 45 seconds

In a separate scheduled repository process, a fresh observation overwrote the daily record and removed the marker that an action had already happened. That could weaken the daily action guard. I changed the writer to merge prior state, preserve the action fields and keep a bounded history, then restored the record. The repair is in Git. I can show the state-loss defect and preservation behavior, but I do not claim that a duplicate customer action actually happened.

### Deep answer 90 to 120 seconds

I would separate two things here: losing duplicate protection and observing an actual duplicate action. The public history proves the first. A daily record tracked an action that had already been taken. A later scheduled observation generated a new object with NO_ACTION and replaced that record, so the previous action fields disappeared.

The root cause was ownership of the state. Fresh observations should update what was seen, but they should not erase the decision already committed for that day. The patch loads the existing file, copies protected action and proposal fields into the fresh observation, and appends a bounded run history. Another commit restores the missing action record. The date calculation also changes to Asia/Jakarta, although I cannot prove that timezone caused this specific overwrite.

I verified the preservation function with an existing action marker and a new observation. The marker remains, and the observation history is updated. The commits and merged PR make that repair inspectable.

I would still avoid calling the file a distributed lock. Two writers can race, and field preservation does not solve atomic replacement or concurrent scheduling. If the system needed several workers, I would move authoritative action reservation into transactional storage. The interview result is a verified state-preservation repair, with a precise limit on what it proves.

### Follow up questions

**Why?** An action marker must survive later observations.

**What was the root cause?** The writer replaced the whole object without merging existing state.

**What tradeoff did you make?** A bounded merge was appropriate for the current file workflow.

**What would you change now?** Use transactional reservation if several workers must coordinate.

**How did you verify the fix?** Inspect the repair/restoration commits and run the merge regression.

**How did you prevent recurrence?** Preserve authoritative fields and test repeated writes on the same date.

## 3 Tell me about a concurrency problem

**Evidence type:** Reported worker defect plus full-selector fixtures; lock limit explicit. [Inspect the evidence](https://github.com/naraya07pedro-spec/varevant.com/blob/main/n8n/incidents/incident-03-worker-identity.md).

### Short answer 30 to 45 seconds

My strongest worker case is about identity and lane ownership. The queue read replaced the trigger item, so the selector could lose whether it belonged to lane A or B and select nothing. The repair reads the Acquire node from the current execution. Full-selector fixtures select separate batches for the two lanes and zero rows when identity is missing. I also tested a limitation in the older lease: independent static-data snapshots can both acquire it, so I do not call that a distributed lock.

### Deep answer 90 to 120 seconds

The archived worker repair explains why a successful execution can do no useful work. The Acquire node emits the worker lane, but Read Prospect Master then emits spreadsheet rows instead of the lease item. If the selector relies only on static lease data and that state is unavailable, it has no lane identity. It correctly fails closed, but every candidate is skipped.

The V10.1 selector reads the lane-specific Acquire node that actually executed. It catches the sibling that did not execute and keeps an execution-bound static lease lookup only as fallback. I tested the full archived selector with a fixed clock and 100 valid synthetic rows. Lane A selects 25; lane B selects 25 different rows; missing identity selects zero. Those numbers describe the fixture, not historical email throughput.

Selection and exclusion are different guarantees. The older V6 static-data lease blocks another owner within a shared object, but another test gives two independent snapshots and both grant ownership. Also, a Sheets claim and reread is not an atomic compare-and-set.

For a stronger reservation boundary, my separate backend reference uses a PostgreSQL unique constraint and INSERT ON CONFLICT. Its database tests run contenders in CI. I would use that kind of durable reservation for shared external actions, while still keeping lane identity explicit through every node that changes the input shape.

### Follow up questions

**Why?** Lane ownership must remain explicit after an input-replacing node.

**What was the root cause?** The queue read removed the upstream identity; static state was a fragile carrier.

**What tradeoff did you make?** Read the executed node context while keeping a compatibility fallback.

**What would you change now?** Use a database reservation for cross-worker exclusion.

**How did you verify the fix?** Execute the entire selector and test missing identity, both lanes and fallback.

**How did you prevent recurrence?** Keep identity tests; do not equate disjoint selection with atomic claims.

## 4 Tell me about a retry problem

**Evidence type:** Tested historical control and separate reference behavior. [Inspect the evidence](https://github.com/naraya07pedro-spec/varevant.com/blob/main/n8n/FAILURE-MODES.md).

### Short answer 30 to 45 seconds

The retry problem I can demonstrate is an uncertain external action. If Gmail times out after accepting a send, repeating it can send twice. My historical control classifies that as SEND-UNKNOWN and requires reconciliation; automatic Gmail retry is disabled. In the separate HTTP reference, retries are bounded and reuse one idempotency key, but they are safe only if the provider honors that key. I have tests for these behaviors, not a verified historical duplicate-send incident.

### Deep answer 90 to 120 seconds

I start by asking whether the failed operation was a read or an external side effect. A failed read can often be repeated. A send is different because a timeout can happen after the provider accepted it. The absence of a response does not prove the absence of an action.

In the historical V6 source, automatic Gmail retry is disabled. The send-error classifier puts a socket timeout into an ambiguous-outcome state and marks it for reconciliation. A fixture verifies that output. A permanent recipient rejection produces a stop marker, while sender quota or configuration errors halt the lane for that run. The text classification is heuristic, so it still needs investigation.

The backend reference demonstrates a separate policy. It retries transport failures and 408, 429 and 5xx responses within bounded attempts, exponential delay and jitter. It preserves one downstream idempotency key across attempts. Other errors are not blindly retried. Tests check both attempt counts and delays.

The tradeoff is slower recovery when the outcome is unclear. I prefer a visible hold over silently repeating a possibly accepted action. I would now add provider-specific reconciliation and rate-limit coordination where the contract supports it. I would not describe these fixtures as evidence that I recovered a historical Gmail duplicate or implemented exactly-once delivery.

### Follow up questions

**Why?** A timeout does not establish that the action failed.

**What was the root cause?** Provider acceptance and response delivery can diverge.

**What tradeoff did you make?** Hold uncertain Gmail actions instead of maximizing automatic retries.

**What would you change now?** Add provider-specific reconciliation and Retry-After coordination.

**How did you verify the fix?** Test ambiguity classification, stable keys, attempt bounds and delays.

**How did you prevent recurrence?** Persist uncertainty and require a verified retry decision.

## 5 Tell me about an API integration failure

**Evidence type:** Cloud configuration failure and search fallback contract. [Inspect the evidence](https://github.com/naraya07pedro-spec/varevant.com/blob/main/n8n/incidents/incident-02-cloud-environment.md).

### Short answer 30 to 45 seconds

An early n8n workflow depended on environment variables that the Cloud runtime denied. It failed before the integration could do its useful work. I checked the hosting contract and the failing policy node, then used the runtime-native revision that removes those reads. A fixture deliberately blocks environment access: the old body fails and the revised body emits valid items. I can prove that compatibility repair, but not a full historical provider-success run.

### Deep answer 90 to 120 seconds

This case taught me to separate the API contract from the hosting contract. The visible error was access to env vars denied in Load Policy plus Territory Control. If I had treated it as a search-provider outage, I would have debugged the wrong layer.

The archived V2 export contains environment reads in Code and HTTP settings. The V3 Runtime Native artifact removes all of them and uses runtime-native defaults and inputs. It changes more than one node, so I would not describe it as a one-line patch. The source association is strong, but I do not have the exact historical saved workflow snapshot.

I executed the two archived policy bodies with an environment proxy that throws on access. The V2 body fails; the V3 body returns object-backed items without accessing it. That is a narrow, reproducible result. It does not test the whole provider graph or prove valid credentials and endpoint availability.

For a current integration, I would check runtime configuration support, credential binding, request shape, timeouts, response shape and failure routes before enabling a schedule. The search-handler case reinforces the last part: the fallback needs a valid item contract too. My separate backend reference adds raw-byte signed intake and explicit validation, but it is not a claim about how the historical n8n Cloud deployment was secured.

### Follow up questions

**Why?** Debug the first failing layer rather than assuming the provider is down.

**What was the root cause?** The configuration depended on denied runtime environment access.

**What tradeoff did you make?** Use the supported configuration surface rather than weakening runtime restrictions.

**What would you change now?** Add a preflight for runtime, credentials and response contracts.

**How did you verify the fix?** Execute both archived policy bodies with environment access denied.

**How did you prevent recurrence?** Keep compatibility and failure-path checks before publishing workflows.

## 6 Tell me about a schema or payload problem

**Evidence type:** Historical per-item contract failure; no schema-migration claim. [Inspect the evidence](https://github.com/naraya07pedro-spec/varevant.com/blob/main/n8n/incidents/incident-04-no-send-contract.md).

### Short answer 30 to 45 seconds

My clearest payload case is the no-send branch. It was expected to return a diagnostic item, but the Code node ran once per item and returned an array. The historical capture shows that node failing. The next source revision returns one json object and preserves NO_SEND and gmail_attempted false. The regression checks the shape and retained context. I would describe this as a payload contract repair, not an unverified database schema migration.

### Deep answer 90 to 120 seconds

The no-send branch matters because it is an expected business outcome. A queue can be empty, suppressed or outside the sending window. The workflow should explain that and stop cleanly. In the historical V9 capture, the false branch reaches SINGLE No Sendable Rows and then throws a json-object error.

The archived node runs once for each item but returns an array. The following V10 source returns a single json object and adds a diagnostic message for sender budget exhaustion or lack of eligible rows. It keeps the original fields and explicitly records that Gmail was not attempted.

I ran both archived bodies with synthetic input. The before result is an array; the corrected result is an object with retained context, NO_SEND and gmail_attempted false. That checks the return contract without contacting Gmail or Sheets. I do not have a saved historical V10 execution proving the whole branch succeeded after import.

I would now document item shape and node mode together. For integration events, I would validate fields before reserving or sending, as the separate backend reference does. I would also test empty and failure paths instead of focusing only on happy-path data. A schema version or contract migration should be supported by an actual before/after contract; I would not add that story merely because JSON was involved.

### Follow up questions

**Why?** An expected no-op still has to be a valid runtime output.

**What was the root cause?** Array return conflicted with per-item Code mode.

**What tradeoff did you make?** Keep the clean stop and add diagnostics; do not force a send.

**What would you change now?** Document item shape and node mode together.

**How did you verify the fix?** Run both source bodies and assert context plus explicit no-send fields.

**How did you prevent recurrence?** Test empty, normal and error branches before import.

## 7 Tell me about an authentication or rate limit problem

**Evidence type:** Honest history boundary plus tested configuration/quota handling. [Inspect the evidence](https://github.com/naraya07pedro-spec/varevant.com/blob/main/n8n/incidents/incident-02-cloud-environment.md).

### Short answer 30 to 45 seconds

I do not have a documented expired-token recovery that I would claim as a real incident. The closest verified configuration failure is n8n Cloud denying environment access. I also have a source-level quota safeguard: the send-error classifier halts the sender lane for that run, and a fixture verifies it. In the HTTP reference, 401 stops after one attempt while 429 is retryable within a bound. Token rotation and provider rate-limit coordination would still need deployment-specific work.

### Deep answer 90 to 120 seconds

I would be clear about the evidence first. My archive does not establish that a token expired, was refreshed and recovered in a historical production execution. I would not turn a quota fixture into that story. The directly observed configuration case is environment access denied in n8n Cloud.

For the controls I can show, the historical send-error classifier recognizes sender-related failures and halts the lane for the run. A synthetic quota-exceeded input verifies the halt marker. That control is useful, but broad error-text matching can misclassify the provider response, and a fresh execution still needs durable stop state.

The backend reference tests HTTP categories more explicitly. A 401 is a permanent error under its current policy and gets one attempt. A 429 is retryable within the attempt bound. Exponential delay and jitter are implemented; Retry-After coordination and distributed rate limiting are not.

In a real authentication incident, I would stop affected actions, check credential scope and expiration without logging secrets, restore access through the provider's supported flow and verify a controlled request before resuming. For rate limits, I would inspect the actual provider contract and coordinate capacity. Those are the steps I would take, not claims about work the historical evidence proves I already completed. My strength here is explicit failure classification and knowing where automatic retry is unsafe.

### Follow up questions

**Why?** Configuration, authentication and quota failures need different remedies.

**What was the root cause?** Expired-token root cause is UNKNOWN; Cloud access denial is observed.

**What tradeoff did you make?** Stop the affected lane rather than repeatedly consuming failed attempts.

**What would you change now?** Add provider-specific refresh and rate-limit coordination when required.

**How did you verify the fix?** Show the Cloud fixture, quota halt test and 401/429 retry tests.

**How did you prevent recurrence?** Do not log credentials; persist relevant stop state and verify before resuming.

## 8 Tell me about a partial failure

**Evidence type:** Controlled reference test; historical send recovery not claimed. [Inspect the evidence](https://github.com/naraya07pedro-spec/production-integration-reference/blob/main/docs/RELIABILITY-REVIEW.md).

### Short answer 30 to 45 seconds

I test the case where an external action succeeds but the database write fails afterward. In my backend reference, the event is reserved first. When markSent is forced to fail after downstream success, the test confirms that RESERVED stays blocked. I do not release it and repeat the action. The next step is provider reconciliation. It is a controlled fault test, not a customer incident, and it shows why provider and database writes cannot be treated as one transaction.

### Deep answer 90 to 120 seconds

The dangerous part is the gap between the provider accepting an action and the system recording success. A database transaction cannot include an unrelated external API. If success persistence fails, treating that as an ordinary failed send can repeat an action that already happened.

My reference handler reserves the event before calling downstream. In the partial-commit test, the injected downstream succeeds and markSent then throws a database-unavailable error. The handler rejects, but the reservation remains RESERVED. The test asserts that state. It demonstrates the recovery boundary using a memory test store; the PostgreSQL reservation implementation and database contention tests are separate evidence in CI.

Leaving RESERVED blocked is deliberate. It costs an automatic recovery path, but it preserves the information that an action may have occurred. I would reconcile against the provider's result and the immutable event identity before deciding how to update state or retry. Deleting the reservation just to unblock processing would remove the protection.

The historical n8n workflow has a related boundary: Gmail, Sheet commits and log appends are separate operations, and the commit verifier checks the saved provider result against the reread row. That does not make them atomic. I would now add a provider-aware reconciliation tool and an auditable decision record. I would still describe the executed backend example as a controlled test, not historical production recovery.

### Follow up questions

**Why?** An accepted action can outlive a failed database write.

**What was the root cause?** There is no transaction spanning the provider and local persistence.

**What tradeoff did you make?** Keep the reservation blocked and accept manual reconciliation.

**What would you change now?** Add a provider-aware reconciliation tool with an audited decision.

**How did you verify the fix?** Force markSent failure after downstream success and assert RESERVED.

**How did you prevent recurrence?** Reserve before acting and never automatically delete uncertain state.

## 9 Tell me about a system you designed end to end

**Evidence type:** Source-backed VAREVANT architecture; deployment limits explicit. [Inspect the evidence](https://github.com/naraya07pedro-spec/varevant.com/blob/main/n8n/FLAGSHIP-CASE-STUDY.md).

### Short answer 30 to 45 seconds

My strongest inspectable system is the VAREVANT revenue workflow. It connects discovery and evidence checks to queue handoff, live-state validation, claims, Gmail actions and result verification, with bounce and outcome handling around it. I own the automation design and the reliability work shown in the source. The public export has 117 nodes and 60 JavaScript Code nodes. Those are structure counts. I can walk through the contracts and tests without claiming that this sanitized review copy is a live production deployment.

### Deep answer 90 to 120 seconds

I start with the boundary between an opportunity and the next external action. Discovery produces candidate evidence; qualification and copy gates decide whether it can enter the queue. The dispatcher then rereads live state, checks suppression and prior provider IDs, records an execution-specific claim, verifies it and uses a frozen payload for the send. Afterward, the commit verifier compares the reread row with the stored provider result. Bounce, reply and outcome paths influence future eligibility.

The selected historical source makes that design inspectable. It has 117 nodes and 60 Code nodes, but I would use the counts only to describe structure. Several entrypoints live in one graph; that does not prove five independently deployed services. The public copy is inactive, removes credentials and disables external nodes.

I also explain the limits. Sheets claims are not atomic, a static-data lease is not a distributed lock, and a copy gate is not a semantic fact checker. Human-review labels do not prove an enforced approval workflow.

The separate TypeScript/PostgreSQL reference shows a stronger event-reservation boundary, signed HTTP intake and tested retries. BIMMCA supplies supporting Supabase consumer code and refresh-state tests. I keep those implementations separate rather than pretending they all ran behind one client deployment. A reviewer can inspect the actual source, the tests, the reproduced recovery and the remaining evidence gaps.

### Follow up questions

**Why?** The design follows state and external-action boundaries.

**What was the root cause?** The operating risks are stale eligibility, unclear ownership and incomplete commits.

**What tradeoff did you make?** Keep deterministic gates while using AI for bounded language tasks.

**What would you change now?** Move shared reservations into transactional storage where required.

**How did you verify the fix?** Use source extraction, control tests, saved recovery and CI.

**How did you prevent recurrence?** Document contracts, failure states and recovery limits beside the code.

## 10 Tell me about a client requirement that changed

**Evidence type:** MAXY scope-planning self report; implementation/acceptance unverified. [Inspect the evidence](https://github.com/naraya07pedro-spec/naraya07pedro-spec/blob/main/CLIENT-WORK.md).

### Short answer 30 to 45 seconds

For MAXY, the evidence I have is scope planning, not an accepted delivery. The discussion became a Singapore outbound MVP using existing HubSpot, email and assisted LinkedIn. It also surfaced that n8n needed setup and Apollo was not already available. The response was to define the initial deliverables, access, approval and suppression boundaries before building. I would use this as a requirements example, and I would not say the system was completed or that it produced appointments.

### Deep answer 90 to 120 seconds

This is a requirements and commercial-scope example, so I would label it that way from the start. My uploaded context note reports a discovery discussion with MAXY and a Singapore outbound direction. The brief becomes more specific about target segments, the existing HubSpot pipeline, the email channel and LinkedIn with human assistance. It also says n8n needs a new setup and Apollo is not available.

Those details change the implementation dependencies. I cannot assume that a prospect-source subscription exists, that LinkedIn actions should be autonomous, or that booking configuration is ready. The initial scope needs exact sourcing, deduplication, suppression, draft review, controlled sending, CRM updates and handoff criteria. The social-content engine discussed separately should not silently become part of the outbound MVP.

The tradeoff is a smaller initial scope with clear acceptance criteria instead of promising the entire broader system at once. Access and commercial terms need to be settled before build.

The evidence boundary is also clear: the note is my scope statement, and the older tracker row is stale. Connected searches did not recover a client-origin acceptance, implementation test chain or completed handoff. I would not present a planning diagram as deployed integration. What I can explain is how I translate new dependencies into a bounded implementation plan and prevent the agreed scope from drifting.

### Follow up questions

**Why?** New tools and channel requirements change implementation dependencies.

**What was the root cause?** Scope expanded while infrastructure/access assumptions were still unresolved.

**What tradeoff did you make?** Define a lean initial scope and separate later expansion.

**What would you change now?** Keep written deliverables, access dependencies and acceptance criteria together.

**How did you verify the fix?** Use the current scope note; completed build/test/signoff are unverified.

**How did you prevent recurrence?** Avoid adding unapproved tools or treating planning as delivered implementation.

## Supporting Supabase example

If asked about a frontend integration defect, use [BIMMCA refresh hardening](https://github.com/naraya07pedro-spec/bimmca-intelligence/blob/main/docs/DEBUGGING-CASE.md): failed refetch preserves the prior data but marks it stale; overlapping change events are coalesced. The merged source and nine offline tests establish behavior, not a historical live outage or metric accuracy.

## Evidence boundaries to remember

No confirmed expired-token recovery, historical duplicate-send outcome, achieved hourly volume, client UAT/signoff, exactly-once delivery, distributed n8n lock or autonomous approval enforcement is established. The real n8n Error-to-Success pack is a reproduced recovery. MAXY is reported scoping; PT Geget Gigit and EZUmrah are self-reported private engagement scopes. State these naturally when relevant, then focus on the code and verified result.

