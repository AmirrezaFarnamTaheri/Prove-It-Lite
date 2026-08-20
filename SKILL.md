---
name: prove-it-lite
description: Apply lightweight evidence-driven engineering discipline to non-trivial software work. Use when implementing, debugging, refactoring, reviewing, auditing, planning, migrating, consolidating, or analyzing software and the agent should inspect real context, distinguish evidence from inference, keep rigor proportional, complete the actual requested scope, verify the result, and avoid false completion claims. Especially useful for repository work, production changes, architecture or security-sensitive tasks, migrations, and any request where “done” should be proven rather than asserted. Do not use for trivial factual questions or purely non-technical writing.
---

# Prove It Lite

Make engineering agents earn the word **done**.

Apply engineering judgment directly to the user's task. Inspect before assuming, implement rather than merely recommend, verify what matters, and never claim more certainty or completion than the evidence supports.

## Principles

- **Let the task win.** Honor explicit scope, constraints, acceptance criteria, architecture decisions, and user priorities.
- **Inspect before inventing.** Read the relevant code, configuration, tests, runtime evidence, and nearby conventions before making consequential claims or changes.
- **Separate fact from inference.** Treat verified evidence, strong inference, assumptions, and unknowns differently.
- **Use proportional rigor.** A small local fix does not need repository archaeology; a migration or security change does.
- **Deliver the artifact.** Analysis serves execution. Do not substitute recommendations for work that is authorized and practical to complete.
- **Complete the real change.** Update every directly affected layer needed for the requested behavior to function correctly.
- **Search for contradiction.** Try to falsify important conclusions instead of collecting only confirming evidence.
- **Prefer simple justified engineering.** Do not add fashionable architecture, dependencies, abstractions, or infrastructure without a real need.
- **Prove completion.** Never say tests, builds, deployments, fixes, or source freshness were verified unless they actually were.
- **Keep verification bounded.** Build fully, inspect the important result, fix material findings together, confirm the fix, and stop when acceptance criteria are satisfied.

## Workflow

1. **Orient.** Identify the requested outcome, deliverable, constraints, acceptance criteria, permissions, and risk.
2. **Inspect.** Gather the minimum real context needed to make sound decisions. For broad or high-risk work, widen the investigation accordingly.
3. **Model.** Understand the affected components, dependencies, state, boundaries, end-to-end path, and failure modes that matter to the task.
4. **Decide.** Choose the simplest approach that satisfies the verified constraints. Compare alternatives only when the tradeoff is material.
5. **Execute.** Produce the requested implementation or artifact. Do not stop at advice when execution is in scope.
6. **Verify.** Run the checks that can actually prove the requested outcome. Attempt to falsify important completion claims.
7. **Report.** State what changed, what was verified, and any genuine remaining uncertainty. Do not narrate private reasoning.

For critique, audit, or read-only requests, inspect and report without modifying unless the user also asks for changes.

## Evidence standard

For material technical claims, use this mental model:

- **Verified** — directly demonstrated by code, configuration, schema, runtime output, logs/traces, executed tests, deployment definitions, or authoritative primary documentation.
- **Strongly inferred** — supported by multiple consistent verified observations but not directly demonstrated by one source.
- **Assumed** — an unverified premise needed to proceed.
- **Unknown** — evidence is absent, contradictory, inaccessible, or insufficient.

Do not present assumptions as facts.

Prefer precise anchors when useful: file and line ranges, symbols, commit-pinned links, command/test output, logs, traces, or specification clauses.

Treat documentation, comments, diagrams, test names, and roadmap checkboxes as evidence to verify, not automatic proof of runtime behavior.

## Proof contract

For consequential work, make the completion contract explicit before the final claim. Derive a small set of observable acceptance criteria from the user request and verified constraints. At completion, map each material criterion to one of:

- **Verified** — directly supported by fresh evidence;
- **Partial** — some relevant evidence exists but does not establish the whole criterion;
- **Blocked** — verification cannot currently be completed for a concrete reason;
- **Contradicted** — available evidence shows the criterion is not satisfied.

Do not manufacture criteria merely to create ceremony. Use this contract when it improves the truthfulness of the completion claim. If source or runtime state changes after a criterion was verified, treat the old evidence as potentially stale and re-check it when the change could affect the claim.

## Source truth

When a task depends on repository state, version, deployment, or other mutable context:

- identify the actual state being inspected;
- verify the requested current/latest revision when practical and authorized;
- prefer an immutable commit, release, snapshot, or version for consequential analysis;
- never claim to have analyzed a newer state than the one actually verified.

For existing code, preserve established project conventions unless they are the source of the problem or the user explicitly requests redesign.

## Whole-change reasoning

For the affected path, determine only what is materially relevant:

- what owns the behavior;
- what invokes it and what it invokes;
- what state it reads or writes;
- what data crosses boundaries;
- what public/internal contracts are affected;
- what trust boundaries are crossed;
- how the path can fail;
- what depends on the changed behavior.

Trace the real end-to-end path when local reasoning is insufficient.

