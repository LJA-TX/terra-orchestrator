# terra-orchestrator

`terra-orchestrator` is an explicitly invoked Codex skill for economical heterogeneous orchestration of confirmed GPT-5.6 Terra parent tasks. It keeps Terra as the chief reasoner and integrator while using a bounded, rolling GPT-5.6 Luna worker pool for independent work that can improve quality, safety, elapsed time, Terra capacity, or coordination cost.

## Activation and authority

Invoke the skill explicitly:

```text
$terra-orchestrator
```

The parent must be confirmed as a GPT-5.6 Terra variant, normally Terra Ultra. The skill is inactive for an unconfirmed parent and for Luna-parent tasks. It does not select, change, or imply a change to the parent model.

System, developer, user, repository, and applicable `AGENTS.md` instructions remain binding. Terra retains the central critical path, architecture, dependency management, conflict resolution, synthesis, scope control, acceptance, and final verification.

## Operating model

- **Terra is the chief reasoner and integrator.** It owns the decisions that require cross-cutting judgment and reconciles worker results.
- **Luna is the default bounded worker.** GPT-5.6 Luna handles useful independent investigation, implementation, testing, validation, review, documentation, platform analysis, evidence gathering, or contained debugging.
- **The worker pool is rolling.** Maintain a compact work board, dispatch useful ready work early, reassess after completions and newly unblocked work, and replenish only when the expected benefit exceeds coordination cost.
- **The tail guard protects the downstream work.** After an initial worker batch returns, make a fresh delegation decision before Terra absorbs downstream testing, documentation, validation, implementation, or review.
- **Terra children are constrained overflow.** Use a GPT-5.6 Terra child only when the delegated work genuinely needs Terra-class reasoning and the parent must concurrently retain a different central Terra-class or integration responsibility. Luna must be insufficient for that work.

Workers receive bounded packets with a defined scope, deliverable, success checks, mutation boundary, dependencies, and stop conditions. Their results are inputs, not authority; Terra checks assumptions, evidence, scope, ownership, and risk before integration. The skill uses only the permitted internal child-agent mechanism and does not create user-facing threads to simulate delegation.

## Installation and use

Make this directory available to the host's supported skills location, preserving its relative paths and the files in `SKILL.md` and `agents/openai.yaml`. The exact installation location is host-specific; use the host's documented user-scoped or repository-local skill discovery rules.

To use the skill:

1. Confirm that the parent is a GPT-5.6 Terra variant.
2. Invoke `$terra-orchestrator` explicitly.
3. Read the applicable task instructions and establish the work board.
4. Dispatch bounded Luna work when it is independently useful.
5. Reassess the rolling pool, including the tail guard.
6. Keep synthesis, acceptance, and final verification with Terra.
7. Report delegated work, Terra-retained work, Terra children, and intentional non-delegation.

## Repository layout

- `SKILL.md` — normative orchestration policy.
- `agents/openai.yaml` — host-facing skill metadata and explicit-invocation policy.
- `LICENSE` — MIT license.
- `README.md` — overview, boundaries, and use.
- `CHANGELOG.md` — release history.

## Requirements and limits

The design requires explicit invocation, a confirmed GPT-5.6 Terra parent, access to the permitted internal child-agent mechanism, compliance with governing concurrency and task-policy rules, and manual observation and scheduling by the parent.

The skill cannot verify or change the parent model, reserve capacity, obtain token-cost telemetry, receive completion callbacks autonomously, or force reuse of an unavailable worker. It is a parent-operated discipline, not an autonomous scheduler.

## Roadmap

This roadmap is directional and does not promise unreleased capabilities.

- **v1.1:** Refinements arising from our own field observations.
- **v2:** Later orchestration hardening.
- **v3:** Later usability and observability work.

## License

MIT; see [`LICENSE`](LICENSE).
