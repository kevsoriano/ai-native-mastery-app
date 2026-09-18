*Offline first Android learning platform with shared Firebase and Cloud Run services*

| **Document**    | **Application implementation and delivery plan**           |
|-----------------|------------------------------------------------------------|
| Version         | 0.1                                                        |
| Date            | 18 September 2026                                          |
| Source          | AI Native Mastery Platform PRD version 0.11                |
| Initial pathway | Data Problem-Solving and Automation                        |
| Target          | Working prototype in 6-8 weeks followed by pilot hardening |

# 1 Executive Direction

Build the Android offline vertical slice first, then add synchronization, connected GenAI, and the minimum web operations portal required to publish content and review evidence. This sequence tests the hardest product promise early: a learner must be able to complete the full Diagnose, Learn, Practice, Verify, and Revisit loop after disconnecting from the internet.

The plan uses test-driven development for application-owned behavior and short capability spikes for uncertain external technology. The existing Firebase AI Offline and On Device Capability Verification Plan remains the specialist work package for Gemini Nano and Firebase AI hybrid inference. Findings from that plan feed the GenAI gateway without making on-device generation a dependency of the core loop.

# 2 Delivery Outcomes

| **Outcome**               | **Prototype evidence**                                                                                                                 |
|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
| Offline learner loop      | A learner downloads one module, disconnects, completes all five stages, closes and restarts the app, and retains progress.             |
| Practical skill pathway   | A bounded Data Problem-Solving and Automation module includes spreadsheet-like, SQL, and limited scripting activities.                 |
| Credible evidence         | The system distinguishes assisted learning from independent proof and records rubric, provenance, uncertainty, and follow-up evidence. |
| Resilient synchronization | Locally committed events synchronize idempotently after interruption without duplication or loss.                                      |
| Meaningful GenAI          | Gemini generates a grounded targeted explanation and a learner-specific follow-up question while deterministic rules retain authority. |
| Operational support       | A small web portal publishes content packs, exposes review queues, and displays pilot health.                                          |
| Google Cloud deployment   | The prototype is deployed using Firebase and Cloud Run with App Check, monitoring, and demonstrable offline behavior.                  |

# 3 Scope and Delivery Principles

- Vertical slices before platform breadth. Deliver one skill end to end before generalizing the whole pathway.

- Local first by construction. Network access is an enhancement and synchronization channel, not the execution engine for downloaded learning.

- Evidence before labels. Store how a learner demonstrated a skill before displaying a mastery state.

- Deterministic authority. Generative AI may explain, probe, and interpret, but versioned rules and rubrics govern progression.

- Explicit degradation. Every connected or on-device AI feature declares an authored fallback.

- Append-only history. Corrections and reviews add events rather than rewriting the original record.

- Representative hardware early. Test low-cost and intermittent-connectivity conditions throughout implementation, not only before launch.

# 4 Target Architecture

| **Layer**              | **Components**                                                                                                                                  | **Primary rule**                                                                 |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| Android learner client | UI, local database, content-pack manager, mastery engine, sandbox, evidence recorder, outbox, sync manager, capability detector, GenAI gateway. | Own unsynchronized learner state and complete the downloaded loop offline.       |
| Web operations client  | Content and rubric management, pack publication, evidence review, pilot monitoring.                                                             | Remain small and connected-only for the MVP; never mediate learner sessions.     |
| Firebase               | Authentication, App Check, Firestore, Cloud Storage, Hosting, Remote Config, Crashlytics, and eligible AI client access.                        | Provide shared client-facing services with least-privilege rules.                |
| Cloud Run              | Synchronization API, content-pack builder, signing, secure assessment allocation, cloud AI orchestration, review and analytics services.        | Own secrets, sensitive logic, cross-user operations, and server-only validation. |
| Google AI              | Cloud Gemini and optional supported-device Gemini Nano through the GenAI gateway.                                                               | Return advisory outputs with provenance; never update mastery directly.          |

## 4.1 Core application contracts

