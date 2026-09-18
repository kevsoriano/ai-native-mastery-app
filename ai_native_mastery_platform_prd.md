# AI Native Mastery Platform

**Product Requirements Document**

*Continuously teach, test, and build credible evidence of independent skill mastery*

| **Document**     | **Value**                                                          |
|------------------|--------------------------------------------------------------------|
| Status           | Concept PRD for discovery and offline-first MVP planning           |
| Version          | 0.6                                                                |
| Date             | 18 September 2026                                                  |
| Primary audience | Product, design, engineering, learning science, and pilot partners |
| Initial wedge    | Data Problem-Solving and Automation                                |

## Working thesis

> *Build an AI-native learning system that continuously estimates what a person knows and can independently do, then selects the next activity that will most improve learning or reduce uncertainty about mastery.*

## Core promise

Do not merely prove that a learner completed a course. Build evidence that the learner can use the skill independently, explain their reasoning, and retain it over time.

# 1 Executive Summary

Generative AI weakens traditional signals of learning. A completed assignment, polished essay, correct answer, or working code sample may show that a learner used AI effectively, but it no longer proves that the learner personally understands or can reproduce the underlying skill. Existing learning systems also over-index on content delivery and completion rather than calibrated evidence of capability.

The proposed product is an offline-first mastery and evidence engine. It represents a domain as a graph of observable skills, keeps a probabilistic learner model for each skill, and chooses the next teaching or assessment activity based on the learner's goal, current evidence, likely misconceptions, forgetting risk, and uncertainty. The core Diagnose, Learn, Practice, Verify, and Revisit loop must work without an active internet connection. Learning Mode allows broad AI assistance. Proof Mode constrains assistance and collects stronger evidence through oral reasoning, adaptive questions, debugging, and hands-on tasks.

The MVP should not attempt to become a complete course marketplace, video generator, credentialing body, or enterprise HR platform. It should validate the narrowest risky claim: that multi-modal, adaptive evidence predicts independent performance better than course completion and conventional quiz scores.

## Recommended first product

- Target learner: motivated adult learners who need practical data skills for work, small business, education, public service, or entry into technical careers.

- Initial pathway: Data Problem-Solving and Automation, beginning with data literacy and spreadsheets, progressing through SQL, and introducing scripting when automation adds clear value.

- Core experience: downloadable diagnostic assessment, adaptive learning plan, optional local AI mentor, quizzes, oral explanation, hands-on tasks, delayed retention checks, and an evidence-backed skill profile.

- Access model: Android-first learner app with optional school or community hub, local Wi-Fi delivery, and opportunistic cloud synchronization.

- Pilot design: one domain, 100–300 learners, and an external transfer task scored blind to the product's mastery estimate.

## Product decisions embedded in this PRD

| **Decision**   | **Recommendation**                                         | **Reason**                                                                           |
|----------------|------------------------------------------------------------|--------------------------------------------------------------------------------------|
| Primary object | Skill and evidence, not course completion                  | Keeps the product aligned to actual capability.                                      |
| Mastery output | Calibrated confidence with evidence history                | Avoids false precision and makes claims auditable.                                   |
| Modes          | Separate Learning Mode and Proof Mode                      | Assistance is valuable for learning but weak evidence during verification.           |
| Adaptation     | Choose activities for learning value and information value | The next activity should teach or resolve an important uncertainty.                  |
| Initial market | Learner-funded direct pilot; institutional buyers later    | Tests learner value and demand before adding institutional procurement requirements. |
| Connectivity   | Personal-device offline use first; local hub later         | Validates the lowest-dependency access model before introducing hub operations.      |
| Human role     | Reviewer for disputed or high-stakes evidence              | AI scoring alone should not determine consequential decisions.                       |

# 2 Improvements to the Original Concept

The original concept contains the right ingredients, but several changes make it more differentiated and buildable.

| **Original direction**   | **Improved formulation**                                                                                                            |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Many learning channels   | Each modality has a measurement purpose: explanation tests reasoning, projects test application, and delayed checks test retention. |
| AI is a patient teacher  | AI continuously teaches, observes, challenges, estimates uncertainty, and revisits weak skills.                                     |
| Adaptive quizzes         | An adaptive activity policy selects any next action—not only quiz questions—based on expected learning and information gain.        |
| Mastery percentage       | A confidence estimate with evidence strength, recency, independence, and coverage; never an unexplained score.                      |
| Proof through assessment | Proof is a portfolio of converging evidence collected across time and contexts, not one exam.                                       |
| Future HR use            | A separate, higher-risk product surface requiring consent, human review, fairness validation, and role-specific governance.         |

The most important addition is an explicit outcome validation strategy. The product should earn the right to claim mastery by demonstrating that its estimates predict performance on unseen, independently scored tasks and remain calibrated across learner groups.

# 3 Problem Definition

## 3.1 User problem

Learners cannot reliably tell which skills they genuinely understand, which they can apply without assistance, and which they are beginning to forget. They receive content recommendations, grades, and completion certificates, but those signals often fail to reveal specific misconceptions or readiness for real work.

## 3.2 Institutional problem

Educators and employers need credible, current evidence of capability. AI-assisted work makes provenance and independence harder to interpret. Conventional proctoring can increase surveillance without proving transfer, while static exams provide only a narrow snapshot.

## 3.3 Root causes

- Completion and time-on-task are treated as learning outcomes.

- Most assessments sample too few contexts and reward recognition or memorization.

- Learning systems rarely model decay, prerequisite gaps, or uncertainty explicitly.

- AI assistance is either banned indiscriminately or allowed without distinguishing assisted production from independent capability.

- Evidence is fragmented across quizzes, conversations, projects, and external work.

## 3.4 Opportunity

Create a learner-owned, continuously updated record that answers four practical questions: What can I do now? How strong is the evidence? What should I do next? When should this be checked again?

# 4 Product Vision and Principles

## 4.1 Vision

Every learner has an adaptive tutor and an auditable skill profile that improves through authentic practice and credible demonstration—not through passive completion. Core learning and proof remain available without continuous internet access.

## 4.2 Product principles