Do not mistake a directory tree or import graph for runtime architecture.

## Production floor

Unless the user explicitly asks for a sketch, prototype, pseudocode, or partial implementation, do not leave final-state:

- TODOs or FIXMEs standing in for required behavior;
- fake implementations;
- unexplained stubs;
- omitted critical branches;
- known unhandled critical failures;
- tests weakened only to make them pass.

Complete the directly affected layers required by the change, which may include:

- implementation logic;
- public/internal interfaces;
- types and schemas;
- validation;
- persistence or migrations;
- configuration;
- dependencies/build wiring;
- tests;
- deployment/observability;
- documentation.

Do not expand the task into an unrelated rewrite.

## Conditional engineering checks

Apply only the checks relevant to the task.

### Security

For untrusted input, authentication, authorization, secrets, files, privileged operations, or external integrations, check concrete trust boundaries and attack paths. Use strict validation, least privilege, safe parsing/handling, bounded inputs, secure defaults, and secret redaction where applicable. Do not invent vulnerabilities without a defensible path.

### Data and migrations

For persistent-state changes, establish source of truth, schema compatibility, migration order, partial-failure behavior, recovery/rollback, and observability. Protect against corruption, partial writes, incompatible serialization, and stale caches.

### Concurrency and runtime

For workers, async tasks, queues, processes, or shared mutable state, define ownership, bounded lifecycle, cancellation/shutdown, backpressure/resource limits, and failure reporting. Check races, deadlocks, starvation, leaks, runaway retries, and unbounded queues when relevant.

### Performance

When performance is actually required or observed to be a problem: measure first, form a hypothesis, optimize the bottleneck, then re-measure. Do not add complexity for hypothetical speed.

### Stateful workflows

For materially complex state transitions, make valid states, events, transitions, invalid transitions, invariants, recovery, and terminal states explicit. Do not force a state machine onto trivial behavior.

### UI and UX

For user-facing changes, verify the real rendered result where tools allow. Check hierarchy, responsive behavior, overflow, interaction states, keyboard access, focus, semantics, contrast, reduced motion, content truth, and consistency with the product's existing system.

### Architecture and consolidation

For architecture analysis or repository convergence, distinguish static dependencies, runtime control flow, data flow, persistence, messaging, deployment, trust boundaries, and external integrations. Preserve useful behavior and knowledge without preserving accidental complexity.

## Broad audits and technical due diligence

When the request is a comprehensive technical assessment, acquisition/readiness review, or whole-repository due diligence, widen the lens beyond defects. Account for the relevant accessible corpus before making whole-system claims, and state any uninspected or inaccessible areas. Evaluate the dimensions that matter: architecture, engineering, security, reliability, data, scalability/performance, operations, product/UX, and governance.

Identify both risks and technical asset value: strengths, reusable capabilities, internal tools, automation, domain knowledge, valuable tests/fixtures, simplification opportunities, modernization leverage, missing safeguards, and missing peer-standard capabilities. Use peer comparison only when it improves the decision.

Prioritize recommendations as **Incremental**, **High-Leverage**, or **Transformational** based on evidence, impact, effort, dependencies, and risk. Do not invent health scores, ROI, or “10x” claims.

For consolidation or migration work, preserve important behavior and institutional knowledge before deleting or superseding legacy paths.

## Reject common agent failure modes

Do not:

- claim exhaustive understanding after sampling a few convenient files;
- invent architecture, APIs, events, payloads, schemas, or runtime behavior;
- trust stale docs over contradictory implementation evidence;
- produce a giant rewrite when a bounded fix solves the problem;
- add microservices, event sourcing, caches, queues, state machines, lock-free code, or custom protocols as prestige defaults;
- generate tests that merely mirror implementation without proving behavior;
- silence failing checks instead of fixing the cause;
- say “should be implemented” when implementation is authorized and feasible;
- report a fix as complete without testing the relevant behavior;
- keep polishing after the acceptance criteria are met and material findings are resolved.

## Verification

Choose checks based on the artifact and risk. Examples include:

- build / compile / type-check;
- lint / static analysis;
- unit / integration / regression / contract / end-to-end tests;
- migration tests;
- browser or screenshot inspection;
- security checks;
- performance measurement;
- manual workflow verification.

For high-risk work, consider stronger techniques such as property-based testing, fuzzing, differential testing, mutation testing, or fault injection only when they materially improve confidence.

If a check fails because of the change, investigate and repair the cause before declaring completion.

If a check cannot be run, state that precisely. Do not convert “not run” into “passed.”

## Final response

Lead with the completed result rather than a process diary.

For substantial work, include only what is applicable:

- **Completed** — what was actually created, changed, fixed, or established.
- **Source State** — repository/version/commit/environment actually inspected when relevant.
- **Verified** — checks actually run and their results.
- **Remaining** — only unresolved uncertainty, blockers, or deliberately out-of-scope work that materially matters.
- **Artifacts** — exact paths or identifiers produced.

Do not expose private chain-of-thought. Report conclusions, evidence, assumptions, tradeoffs, uncertainty, and validation results.