| **Contract**   | **Required fields or behavior**                                                                                                                                               |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Content pack   | Pack ID, version, skill graph, resources, activities, rubrics, validators, prompt policies, fallback content, assets, manifest, checksum, signature, and minimum app version. |
| Evidence event | Stable event ID, learner and device pseudonymous IDs, skill, activity, timestamp, result, assistance, rubric version, provenance, policy version, and sync status.            |
| Stage decision | Current stage, next stage, reason code, evidence references, rule version, actor, timestamp, and review status.                                                               |
| Sync envelope  | Device sequence, event batch, pack and schema versions, retry token, acknowledgements, conflicts, and server time.                                                            |
| GenAI result   | Capability, provider, model or base model, inference location, prompt policy, source bundle, output, uncertainty, validation result, and fallback reason.                     |

# 5 Workstreams

| **Workstream**                 | **Primary deliverables**                                                                                                                            | **Dependencies**                                                   |
|--------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------|
| A Product and learning design  | Skill graph, module blueprint, misconceptions, rubrics, content sources, activities, transfer task, and review policy.                              | Pilot learning goals and external validation design.               |
| B Android platform             | Navigation, local database, content packs, offline state, accessibility, notifications, lifecycle recovery, and capability detection.               | Contracts from A and shared schemas.                               |
| C Mastery and evidence         | Stage policy, evidence weighting, assistance handling, readiness rules, retention schedule, skill profile, and audit history.                       | Rubrics and evidence schema.                                       |
| D Offline sandbox              | Table viewer, spreadsheet-like operations, SQL runner, limited scripting, datasets, deterministic tests, project history, and resource limits.      | Activity definitions and security constraints.                     |
| E Cloud and synchronization    | Firebase project, authentication, App Check, storage rules, sync API, conflict handling, pack distribution, monitoring, and backups.                | Local event and content contracts.                                 |
| F Web operations portal        | Content publication, rubric management, evidence queue, review action, and pilot health views.                                                      | Cloud APIs and reviewer roles.                                     |
| G GenAI and evaluation         | GenAI gateway, authored fallback, cloud Gemini flow, on-device capability experiment, prompt registry, response validation, and quality evaluation. | Approved sources, policies, and Firebase AI verification findings. |
| H Quality and pilot operations | Automated tests, device lab, security and privacy review, accessibility checks, support procedures, telemetry, and pilot runbook.                   | All vertical slices and deployment environments.                   |

# 6 Phased Delivery Plan

The schedule assumes a focused team with overlapping roles. A smaller team should preserve the phase order and reduce scope rather than run every workstream concurrently.

| **Phase**                            | **Timing**           | **Build focus**                                                                                                                        | **Demonstrable exit**                                                                                        |
|--------------------------------------|----------------------|----------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| 0 Contracts and foundations          | Week 1               | Repository, CI, environments, schemas, event model, local database, fake providers, sample content pack, and threat model.             | App installs; sample pack opens; offline acceptance test initially fails for a known reason.                 |
| 1 Offline learner vertical slice     | Weeks 2-3            | One skill through Diagnose, Learn, Practice, Verify, and Revisit; local persistence; deterministic feedback; first sandbox activity.   | Full loop passes in airplane mode and survives restart on representative hardware.                           |
| 2 Synchronization and cloud backbone | Weeks 4-5            | Firebase identity and files, App Check, Cloud Run sync API, idempotent outbox, pack update, telemetry, and deployment.                 | Interrupted upload resumes without duplicate or lost events; new pack version downloads safely.              |
| 3 GenAI and evidence review          | Weeks 5-6            | Grounded targeted explanation, dynamic follow-up, GenAI provenance, authored fallback, provisional evidence, and reviewer queue.       | Same learner flow works with cloud Gemini, supported on-device inference when available, and no-AI fallback. |
| 4 Web operations and demonstration   | Weeks 6-7            | Content-pack publication, rubric management, review action, pilot health view, and end-to-end demo instrumentation.                    | Author publishes a pack; reviewer resolves evidence; learner receives result after reconnection.             |
| 5 Hardening and prototype gate       | Week 8               | Low-cost device pass, network-denial testing, accessibility, security, data migration, monitoring, cost controls, and recovery drills. | Prototype meets the Definition of Done and can be demonstrated without manual data repair.                   |
| 6 Pilot hardening                    | Following 8-12 weeks | Broader pathway content, device coverage, facilitator workflows, calibration, support, consent, and field measurement.                 | 100-300 learner pilot is operationally ready with external transfer evaluation.                              |