| **Principle**                    | **Implication**                                                                                               |
|----------------------------------|---------------------------------------------------------------------------------------------------------------|
| Evidence before labels           | Show why a skill is considered demonstrated or uncertain.                                                     |
| Learning and proof are different | Permit rich assistance in learning; constrain and record assistance in proof.                                 |
| Uncertainty is useful            | The system may say it lacks enough evidence and should seek the most informative next activity.               |
| Transfer matters                 | Prefer novel application over repeated variants of memorized questions.                                       |
| Learner agency                   | Let learners inspect, challenge, and supplement their evidence.                                               |
| Low-surveillance integrity       | Use task design, interaction evidence, and follow-up questioning before invasive monitoring.                  |
| Calibrated claims                | Report confidence bands and evidence quality; avoid false precision.                                          |
| Human accountability             | No consequential education or employment decision should rely only on an AI score.                            |
| Offline by default               | Save locally first; use connectivity for updates, backup, stronger AI, and review rather than core operation. |

# 5 Users and Jobs to Be Done

| **User**             | **Primary job**                                                              | **Initial priority** |
|----------------------|------------------------------------------------------------------------------|----------------------|
| Learner              | Help me know what I can actually do and choose the highest-value next step.  | Primary              |
| Instructor or mentor | Show me where a learner is stuck and what evidence supports that conclusion. | Pilot support        |
| Program owner        | Determine whether the learning experience produces transferable capability.  | Pilot buyer          |
| Employer or HR       | Understand skill gaps and readiness for a role with appropriate governance.  | Later                |
| Content author       | Map resources and tasks to skills and evidence types.                        | Internal first       |

## Primary persona

A motivated adult learner who wants to use data to solve practical problems, improve work, or enter a technical career. They may have limited connectivity, uneven formal preparation, and little or no prior programming experience.

## Primary job story

When I am learning to solve practical problems with data and automation, I want the system to distinguish what I can do with help from what I can do independently, so I can focus my effort, demonstrate credible progress, and apply the skill responsibly in real work.

## 5.1 Initial Pathway

The MVP will launch with Data Problem-Solving and Automation. The pathway teaches learners to frame a practical question, inspect and validate data, calculate or query an answer, communicate the result, and automate repeatable work. It is deliberately broader than a single tool and narrower than a data-science occupation.

### Pathway progression

1\. Data foundations: tables, data types, missing values, validation, privacy, and evidence-based conclusions.

2\. Spreadsheet problem-solving: formulas, filters, summaries, charts, error checking, and reusable templates.

3\. SQL investigation: selecting, filtering, joining, grouping, and validating results against source records.

4\. Workflow automation: repeatable transformations, rule-based checks, and small scripts using an approved offline runtime.

5\. Applied projects: locally relevant scenarios such as inventory, crop or clinic records, school attendance, household budgeting, and service operations, using synthetic or properly governed data.

6\. Specialization bridges: learners may continue into software development, security operations, applied analytics, or AI-assisted work after demonstrating the relevant prerequisites.

### MVP boundary

The pilot covers spreadsheet-like tables, CSV files, SQL, and limited Python or JavaScript automation. It does not claim to train a data scientist, software engineer, or cybersecurity professional. Cloud deployment, unrestricted packages, production databases, offensive security tooling, and large-scale machine learning remain outside the initial pathway.

### Mastery evidence

Proof combines correct outputs with inspection of formulas or queries, validation checks, explanation of assumptions, recovery from planted errors, transfer to an unfamiliar dataset, and delayed reassessment. A polished chart or AI-generated script alone is not sufficient evidence of mastery.

### Offline sandbox

The learner device provides a constrained workspace with a table viewer, spreadsheet-like editor, SQL runner backed by a local database, and an optional prepackaged scripting runtime. Starter datasets, tests, hints, and project history are stored in the content pack. Execution has time and memory limits, external network access is disabled by default, and work synchronizes only when a connection or local hub becomes available.

# 6 The Mastery Model

## 6.1 Skill graph

The core content structure is a directed graph of observable skills and prerequisites. A course is a curated path through that graph, not the canonical source of truth. Skills must be narrow enough to assess through behavior, such as “clean inconsistent records and justify each transformation,” rather than broad labels such as “knows data analysis.”

| **Skill field**       | **Definition**                                                                     |
|-----------------------|------------------------------------------------------------------------------------|
| Skill statement       | An observable capability written as an action in a defined context.                |
| Prerequisites         | Skills whose absence materially reduces the chance of success.                     |
| Evidence requirements | Minimum mix of recall, explanation, application, transfer, and retention evidence. |
| Difficulty range      | Expected complexity and scaffolding levels.                                        |
| Misconceptions        | Known wrong models the system should diagnose.                                     |
| Assessment bank       | Validated prompts, tasks, rubrics, and variants.                                   |
| Resources             | Explanations, examples, videos, documentation, and practice mapped to the skill.   |

## 6.2 Mastery state

The learner-facing state should remain understandable while the internal model may be probabilistic.

| **State**    | **Meaning**                                                           | **Typical next action**     |
|--------------|-----------------------------------------------------------------------|-----------------------------|
| Unknown      | Not enough evidence to estimate current capability.                   | Short diagnostic            |
| Exposed      | The learner has encountered the idea but has not demonstrated it.     | Guided example              |
| Developing   | Some correct evidence exists, with important gaps or inconsistency.   | Targeted practice           |
| Demonstrated | The learner succeeds independently in representative contexts.        | Novel transfer task         |
| Mastered     | Multiple strong, recent, independent evidence items support transfer. | Advance and schedule review |
| At risk      | Earlier mastery evidence has aged or recent performance has declined. | Spaced retrieval check      |

## 6.3 Evidence model

Every evidence item records more than correctness. Its contribution depends on quality and context.

| **Dimension**    | **Examples**                                               |
|------------------|------------------------------------------------------------|
| Outcome          | Correctness, rubric score, partial credit, error class     |
| Independence     | Unassisted, hints used, AI used, collaborator present      |
| Cognitive demand | Recall, explain, apply, debug, design, transfer            |
| Novelty          | Seen pattern, variant, unfamiliar context                  |
| Recency          | When the evidence was collected                            |
| Consistency      | Agreement with other evidence across modalities            |
| Authenticity     | Interaction trace, follow-up explanation, artifact history |
| Rater confidence | Rubric reliability and model or human scoring confidence   |

A learner-facing mastery view should expose the evidence mix, most recent independent demonstration, known weaknesses, and next verification date. A numeric confidence may be shown only if calibrated and accompanied by plain-language meaning.

