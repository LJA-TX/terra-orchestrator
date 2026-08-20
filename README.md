# Terra Orchestrator

`terra-orchestrator` is a Codex skill for tasks whose parent model is already GPT-5.6 Terra. Terra stays the chief reasoner and integrator. Independent work may be delegated to a bounded, rolling pool of GPT-5.6 Luna workers when that is likely to improve quality, cost, or elapsed time.

It does not select or change the parent model. Invoke it explicitly with `$terra-orchestrator`.

## When to use

Use the skill when:

- the parent is confirmed to be GPT-5.6 Terra; and
- the task has meaningful independent workstreams that Luna can advance.

It is not intended to switch models, to run Luna-parent tasks, or to split trivial, tightly coupled, or inherently serial work.

This requires a confirmed GPT-5.6 Terra parent, commonly at Ultra reasoning effort. “Ultra” describes the reasoning effort; it is not a separate model. The skill remains inactive when the parent is not confirmed Terra.

## Installation

Place the `terra-orchestrator` directory in one of the host's supported Codex skill locations:

- user-wide: `$HOME/.agents/skills/terra-orchestrator/`
- repository-local: `$REPO_ROOT/.agents/skills/terra-orchestrator/`

Preserve the relative layout, including:

```text
terra-orchestrator/
  SKILL.md
  agents/
    openai.yaml
```

The `agents/openai.yaml` file is functionally important. This release sets `allow_implicit_invocation: false`, so omitting or relocating that metadata can change the skill's activation behavior. See the [official Codex skills documentation](https://developers.openai.com/codex/skills) for host-level installation guidance.

## Human use

The User-facing procedure is short:

1. Install the skill in a supported location.
2. Confirm that the selected parent is GPT-5.6 Terra.
3. Include an explicit `$terra-orchestrator` invocation in the task prompt.

For example:

```text
$terra-orchestrator Implement the parser, add tests, and update the docs. Keep architecture and final review with Terra.
```

After invocation, the Terra parent builds and maintains the work board, dispatches useful bounded Luna work, reassesses the rolling worker pool, applies the tail guard, and keeps synthesis, acceptance, and final verification. It reports the resulting delegation, retained work, and intentional non-delegation to the User.

## Operating model

- **Luna is the default bounded worker.** GPT-5.6 Luna handles useful independent investigation, implementation, testing, validation, review, documentation, platform analysis, evidence gathering, or contained debugging.
- **The worker pool is rolling.** The parent dispatches useful ready work early, reassesses when work completes or becomes unblocked, and replenishes only when the expected benefit exceeds coordination cost.
- **The tail guard prevents silent absorption of downstream work.** After an initial Luna batch returns, the parent makes another delegation decision before silently taking on downstream tests, documentation, validation, implementation, or review that Luna could still advance.
- **Terra children are constrained overflow.** A GPT-5.6 Terra child is used only when the delegated work genuinely needs Terra-class reasoning, the parent must concurrently retain a different central Terra-class or integration responsibility, and Luna is insufficient.

Workers receive bounded packets with a defined scope, deliverable, success checks, mutation boundary, dependencies, and stop conditions. Their results are inputs, not authority; the Terra parent checks assumptions, evidence, scope, ownership, and risk before integration.

Delegation uses the host's permitted native child-agent mechanism. The skill does not open separate User chats merely to imitate delegation; it does not prohibit the host's own inspectable child-agent behavior.

## Requirements and limits

The skill requires a Codex environment in which the permitted child-agent mechanism can launch GPT-5.6 Luna workers. It also requires a confirmed GPT-5.6 Terra parent and compliance with the governing concurrency and task-policy rules.

The skill cannot verify or change the parent model, reserve capacity, obtain token-cost telemetry, receive completion callbacks autonomously, or force reuse of a worker that is no longer available. It is a parent-operated scheduling discipline, not an autonomous scheduler.

## Repository layout

- `SKILL.md` — normative orchestration policy.
- `agents/openai.yaml` — host-facing skill metadata and explicit-invocation policy.
- `LICENSE` — MIT license.
- `README.md` — overview, boundaries, installation, and use.
- `CHANGELOG.md` — release history.

## Roadmap

This roadmap is directional and does not promise unreleased capabilities.

- **v1.1:** Refinements from field use of v1.0.
- **v2:** Later orchestration hardening.
- **v3:** Later usability and observability work.

## License

MIT; see [`LICENSE`](LICENSE).