# 7 Test Driven Development Strategy

Use TDD as the default for code and policies controlled by the team. Use capability spikes only where a real device, service, or experimental SDK must answer a feasibility question. A spike is complete only when its confirmed behavior becomes a fixture, contract test, or documented release constraint.

## 7.1 Test layers

| **Layer**               | **What it proves**                                                                   | **Examples**                                                                                                        |
|-------------------------|--------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| Unit and property tests | Pure rules remain correct across edge cases and event sequences.                     | Mastery transitions, evidence weighting, decay, reason codes, content validation, conflict resolution, and parsers. |
| Component tests         | Local components work with fake clocks, storage, network, and model providers.       | Room migrations, outbox retry, pack verification, sandbox limits, notifications, and GenAI routing.                 |
| Contract tests          | Android, web, Firebase, and Cloud Run agree on schemas and error behavior.           | Sync envelopes, acknowledgements, pack manifests, review actions, authentication, and API version compatibility.    |
| Integration tests       | Real local storage and emulated cloud services cooperate correctly.                  | Offline writes, reconnect, partial batch failure, token expiry, pack update, reviewer decision, and telemetry.      |
| Device acceptance tests | The product promise holds on representative hardware and connectivity.               | Airplane-mode loop, process death, low storage, interrupted download, battery pressure, and accessibility.          |
| AI evaluation           | Variable model outputs meet quality and safety thresholds rather than exact strings. | Groundedness, misconception targeting, answer leakage, reading level, consistency, latency, and fallback behavior.  |

## 7.2 Mandatory test first scenarios

| **ID**  | **Scenario**                                                      | **Pass condition**                                                                    |
|---------|-------------------------------------------------------------------|---------------------------------------------------------------------------------------|
| OFF-01  | Disconnect immediately after content download.                    | The learner completes the full loop without a network request.                        |
| DUR-01  | Terminate the app after an answer but before synchronization.     | The attempt and evidence reappear exactly once after restart.                         |
| SYNC-01 | Interrupt and retry the same event batch.                         | Server acknowledges stable IDs and produces no duplicate progress.                    |
| PACK-01 | Install a newer content pack with changed rubric and policy.      | Historical evidence retains original versions; current activity uses the new version. |
| AI-01   | Cloud and on-device AI are both unavailable.                      | The authored explanation and question appear without blocking progression.            |
| AI-02   | Model returns empty, irrelevant, long, or answer-leaking content. | Validator rejects it, records the reason, and shows the authored fallback.            |
| AUTH-01 | Expired identity while offline and reconnecting.                  | Local work remains available; upload waits for safe reauthentication.                 |
| REV-01  | Reviewer changes a provisional score.                             | A new review event is appended; the original evidence remains visible.                |

# 8 Environments and Delivery Pipeline

| **Environment**  | **Purpose**                                                                               | **Data policy**                                                                                |
|------------------|-------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|
| Local and CI     | Fast unit, component, schema, and emulator tests with fake GenAI and deterministic seeds. | Synthetic fixtures only.                                                                       |
| Development      | Shared integration of Firebase, Cloud Run, web, Android builds, and test content packs.   | Synthetic accounts and non-sensitive artifacts.                                                |
| Staging          | Release-candidate device, network, migration, security, accessibility, and demo testing.  | Pilot-like synthetic data; production configuration shape.                                     |
| Pilot production | Controlled learner deployment and external outcome evaluation.                            | Minimum necessary learner data with consent, retention controls, audit, and role-based access. |

Pipeline order: static checks and unit tests; schema and contract tests; Android and web builds; emulator integration tests; deployment to development; smoke tests; signed release candidate; staging device matrix; manual approval; pilot rollout with staged cohorts and rollback capability.

# 9 Proposed Repository Boundaries