## 6.4 Next best activity policy

The selection engine balances five signals: expected learning gain, expected information gain, goal relevance, prerequisite leverage, and learner cost. It should also enforce variety and avoid repeatedly testing the same surface pattern.

Conceptual priority score: activity value = learning gain + information gain + goal relevance + prerequisite leverage − time and frustration cost. Initial MVP weights should be rules-based and observable; optimization can follow after sufficient outcome data exists.

# 7 Core Experience

## 7.1 Continuous loop

1. Diagnose: collect a compact baseline across prerequisites and target skills.
2. Learn: offer an explanation or resource suited to the learner's misconception and preference.
3. Practice: provide scaffolded activities with hints and feedback.
4. Verify: remove scaffolding, introduce a novel challenge, and collect independent evidence against an explicit rubric.
5. Revisit: schedule retrieval based on evidence strength, age, and observed decay.

The loop is not a fixed course sequence. It operates per skill. A learner may move directly from Diagnose to Verify when prior evidence is strong, return from Practice or Verify to Learn when a misconception appears, or revisit a previously mastered skill while continuing to develop other skills.

```mermaid
flowchart TD
    D[Diagnose] --> L[Learn]
    L --> P[Practice]
    P --> R{Ready to verify?}
    R -->|No| L
    R -->|Yes| V[Verify]
    V -->|Demonstrated| RV[Revisit]
    V -->|Gap found| L
    RV -->|Retained| A[Advance]
    RV -->|At risk| L
```

*Figure 1 Mastery loop transitions*

## 7.2 Learning Mode

Learning Mode is permissive and collaborative. Learners may ask questions, request alternate explanations, use examples, reveal hints, consult documentation, and work with the AI mentor. Activity events still record assistance so the system can distinguish learning progress from proof evidence.

## 7.3 Proof Mode

Proof Mode collects stronger evidence under declared constraints. It uses bounded sessions, novel tasks, randomized parameters, oral follow-ups, and artifact or interaction history. The interface tells the learner what assistance is allowed. A session may be paused or invalidated when the evidence cannot support the intended claim, but the learner should receive a clear reason and an appeal or retry path.

| **Proof method**   | **What it tests**                        | **Integrity mechanism**                            |
|--------------------|------------------------------------------|----------------------------------------------------|
| Adaptive questions | Recall and conceptual discrimination     | Item variation and follow-up on reasoning          |
| Oral explanation   | Mental model and independent reasoning   | Dynamic probes tied to prior answers               |
| Debugging task     | Diagnosis and application                | Novel defect and action trace                      |
| Hands-on build     | Integrated performance                   | Milestones, version history, and defense questions |
| Transfer scenario  | Generalization beyond practiced examples | Unfamiliar context with rubric-based scoring       |
| Delayed review     | Retention                                | Unannounced variant after an appropriate interval  |

## 7.4 Learner profile

- Goal and target role or outcome.

- Skill map with state, confidence language, and prerequisite relationships.

- Evidence timeline with modality, assistance level, rubric, date, and result.

- Misconceptions and skills requiring review.

- Recommended next activity with an explanation of why it matters.

- Learner controls to correct context, add evidence, request reassessment, or hide sharing.

## 7.5 Loop operation model

Every stage is a contract with an entry reason, a learner activity, evidence rules, and an exit decision. The next-best-activity policy selects a stage and activity for one or more skills; it does not simply advance the learner after completion.

| **Stage** | **Purpose**                                                | **Learner experience**                                                                     | **Evidence**                                                                      | **Exit decision**                                                         |
|-----------|------------------------------------------------------------|--------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------|
| Diagnose  | Estimate current capability and uncertainty                | Complete a short adaptive set of questions, explanations, or tasks                         | Correctness, reasoning, confidence, error pattern, difficulty, and assistance     | Identify a gap, establish readiness for Verify, or remain Unknown         |
| Learn     | Introduce a capability or correct a specific misconception | Use a targeted explanation, example, dialogue, or demonstration                            | Self-explanation and formative checks; not strong proof evidence                  | Pass a comprehension check or receive a different explanation             |
| Practice  | Build capability with progressively reduced support        | Complete varied exercises with feedback and optional hints                                 | Accuracy, consistency, error recovery, difficulty, and assistance used            | Meet a readiness rule, continue practice, or return to Learn              |
| Verify    | Test independent application and transfer                  | Complete a novel challenge under declared assistance constraints and explain the reasoning | Rubric score, independence, novelty, reasoning, provenance, and scorer confidence | Demonstrate the skill, collect more evidence, or return to a targeted gap |
| Revisit   | Test retention after time has passed                       | Complete a delayed retrieval or transfer task with meaningful variation                    | Retention interval, independence, transfer, and contradictory evidence            | Keep current, mark At risk, or reopen Learn or Practice                   |

## 7.6 Evidence processing after each activity

> 1\. Record the result with skill, difficulty, novelty, permitted and actual assistance, time, modality, rubric, content version, and provenance.
>
> 2\. Validate the evidence. Reject, quarantine, or request review when the activity is incomplete, corrupted, outside its permitted conditions, or scored with low confidence.
>
> 3\. Update the mastery estimate. Independent novel evidence carries more weight than assisted practice; recent contradictory evidence can lower confidence.
>
> 4\. Locate the remaining uncertainty. Distinguish whether the unresolved question concerns recall, explanation, application, transfer, retention, or evidence authenticity.
>
> 5\. Select the next activity by expected learning gain, information gain, goal relevance, prerequisite leverage, learner cost, offline availability, and required modality.

The learner should see a concise reason for the selection. Example: You can summarize a clean table, but there is not enough evidence that you can detect and repair inconsistent records independently. Your next activity is an unassisted data-cleaning task.

## 7.7 Initial transition rules

The MVP uses transparent, versioned rules. A language model may help interpret an answer, but it does not control progression without the policy layer.

