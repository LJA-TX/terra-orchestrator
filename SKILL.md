---
name: terra-orchestrator
description: "Economical heterogeneous orchestration for explicitly invoked, confirmed GPT-5.6 Terra parent tasks. Use for multi-stream work when a rolling GPT-5.6 Luna worker pool can improve quality, cost, or elapsed time; do not use to change models or on Luna-parent tasks."
---

# Terra Orchestrator

Schedule a confirmed Terra parent as the chief reasoner while using Luna for
independent work that can meet the required standard. Optimize jointly for
quality, safety, Terra capacity, elapsed time, and coordination cost.

## Activation and authority

- Activate only when explicitly invoked as `$terra-orchestrator` and the parent
  is confirmed to be a GPT-5.6 Terra variant, normally Terra Ultra.
- Do not select, change, or imply a change to the parent model. If the parent is
  not confirmed Terra, state that this skill is inactive and follow the ordinary
  applicable policy without Terra-specific scheduling.
- Read the applicable `AGENTS.md` files and task constraints before scheduling.
  Treat system, developer, User, and repository instructions as binding limits;
  this skill only allocates heterogeneous capacity inside those limits.
- Use only the permitted internal child-agent mechanism. Respect the governing
  concurrency, spawning, nesting, scope, and mutation rules. Do not create
  user-facing threads to simulate delegation.
- Do not create nested children unless governing policy permits them and a
  separate, concrete payoff justifies the extra coordination layer.

## Keep a live work board

Before substantial work, map the remaining task into a compact internal board:

| Workstream | State | Class | Owner | Dependency | Mutation boundary | Bounded output |
|---|---|---|---|---|---|---|
| example | ready | Luna | unassigned | none | read-only | evidence summary |

Use these classes:

- **Terra:** central architecture, hard cross-cutting reasoning, security-sensitive
  judgment, conflict resolution, difficult integration, and final verification.
- **Luna:** bounded investigation, implementation with disjoint ownership,
  testing, validation, review, documentation, platform analysis, evidence
  gathering, or contained debugging. Importance or apparent complexity alone
  does not make work Terra-class.
- **Blocked/sequential:** work whose prerequisite or decision is not yet ready.
- **Integration/orchestration:** parent-owned reconciliation, dependency
  management, scope control, and scheduling.

Refresh the board rather than treating the first decomposition as final. Mark
each ready item with its expected payoff, dependencies, risks, and whether its
result can proceed independently.

## Dispatch Luna first

Keep the central critical path with the Terra parent when its reasoning quality
materially shapes the whole result. Around that path, dispatch each meaningful,
ready, independent Luna-suitable workstream early using **GPT-5.6 Luna**
(`gpt-5.6-luna`).

Give every worker a bounded packet containing:

- the exact question, files, or artifact scope;
- the deliverable and success checks;
- read-only versus explicit disjoint mutation ownership;
- relevant policy and stop conditions;
- dependencies and facts the worker must not assume; and
- a request to return evidence, uncertainty, and changed paths.

For concurrent mutations, assign non-overlapping paths or artifacts. Keep
tightly coupled edits on the parent critical path, or use Luna for read-only
investigation and review instead.

Use the lower of the governing concurrency cap, the number of useful ready
workstreams, and safe coordination capacity. Start a small productive pool;
never create work merely to fill slots.

## Run a rolling worker pool

Reassess the board at all of these checkpoints:

1. after a worker returns or completes;
2. when a prerequisite makes a workstream ready;
3. when integration exposes follow-up work;
4. before the parent begins a substantial new direct workstream; and
5. when active Luna utilization falls materially while significant ready work remains.

At each checkpoint:

1. Evaluate returned work enough to update facts, risks, and dependencies; do
   not redo it by default.
2. Reclassify the remaining work and identify independent Luna-suitable items.
3. If a useful item is ready and capacity is available, assign it before the
   parent consumes that workstream.
4. Prefer a related, addressable completed Luna worker for follow-up when its
   context remains useful and reuse will not create scope confusion. Otherwise
   replenish with a new Luna worker within the governing cap.
5. If no dispatch is appropriate, retain or begin the parent work and note the
   concrete reason: no independent work, coordination cost exceeds benefit,
   policy forbids it, or Luna is not adequate for the risk.

Treat a completed Luna worker as a scheduling event, not the end of
delegation. This specifically prevents an early burst of Luna work followed by
an unexamined long Terra-only tail.

Apply a **tail guard** after the first worker batch returns: make a fresh
dispatch decision before the parent takes downstream tests, documentation,
validation, implementation, or review. Keep synthesis and acceptance with
Terra, but give Luna a bounded draft, check, or analysis whenever it can
advance independently. Do not use “integration” as a reason to absorb all
preceding Luna-suitable work.

## Allocate parent attention by fan-out

With zero or one active worker, spend substantial parent effort on the
critical Terra-class stream. With multiple active workers, increasingly reserve
parent attention for incoming-result evaluation, dependency release,
follow-up assignment, conflicts, integration, and genuinely critical
Terra-class work.

Do not turn the parent into an idle dispatcher. Do not let it take a
noncritical Luna-suitable direct workstream while useful Luna capacity is
available, but do let it advance the central path when waiting would harm
quality or elapsed time.

## Use Terra children only as concurrent overflow

Spawn a **GPT-5.6 Terra** child (`gpt-5.6-terra`) only when both conditions
hold:

1. the bounded delegated work genuinely needs Terra-class reasoning; and
2. the parent must concurrently retain a different central Terra-class or
   integration responsibility, so absorbing the work itself would create a
   meaningful bottleneck.

Record the concrete reason for both conditions, the work the parent is
retaining, and why Luna is insufficient. If either condition is absent, keep
the work with the parent or use Luna as appropriate. A Terra child is extra
concurrent reasoning capacity, never a prestige default or a way to switch the
parent model.

## Integrate results skeptically

Treat child results as inputs, not authority. Check assumptions, evidence,
scope, mutation ownership, and risk before incorporating them. Resolve
conflicts in the parent, and use independent review only when it adds real
verification value.

Take a workstream back to Terra when Luna repeatedly fails, lacks the needed
capability, or raises material correctness or safety risk. Preserve quality
over token economy.

Avoid delegation for trivial, tiny, inherently serial, immediately
parent-dependent, or overly coupled work. Avoid duplicate parent effort unless
independent verification is justified. Favor direct work when delegation would
add more latency or coordination cost than it removes.

## Close with an orchestration report

Include a concise final report whenever this skill was active:

- **Delegated:** workstreams and whether Luna or Terra handled each; mention
  meaningful Luna follow-ups or reuse.
- **Terra retained:** major architecture, critical-path, integration, security,
  or final-verification work.
- **Terra children:** `none`, or each one with the concrete two-condition
  justification.
- **Intentional non-delegation:** notable ready work kept with the parent and
  why.

## Tooling limits

This skill is a parent-operated scheduling discipline, not an autonomous
scheduler. It cannot verify or change the parent model, reserve capacity,
obtain token-cost telemetry, receive completion callbacks on its own, or force
reuse of a worker that is no longer addressable. Observe worker status at the
checkpoints and issue permitted spawn or follow-up actions manually.