| **Area**         | **Suggested boundary**                                                                                            |
|------------------|-------------------------------------------------------------------------------------------------------------------|
| android-app      | Learner UI, Room database, content-pack runtime, mastery client, sandbox, outbox, sync client, and GenAI gateway. |
| web-portal       | Authoring, publication, evidence review, and pilot health interface.                                              |
| cloud-api        | Cloud Run services for synchronization, content packaging, review, analytics, and GenAI orchestration.            |
| shared-contracts | Versioned schemas, generated clients, reason codes, fixtures, and compatibility tests.                            |
| learning-content | Skill graph, authored resources, rubrics, templates, validators, synthetic datasets, and pack manifests.          |
| evaluation       | External transfer design, prompt-quality fixtures, calibration analysis, and pilot reporting.                     |
| infrastructure   | Firebase and Google Cloud configuration, security rules, service accounts, deployment, monitoring, and budgets.   |

# 10 Security Privacy and Trust Work

- Complete a data inventory before instrumenting learner behavior; collect only events required for learning, integrity, reliability, or evaluation.

- Use pseudonymous learner and device identifiers in event payloads and separate identity from detailed learning evidence where practical.

- Protect client access with Firebase Authentication, App Check, least-privilege Firebase rules, and short-lived server authorization.

- Keep secrets, signing keys, secure assessment allocation, cross-user queries, and cloud AI orchestration on trusted server infrastructure.

- Encrypt data in transit and at rest, define deletion and retention behavior, and record reviewer and administrator actions.

- Do not infer deception from identity, emotion, gaze, accent, or biometric characteristics.

- Give learners access to evidence, assistance history, review status, correction, retry, dispute, export, and deletion controls appropriate to the pilot.

# 11 Observability and Operational Readiness

| **Signal**       | **Minimum implementation**                                                                                                                             |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Offline health   | Completed sessions without network, local write failures, restart recovery, storage pressure, and unsynchronized-event age.                            |
| Synchronization  | Batch attempts, acknowledgements, retries, conflicts, duplicates prevented, rejected events, and queue depth.                                          |
| Content delivery | Pack download, verification, install, rollback, version adoption, and failed update reason.                                                            |
| GenAI            | Capability requested, inference location, latency, validation result, fallback reason, token or quota data when available, and sampled quality review. |
| Learning         | Stage transitions, assistance use, verification outcomes, retention outcomes, and unresolved evidence gaps.                                            |
| Operations       | Crash-free sessions, API errors, latency, authorization failures, review queue age, cost, and alert status.                                            |

# 12 Roles and Ownership

| **Role**                        | **Accountability**                                                                                             |
|---------------------------------|----------------------------------------------------------------------------------------------------------------|
| Product and learning lead       | Scope, learner journey, pathway, rubrics, pilot design, claims, and go or no-go decisions.                     |
| Android engineer                | Offline client, local data, lifecycle, content runtime, sandbox integration, sync client, and device quality.  |
| Backend and cloud engineer      | Firebase, Cloud Run, APIs, synchronization, security, pack pipeline, monitoring, and operations.               |
| Web engineer                    | Authoring, publication, review, and pilot operations portal.                                                   |
| AI and evaluation lead          | GenAI gateway, prompts, grounded sources, model evaluation, evidence interpretation, and calibration research. |
| Quality and accessibility owner | Test strategy, device matrix, network conditions, accessibility, release evidence, and defect triage.          |

For a lean team, one person may own multiple roles, but each accountability still needs a named owner. Product, learning, evidence, and privacy decisions should not default silently to engineering.

# 13 Dependencies and Decision Points

| **Decision**                                             | **Required by**     | **Default if unresolved**                                                                                            |
|----------------------------------------------------------|---------------------|----------------------------------------------------------------------------------------------------------------------|
| Android implementation technology and minimum API level  | End of Week 1       | Choose the option that best supports Room or SQLite, lifecycle testing, sandbox isolation, and Firebase integration. |
| Initial skill and external transfer task                 | End of Week 1       | Use dataset validation and repair with an unfamiliar transfer dataset.                                               |
| Sandbox runtime and isolation approach                   | End of Week 2       | Start with table operations and SQL; defer general scripting if safe isolation is not proven.                        |
| Firebase direct-access versus Cloud Run operation matrix | End of Week 2       | Use Cloud Run for sensitive, cross-user, signed, or AI-orchestrated operations.                                      |
| On-device Firebase AI viability                          | Before Phase 3 exit | Treat on-device generation as unavailable and retain cloud plus authored behavior.                                   |
| Pilot hardware floor and device matrix                   | Before Phase 5      | Use representative low-memory Android devices and at least one supported GenAI device for enhancement testing.       |