| **Current condition**                                                           | **Next stage**    | **Reason**                                                        |
|---------------------------------------------------------------------------------|-------------------|-------------------------------------------------------------------|
| Diagnostic reveals a misconception or missing prerequisite                      | Learn             | Target the specific explanatory gap before more testing           |
| Diagnostic provides strong recent independent evidence                          | Verify            | Confirm transfer without unnecessary instruction                  |
| Comprehension check succeeds                                                    | Practice          | Move from conceptual understanding to supported performance       |
| Practice remains inconsistent or hint-dependent                                 | Practice or Learn | Increase variation or repair the recurring misconception          |
| Practice succeeds across sufficiently difficult variants with little assistance | Verify            | Test whether performance transfers without scaffolding            |
| Verify meets the rubric with valid independent evidence                         | Revisit           | Schedule retention while unlocking eligible dependent skills      |
| Verify fails in a diagnosable way                                               | Learn or Practice | Remediate the demonstrated gap instead of repeating the same test |
| Delayed evidence is weak, old, or contradictory                                 | Revisit or Learn  | Refresh the skill and reduce overconfidence                       |

Thresholds are configuration, not universal truths. The team must calibrate readiness and mastery thresholds against blind-scored external transfer tasks and revise them by domain when evidence supports the change.

## 7.8 End to end example

Target skill: detect and repair inconsistent values in a small operational dataset.

| **Stage** | **What happens**                                                                                                                | **System decision**                                                                                                             |
|-----------|---------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| Diagnose  | The learner reviews an inventory table, notices duplicate item names, but treats inconsistent units as equivalent.              | Infer a misconception about data types and unit normalization, then select a targeted explanation.                              |
| Learn     | The learner studies a worked comparison of kilograms and grams, then explains why values must be normalized before aggregation. | A short comprehension check indicates that the misconception may be corrected.                                                  |
| Practice  | The learner cleans three datasets with decreasing hints, validates totals, and recovers from a planted formatting error.        | The readiness rule is met because varied datasets are corrected consistently with little assistance.                            |
| Verify    | The learner independently cleans an unfamiliar stock-count dataset, writes a summary query, and explains each transformation.   | The rubric supports Demonstrated because correctness, validation, independence, explanation, and transfer requirements are met. |
| Revisit   | Fourteen days later, the learner receives a clinic-supplies dataset with different unit and duplicate-record problems.          | Success keeps the skill current; partial success marks it At risk; failure reopens the relevant gap.                            |

## 7.9 Offline execution contract

- Diagnose uses downloaded items, rubrics, and deterministic adaptation rules.

- Learn always has an authored text-first resource; local AI is optional and may provide explanations or dialogue on capable hardware.

- Practice selection and mastery updates run locally and never depend on a network response.

- Verify uses locally available secure tasks, records permitted assistance, and appends evidence before showing completion.

- Revisit uses the local schedule and device notifications. The learner can complete it while still offline.

- Complex AI scoring may remain provisional until local-hub or cloud review, but progress and evidence are never discarded. Synchronization preserves the original event and policy versions.

# 8 Primary User Flows

## 8.1 New learner

> 1\. Select a concrete goal and initial module.
>
> 2\. Review what data will be collected and how evidence may be used.
>
> 3\. Complete a 15–25 minute adaptive diagnostic.
>
> 4\. Receive a skill map that distinguishes observed evidence from unknown areas.
>
> 5\. Start the recommended learning activity and see why it was chosen.
>
> 6\. Complete an independent challenge after enough guided practice.
>
> 7\. Review the evidence-backed result and scheduled follow-up.

## 8.2 Daily return

The learner sees one recommended action, its expected duration, whether it is for learning or proof, and the reason it is prioritized. They may choose an alternative while the system records preference and adapts within goal constraints.

## 8.3 Instructor review

An instructor inspects cohort-level gaps and individual evidence, filters low-confidence or disputed assessments, and can annotate or override a result with a reason. Overrides remain visible in the audit history.

# 9 Offline First and Rural Deployment

## 9.1 Product requirement

A learner must be able to complete the core Diagnose, Learn, Practice, Verify, and Revisit loop without an active internet connection. Important actions are committed locally before any network request. Connectivity enhances the experience but must not be required to open downloaded material, save progress, complete eligible assessments, update the local mastery state, or schedule review.

## 9.2 Deployment model

| **Layer**               | **Offline responsibility**                                                                           | **Connected responsibility**                                                                            |
|-------------------------|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| Learner device          | Content, activities, local profile, evidence log, mastery updates, sync queue, and optional small AI | Download updates, back up events, and receive reviewed results                                          |
| School or community hub | Local Wi-Fi access, shared content, teacher dashboard, device sync, backups, and optional shared AI  | Exchange compact updates with central services when a connection is available                           |
| Cloud services          | Not required for an active offline session                                                           | Content publishing, cross-site synchronization, stronger AI, human review, analytics, and model updates |
| Physical media          | Distribute signed content, model, and software bundles by USB, SD card, or portable drive            | Prepared from an authorized connected environment                                                       |

## 9.3 Hardware tiers

| **Tier**                | **Expected experience**                                                                  | **Product behavior**                                                        |
|-------------------------|------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| Low-cost phone          | Text, compressed images, quizzes, deterministic adaptation, progress, and selected audio | AI is optional; fall back to authored explanations and rule-based scoring   |
| Capable phone or tablet | Core experience plus a small local language model for hints and constrained dialogue     | Display model download size and permit removal without losing learning data |
| Local learning hub      | Shared content library, classroom dashboard, local sync, and more capable AI services    | Continue serving devices over local Wi-Fi when the internet is unavailable  |
| Connected environment   | Full synchronization, difficult scoring, human review, and large updates                 | Never block offline work while cloud processing is pending                  |

## 9.4 Synchronization and distribution

- Use an append-only evidence log with stable event identifiers so retries do not duplicate progress.

- Prioritize small evidence and profile updates before content, video, or model downloads.

- Resume interrupted transfers and show pending, synchronized, failed, and conflict states in plain language.

- Version skills, activities, rubrics, policies, content packs, and AI models; preserve the version used for historical evidence.

- Support internet, local-network peer, school-hub, USB, SD-card, and portable-drive update paths.

- Resolve ordinary progress merges automatically; route contradictory profile or scoring changes for review.

## 9.5 Offline Proof Mode limitations

Offline Proof Mode can produce credible evidence through novel tasks, randomized parameters, interaction history, oral defense, delayed reassessment, and a device-signed event log. It cannot guarantee identity or the absence of outside help. Learner-facing claims must describe the recorded conditions. High-impact evidence may remain provisional until it is synchronized, validated, or reviewed.

## 9.6 Rural accessibility requirements

- Android-first support with testing on representative older and low-memory devices.

- Text-only and low-data content packs, transcripts, compressed media, and visible download sizes.

- No progress loss during power interruption, application termination, or unstable connectivity.

- Battery-aware synchronization and configurable Wi-Fi-only downloads.

- Local-language content packs and equivalent non-voice paths where speech models are unavailable or unreliable.

- Administrators can provision multiple devices locally without requiring individual high-bandwidth downloads.

# 10 MVP Scope

## 10.1 In scope

| **Capability**       | **MVP requirement**                                                                                                                                                            |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Skill graph          | Data Problem-Solving and Automation with 30–60 observable skills spanning data foundations, spreadsheets, SQL, and limited scripting.                                          |
| Diagnostic           | Adaptive baseline using a bounded item and task bank.                                                                                                                          |
| AI mentor            | Dialogue grounded in approved resources, skills, and misconceptions.                                                                                                           |
| Adaptive practice    | Rules-based activity selection with transparent reasons.                                                                                                                       |
| Proof Mode           | Adaptive quiz, oral explanation, and one hands-on task type.                                                                                                                   |
| Mastery estimate     | Evidence-weighted state with uncertainty and decay.                                                                                                                            |
| Evidence record      | Timestamped events with rubric, assistance, provenance, and scorer confidence.                                                                                                 |
| Dashboard            | Learner skill map; basic instructor review queue and cohort summary.                                                                                                           |
| Retention            | At least one delayed reassessment schedule.                                                                                                                                    |
| Evaluation           | External transfer task and calibration analysis.                                                                                                                               |
| Offline operation    | Android-first local data, downloadable content pack, sync queue, and resilient restart.                                                                                        |
| Future hub readiness | Content, evidence, and synchronization formats remain compatible with a later local hub, but hub hardware and operations are not required for the first deployment.            |
| Offline sandbox      | Constrained table, SQL, and scripting workspace with starter datasets, deterministic tests, local project history, resource limits, and no external network access by default. |

## 10.2 Explicitly out of scope

- AI-generated video production as a core capability.

- A broad marketplace of courses or mentors.

- Accredited certification or claims equivalent to a degree or professional license.

- Automated hiring, firing, compensation, or promotion decisions.

- Remote proctoring based on face, gaze, emotion, or biometric inference.

- Open-ended assessment of every professional domain.

- Fully autonomous generation and release of high-stakes assessment items.

- Public skill profiles by default.

- Requiring an on-device generative model for the core learning loop.

- High-quality AI video generation on learner devices.

## 10.3 MVP assumptions

- The first domain can be decomposed into observable skills with usable rubrics.

- A short interaction history plus dynamic follow-ups can provide useful integrity signals without invasive surveillance.

- Learners accept separate assisted and independent modes when the benefit is clearly explained.

- Pilot partners can provide or approve source material, tasks, and an external outcome measure.

- The pilot can obtain representative low-cost Android devices and at least one local-hub configuration for field testing.

# 11 Functional Requirements

| **ID** | **Requirement**                                                                                                                                                           | **Priority** |
|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------|
| FR1    | Create and version skills, prerequisites, misconceptions, rubrics, resources, and evidence requirements.                                                                  | Must         |
| FR2    | Run a diagnostic that adapts difficulty and skill coverage while respecting a time budget.                                                                                | Must         |
| FR3    | Recommend one next activity and display a learner-readable reason.                                                                                                        | Must         |
| FR4    | Support Learning Mode with grounded explanations, hints, examples, and feedback.                                                                                          | Must         |
| FR5    | Support Proof Mode with declared assistance constraints and evidence capture.                                                                                             | Must         |
| FR6    | Score structured and open responses against versioned rubrics, with confidence and review thresholds.                                                                     | Must         |
| FR7    | Update mastery state only from valid evidence and preserve the full event history.                                                                                        | Must         |
| FR8    | Schedule reassessment based on elapsed time, prior strength, and recent contradictory evidence.                                                                           | Must         |
| FR9    | Allow learners to inspect evidence, request a retry, and dispute a scored result.                                                                                         | Must         |
| FR10   | Provide reviewer queues for low-confidence, disputed, or high-impact evidence.                                                                                            | Should       |
| FR11   | Export a learner-controlled evidence summary with scope and limitations.                                                                                                  | Should       |
| FR12   | Support human-authored and approved content before allowing generated assessment content.                                                                                 | Must         |
| FR13   | Complete the core learning and mastery loop without an active internet connection.                                                                                        | Must         |
| FR14   | Persist local events before network submission and synchronize them idempotently when connectivity returns.                                                               | Must         |
| FR15   | Download, verify, update, and remove versioned content packs without deleting learner evidence.                                                                           | Must         |
| FR16   | Distribute approved updates through cloud, local hub, peer network, or physical media.                                                                                    | Should       |
| FR17   | Provide deterministic non-AI fallbacks for explanations, recommendations, and eligible scoring.                                                                           | Must         |
| FR18   | Show offline availability, storage cost, update status, and pending synchronization clearly.                                                                              | Must         |
| FR19   | Apply versioned stage-transition rules and record the reason for every next-stage and next-activity decision.                                                             | Must         |
| FR20   | Run approved spreadsheet-like, SQL, and scripting activities offline in a constrained sandbox and record commands, revisions, tests, assistance, and outputs as evidence. | Must         |

# 12 Nonfunctional Requirements

| **Area**           | **Requirement**                                                                                                               |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Explainability     | Every mastery update and recommendation must be traceable to evidence and a policy version.                                   |
| Latency            | Conversational feedback should begin within 3 seconds; complex scoring may complete asynchronously with status.               |
| Reliability        | No evidence event may be silently lost; scoring retries must be idempotent.                                                   |
| Accessibility      | Target WCAG 2.2 AA, keyboard navigation, captions or transcripts, and equivalent non-voice alternatives.                      |
| Privacy            | Private by default, purpose-limited collection, configurable retention, deletion, and export.                                 |
| Security           | Encryption in transit and at rest, tenant isolation, role-based access, and audit logs.                                       |
| Model governance   | Version prompts, models, rubrics, and policies; support rollback and retrospective evaluation.                                |
| Localization       | Architecture supports future localized content and rubrics; the first pilot is English only.                                  |
| Offline resilience | No completed response or accepted evidence may be lost after power loss, process termination, or interrupted synchronization. |
| Data efficiency    | Prioritize compact event sync; make large downloads explicit, resumable, and optionally Wi-Fi-only.                           |
| Device support     | Set and test minimum Android, memory, storage, and performance targets using representative rural-deployment hardware.        |