# 14 Risks and Mitigations

| **Risk**                                     | **Early signal**                                                         | **Mitigation**                                                                                      |
|----------------------------------------------|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| Offline claim is superficial                 | Learner cannot finish or recover without reconnecting.                   | Make airplane-mode acceptance the first vertical-slice gate and repeat it in every release.         |
| Synchronization corrupts evidence            | Duplicates, missing events, or overwritten versions.                     | Append-only events, stable IDs, idempotency, acknowledgements, migrations, and replay tests.        |
| Sandbox scope dominates delivery             | Environment work delays the learner loop.                                | Begin with constrained table and SQL tasks; add scripting only after isolation is demonstrated.     |
| GenAI becomes a hidden dependency            | Spinners, errors, or weaker offline paths.                               | Gateway, explicit routing, validation, authored fallback, network-denial tests, and feature flags.  |
| Content is insufficient for evaluation       | Prototype works technically but cannot support credible transfer claims. | Build module blueprint, rubric, misconception map, and external transfer task in Phase 0.           |
| Web portal expands into administration suite | Operational features consume learner-product capacity.                   | Limit MVP to publication, review, and pilot health.                                                 |
| Low-cost device performance fails            | Slow startup, storage pressure, crashes, or battery drain.               | Set a hardware budget, test weekly, reduce assets, constrain models, and keep text-first fallbacks. |

# 15 Prototype Release Gates

- A learner completes the downloaded core loop in airplane mode on representative hardware and survives process death and restart.

- Every accepted activity creates durable evidence before the UI reports completion.

- Repeated and interrupted synchronization produces neither lost nor duplicated progress.

- Historical evidence retains its content, rubric, policy, assistance, scorer, model, and inference-location versions.

- The sandbox completes at least one validated spreadsheet-like or SQL task locally with project history and safe resource limits.

- The Gemini demonstration changes a grounded explanation or follow-up question in a way visible to the learner, while authored fallback produces a complete alternative path.

- A content author publishes a signed pack and a reviewer resolves a provisional evidence item through the web portal.

- Security, privacy, accessibility, monitoring, cost, recovery, and device-matrix checks have named owners and recorded results.

# 16 Immediate Backlog

| **Order** | **Work item**                                                                                                   | **Completion evidence**                                                                                      |
|-----------|-----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| 1         | Approve shared schemas and reason codes.                                                                        | Versioned content, evidence, stage-decision, sync, and GenAI contracts with fixtures.                        |
| 2         | Create repository, CI, development Firebase project, Cloud Run service skeleton, and Android application shell. | Green build, deployment, authentication smoke test, and fake-provider tests.                                 |
| 3         | Author the first skill slice and external transfer fixture.                                                     | Approved lesson, misconception map, practice variants, verification task, rubric, and fallback explanations. |
| 4         | Implement local database, content-pack loader, and append-only evidence store test-first.                       | Migration, corruption, restart, and replay tests pass.                                                       |
| 5         | Implement one complete offline learner loop.                                                                    | Airplane-mode acceptance test passes on target hardware.                                                     |
| 6         | Implement idempotent synchronization and pack update.                                                           | Interruption and duplicate-delivery tests pass against development backend.                                  |
| 7         | Integrate cloud Gemini and run Firebase AI on-device capability spike.                                          | Grounded explanation demo, explicit inference provenance, and authored fallback.                             |
| 8         | Implement minimum web publication and review flow.                                                              | Pack publication and reviewer resolution work end to end.                                                    |

# 17 Companion Documents

| **Document**                                                   | **Purpose**                                                                                                                                    |
|----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| AI Native Mastery Platform PRD version 0.11                    | Defines product problem, scope, requirements, learner experience, architecture, success metrics, risks, and launch gates.                      |
| Firebase AI Offline and On Device Capability Verification Plan | Tests experimental Firebase AI hybrid and Gemini Nano behavior on real devices and determines whether on-device GenAI is viable for the pilot. |
| This implementation plan                                       | Sequences product, architecture, development, testing, deployment, and pilot-readiness work.                                                   |