# 13 AI and Data Design

## 13.1 AI responsibilities

| **Component**        | **AI role**                                                       | **Required guardrail**                                                                   |
|----------------------|-------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| Tutor                | Explain, question, diagnose misconceptions, and provide feedback. | Ground responses in approved sources and provide authored offline fallbacks.             |
| Activity selector    | Rank eligible next activities.                                    | Use observable features and log the reason; begin with rules.                            |
| Assessment generator | Create controlled variants from approved templates.               | Human-approved blueprint, leakage checks, and item review sampling.                      |
| Scorer               | Apply a structured rubric to open responses and oral transcripts. | Confidence threshold, second-pass checks, and human escalation.                          |
| Mastery updater      | Combine evidence into a current estimate.                         | Run locally through a calibrated, versioned model with monotonic and policy constraints. |
| Integrity assistant  | Identify inconsistencies and trigger follow-up questions.         | Never infer deception from identity, emotion, gaze, or accent.                           |

## 13.2 Core entities

| **Entity**     | **Selected fields**                                                                                |
|----------------|----------------------------------------------------------------------------------------------------|
| Skill          | id, statement, domain, prerequisites, level, version                                               |
| Activity       | skills, modality, difficulty, duration, mode, allowed assistance                                   |
| Evidence event | learner, skill, outcome, rubric, independence, novelty, timestamp, provenance                      |
| Mastery state  | learner, skill, state, probability range, updated time, policy version                             |
| Misconception  | skill, diagnostic signals, remediation links                                                       |
| Recommendation | candidate set, selected activity, reason, policy version                                           |
| Stage decision | current stage, trigger evidence, eligible transitions, selected transition, reason, policy version |
| Review         | trigger, reviewer, decision, rationale, prior and revised score                                    |
| Sync event     | event id, device, local sequence, payload version, status, attempts, acknowledgment                |
| Content bundle | bundle id, locale, skills, version, size, manifest, signature, dependencies                        |

## 13.3 Initial mastery implementation

Start with an interpretable evidence-weighting model rather than an opaque end-to-end predictor. Correct independent transfer evidence should carry more weight than assisted practice. Contradictory recent evidence should reduce confidence. Older evidence should decay at a skill-specific rate. Prerequisites may influence recommendations, but a weak prerequisite should not automatically overwrite direct evidence for a downstream skill.

Once the pilot produces enough longitudinal data, compare Bayesian knowledge tracing, item-response approaches, and learned sequence models. Promotion should require better calibration and prediction of external transfer—not merely higher fit to internal quiz outcomes.

## 13.4 Content and assessment quality

- Maintain a human-approved assessment blueprint specifying skill coverage and cognitive demand.

- Version rubrics and preserve the rubric used for every historical score.

- Measure item difficulty, discrimination, exposure, ambiguity, and differential performance.

- Keep a secure holdout bank for transfer evaluation and refresh compromised items.

- Do not train or tune on the same responses used for final claims without a documented split.

# 14 Trust Integrity and Responsible Use

## 14.1 Integrity posture

The product should acknowledge that perfect authorship detection is not possible. It should make bounded claims about the conditions under which evidence was collected. Strong proof comes from converging behavior: solving, explaining, responding to novel probes, and retaining the skill—not from a single detector score.

## 14.2 Learner rights

- Know whether an activity is for learning, practice, or proof.

- Know what assistance is allowed and what data is collected.

- See the evidence behind a mastery claim and the limitations of that claim.

- Challenge an automated score and obtain human review where consequences are meaningful.

- Control sharing and revoke access to a profile where contractually and legally possible.

- Use an equivalent alternative when voice or a specific modality creates an accessibility barrier.

## 14.3 High-stakes boundary

Any future HR or credentialing use requires a separate governance review. The product must not present an internally generated mastery score as a validated employment predictor until job relevance, reliability, fairness, accommodations, consent, and human decision processes have been established for that exact use.

# 15 Success Metrics and Validation

## 15.1 North star

Verified durable mastery: the proportion of target skills that a learner demonstrates independently on a novel task and retains at a delayed check. This is more meaningful than lessons completed or time spent.

## 15.2 Metric hierarchy

| **Category**        | **Metric**                                                                                      | **MVP target or decision rule**                                             |
|---------------------|-------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| Validity            | Correlation or predictive performance against blind-scored external transfer tasks              | Materially outperform completion and conventional quiz-score baselines      |
| Calibration         | Observed success by predicted mastery band; Brier score or expected calibration error           | No material overconfidence; predefine acceptable calibration bands          |
| Learning            | Pre-to-post gain on secure equivalent forms                                                     | Positive gain versus comparison condition                                   |
| Retention           | Delayed independent performance after 2–4 weeks                                                 | Better retention than baseline experience                                   |
| Efficiency          | Verified mastery gained per learner hour                                                        | Improve without lowering external performance                               |
| Coverage            | Share of mastery claims supported by more than one evidence modality                            | At least 70% for claims shown as Mastered                                   |
| Trust               | Learner-reported clarity and fairness; dispute and overturn rates                               | Monitor by group and modality                                               |
| Engagement          | Diagnostic completion, weekly active learning, return for spaced review                         | Secondary; never substitute for validity                                    |
| Offline reliability | Sessions completed without internet, recovery after interruption, and unsynchronized-event loss | No accepted evidence loss; predefined crash-recovery and sync-success gates |
| Access efficiency   | Data transferred, storage used, battery impact, and time to provision a learner                 | Meet targets on representative low-cost hardware and intermittent networks  |

## 15.3 Pilot hypotheses

| **Hypothesis**                                                        | **Test**                                                                             | **Pass signal**                                                                |
|-----------------------------------------------------------------------|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|
| The mastery model predicts transfer better than completion.           | Compare external-task prediction using mastery estimate, quiz score, and completion. | Pre-registered improvement with uncertainty reported.                          |
| Adaptive selection improves efficiency.                               | Randomize adaptive path versus fixed sequence.                                       | Equal or better transfer performance in less time.                             |
| Multi-modal evidence improves calibration.                            | Ablate oral, hands-on, and delayed evidence.                                         | Full model reduces calibration error on holdout learners.                      |
| Proof Mode distinguishes assisted output from independent capability. | Compare Learning Mode artifacts with novel Proof Mode tasks.                         | Meaningful within-learner separation where assistance was substantial.         |
| Learners accept the distinction between modes.                        | Interview and survey after use.                                                      | Most learners understand the purpose and view constraints as proportionate.    |
| Offline access preserves outcomes.                                    | Compare offline-first and connected cohorts on equivalent content and proof tasks.   | No material loss in transfer performance after accounting for learner context. |
| The local hub improves access.                                        | Measure provisioning, completion, sync, and support burden with and without a hub.   | Higher successful access without unacceptable maintenance cost.                |

## 15.4 Guardrail metrics

- False-confidence rate: learners labeled Mastered who fail the external task.

- Group calibration gaps and accessibility-related completion gaps.

- Automated-score disagreement with trained human raters.

- Dispute rate, review latency, and score-overturn rate.

- Hallucinated or unsupported tutor responses per audited session.

- Assessment leakage, repeated item exposure, and compromised-task rate.

- Learner stress, perceived surveillance, and withdrawal attributed to Proof Mode.

- Lost or duplicated evidence events, unresolved sync conflicts, and days of unsynchronized data.

- Performance, battery, storage, and failure rates by supported device tier.

# 16 Analytics and Experimentation

Events should support reconstruction of the learner journey without capturing unnecessary sensitive data. Minimum events include activity recommended, activity started, assistance requested, response submitted, rubric scored, evidence accepted or rejected, mastery updated, recommendation overridden, review requested, review decided, and retention check completed.

Experiments must separate learning outcomes from engagement. A feature that increases session length but reduces transfer or increases overconfidence is a failure. Analysis plans should be written before viewing results for core validity claims.

# 17 Delivery Plan

| **Phase**                | **Duration** | **Deliverable**                                                                                               | **Exit criterion**                                                                              |
|--------------------------|--------------|---------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| 0 Discovery              | 3–4 weeks    | Pathway decomposition, assessment blueprint, learner research, sandbox feasibility, and pilot dataset plan    | One bounded Data Problem-Solving and Automation module and measurable external outcome approved |
| 1 Instrumented prototype | 6–8 weeks    | Offline diagnostic, mentor fallback, evidence schema, local persistence, manual review, and skill map         | End-to-end offline sessions run with 15–30 learners                                             |
| 2 Pilot MVP              | 8–12 weeks   | Proof Mode, mastery updater, content packs, personal-device synchronization, retention, and instructor review | 100–300 learner pilot completed across representative devices and connectivity conditions       |
| 3 Validation             | 4–6 weeks    | Calibration, transfer, subgroup, and qualitative findings                                                     | Go, revise, or stop decision against pre-registered gates                                       |
| 4 Productization         | TBD          | Authoring tools, tenant controls, stronger review operations                                                  | Only after validity and demand are supported                                                    |

# 18 Risks and Mitigations

| **Risk**                 | **Why it matters**                                                                       | **Mitigation**                                                                                                   |
|--------------------------|------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| False mastery confidence | A polished score could overstate real capability.                                        | Calibrate to external tasks, show uncertainty, require converging evidence.                                      |
| AI scoring inconsistency | Equivalent answers may receive different judgments.                                      | Versioned rubrics, repeated scoring checks, human review thresholds.                                             |
| Assessment leakage       | Generated or reused tasks may become searchable or memorized.                            | Secure holdouts, variants, exposure tracking, dynamic defense questions.                                         |
| Goodhart's law           | Learners optimize the score rather than the capability.                                  | Use varied novel tasks and keep outcome evaluation separate.                                                     |
| Bias and accessibility   | Voice, language, disability, or culture may affect performance unrelated to skill.       | Alternate modalities, subgroup calibration, accommodations, appeal.                                              |
| Surveillance creep       | Integrity features can become invasive and damage trust.                                 | Prohibit biometric or emotion inference; minimize collection and state limits.                                   |
| Content quality          | Incorrect explanations or ambiguous questions teach the wrong thing.                     | Approved sources, authoring workflow, audit sampling, issue reporting.                                           |
| Cold start               | The model lacks enough evidence for a new learner or skill.                              | Explicit Unknown state, compact diagnostic, conservative claims.                                                 |
| HR misuse                | Scores may be treated as definitive hiring evidence.                                     | Separate product boundary, contractual controls, human review, use-case validation.                              |
| Cost and latency         | Voice, long context, and repeated scoring can be expensive.                              | Tiered models, caching, structured rubrics, asynchronous review.                                                 |
| Low-end device limits    | Local AI, media, or large content packs may exceed memory, storage, or battery capacity. | Hardware tiers, small bundles, authored fallbacks, hub inference, and field benchmarks.                          |
| Sync failure             | Long offline periods or retries may lose, duplicate, or conflict with evidence.          | Append-only event log, stable IDs, acknowledgments, resumable transfer, and conflict review.                     |
| Unequal experience       | Connected learners may receive stronger AI or faster review than offline learners.       | Measure outcome parity, keep core pathways equivalent, and disclose pending enhanced review.                     |
| Hub operations           | Local servers can fail or become difficult for schools to maintain.                      | Simple appliance design, health checks, replaceable storage, administrator training, and offline recovery media. |

# 19 Product Decision Register

Decided items are approved product constraints. Recommended items remain proposals until confirmed through discovery, feasibility testing, or pilot governance review.

| **Decision**                        | **Options**                                                                                                                                        | **Direction**                                                                                                                                                                 |
|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **1 First pilot module**            | A. Inventory and small-business operations; B. Community-service records; C. Personal finance and budgeting.                                       | Recommended: A. It supports realistic spreadsheet, SQL, validation, and automation tasks using safe synthetic data, with broad relevance and clear transfer measures.         |
| **2 Initial buyer**                 | Learner; training provider; university program; employer-sponsored academy.                                                                        | Decided: Learner. Begin with direct learner value and demand; treat institutions as later distribution or buyer channels.                                                     |
| **3 Mastery threshold**             | A. One universal score; B. Fully domain-specific thresholds; C. Shared evidence minimum plus domain-specific rubric thresholds.                    | Recommended: C. Require common evidence qualities such as independence, novelty, and retention, then calibrate task thresholds for each skill domain.                         |
| **4 Proof Mode friction**           | A. Minimal constraints; B. Moderate bounded sessions and dynamic follow-ups; C. High-control remote proctoring.                                    | Recommended: B. Use novel tasks, declared assistance rules, interaction history, and short defense questions; avoid biometric or surveillance-heavy controls.                 |
| **5 Retention interval**            | A. 7 days; B. 14 days; C. 28 days; D. Multiple intervals.                                                                                          | Recommended: D, with day 14 as the primary MVP outcome and day 28 as a smaller durability check where pilot duration permits.                                                 |
| **6 Evidence portability**          | A. Product-only report; B. Learner-controlled signed export; C. Immediate adoption of an external credential standard; D. Defer portability.       | Recommended: B. Export a human-readable summary plus signed structured evidence; map to external standards only after the evidence model stabilizes.                          |
| **7 Mandatory human review**        | A. Review every open response; B. Review only disputes; C. Review low-confidence, disputed, high-impact, and sampled cases.                        | Recommended: C. Target review within three business days during the pilot and audit a random sample of otherwise accepted automated decisions.                                |
| **8 Data retention**                | A. Indefinite retention; B. Fixed short retention; C. Active-account retention plus deletion after inactivity; D. Learner-selected retention only. | Recommended: C. Retain while active, default to deletion 24 months after inactivity, and provide export and deletion controls subject to documented legal obligations.        |
| **9 Minimum device profile**        | A. Android 8 with 2 GB RAM; B. Android 10 with 3 GB RAM and 2 GB free storage; C. Android 12 with 4 GB RAM.                                        | Recommended: B as the supported baseline, while testing a reduced text-and-SQL experience on selected 2 GB devices before making a broader claim.                             |
| **10 First deployment model**       | Personal-device offline use; school or community hubs; both from launch.                                                                           | Decided: Personal-device offline use. Design formats for future hubs, but do not make hub hardware or administration an MVP dependency.                                       |
| **11 Pilot language**               | English only; English plus Filipino; English plus multiple local languages.                                                                        | Decided: English only for the pilot. Preserve localization architecture and equivalent non-voice paths for later expansion.                                                   |
| **12 Provisional offline evidence** | A. No time limit; B. Fixed expiry; C. Local reviewer finalization; D. Tiered rule based on intended use.                                           | Recommended: D. Never discard learning progress, but prevent externally shared verified claims after 30 unsynchronized days unless a qualified local reviewer finalizes them. |

# 20 Launch Decision Gates

Proceed beyond pilot only if the product demonstrates all of the following:

- The mastery estimate predicts blind-scored transfer meaningfully better than completion and ordinary quiz scores.

- Calibration is acceptable overall and no critical subgroup shows unexplained severe overconfidence.

- Learners understand the difference between Learning Mode and Proof Mode and do not experience the integrity design as disproportionate surveillance.

- AI tutor and scorer errors remain within predefined operational thresholds, with effective review and correction.

- At least one target customer segment shows willingness to adopt or pay for the validated outcome.

- The full core loop functions on supported low-cost devices without internet and survives power, process, and synchronization interruptions without accepted evidence loss.

- Offline learners achieve comparable transfer outcomes and are not systematically disadvantaged by delayed AI or human review.

If predictive validity fails, the team should not compensate with more content modalities or stronger marketing. It should revise the skill definitions, evidence design, or measurement model and repeat validation.

# Appendix A Example Skill Module

Illustrative domain: Data Problem-Solving and Automation. This example decomposes a broad pathway into observable skills that can be practiced and verified offline.

| **Skill**                        | **Evidence sequence**                                               | **Mastery requirement**                                               |
|----------------------------------|---------------------------------------------------------------------|-----------------------------------------------------------------------|
| Validate a dataset               | Inspect schema and quality → identify defects → justify corrections | Independent detection and repair across two unfamiliar datasets       |
| Summarize data accurately        | Choose measures → calculate results → check against source records  | Correct result plus explanation of assumptions and limitations        |
| Query related tables             | Trace keys → write a join → diagnose duplicate or missing rows      | Independent query and validation on a novel schema                    |
| Automate a repeatable workflow   | Describe steps → implement rules or script → test edge cases        | Working automation with reproducible checks and safe failure behavior |
| Communicate a defensible finding | Select evidence → create a clear view → answer challenge questions  | Accurate conclusion that survives an unfamiliar follow-up question    |

# Appendix B Example Evidence Summary

| **Field**              | **Illustrative value**                                                                  |
|------------------------|-----------------------------------------------------------------------------------------|
| Skill                  | Detect and repair inconsistent units in tabular data                                    |
| Current state          | Demonstrated; confidence moderate                                                       |
| Strongest evidence     | Unassisted cleaning and SQL summary on an unfamiliar inventory dataset, rubric 4 of 5   |
| Supporting evidence    | Explanation correctly described type, unit, and validation decisions                    |
| Contradictory evidence | Needed two hints on an earlier duplicate-record task                                    |
| Coverage gap           | No evidence yet for multi-table joins with missing keys                                 |
| Next action            | Transfer task using clinic-supplies records                                             |
| Review date            | In 14 days to test retention                                                            |
| Limit                  | This claim concerns a narrow data-cleaning skill, not general data-analysis proficiency |

# Appendix C Definition of Done for Pilot MVP

- A learner can complete the diagnostic, receive a transparent skill map, and begin a recommended activity.

- The learner can complete the core loop in airplane mode using a downloaded content pack.

- Learning and Proof Mode events record permitted assistance and evidence provenance.

- At least three evidence modalities update the learner model through versioned rules.

- Every loop transition is reproducible from its evidence and policy version, and the learner receives a plain-language reason for the next activity.

- Low-confidence and disputed scores reach a reviewer queue with full context.

- The team can reproduce every mastery state from immutable evidence events and policy versions.

- Power interruption, application termination, and repeated synchronization do not lose or duplicate accepted evidence.

- Representative personal devices can be provisioned through downloaded or physically transferred content packs and complete the pilot without a school hub.

- The experience meets defined performance, storage, battery, and accessibility targets on supported low-cost hardware.

- The pilot includes a secure external transfer outcome and a pre-specified analysis plan.

- Privacy, accessibility, and model-risk reviews are completed before external recruitment.
