# Prove It Lite

**One skill. No compiler, profiles, adapters, eval harness, or orchestration machinery. Just evidence-driven engineering judgment.**

Prove It Lite teaches coding agents to inspect before assuming, implement instead of merely recommending, use rigor proportional to the task, verify meaningful outcomes, and stop making unsupported “done” claims.

It is the distilled companion to **Prove It**, the full modular framework. Use Lite when you want a single portable `SKILL.md`. Use full Prove It when you want composable profiles, task templates, model adapters, prompt generation, regression evals, and the optional local MCP proof engine.

## What it changes

Without a discipline layer, coding agents often fail in predictable ways: they infer whole systems from a few files, trust documentation over implementation, make local fixes without tracing affected paths, over-engineer simple problems, under-test risky ones, or claim success because code was written rather than because behavior was verified.

Prove It Lite adds a compact operating standard:

- artifact-first execution;
- source truth before speculation;
- verified / inferred / assumed / unknown evidence discipline;
- proportional investigation and verification;
- contradiction search for important conclusions;
- complete affected-layer implementation;
- conditional security, data, concurrency, performance, UI, architecture, and due-diligence checks;
- bounded verification and an explicit stop rule;
- honest completion reporting.

## Install

Create a `prove-it-lite` directory in your agent's skills location and place [`SKILL.md`](SKILL.md) inside it.

Common project-level locations include:

| Agent | Directory |
| --- | --- |
| Claude Code | `.claude/skills/prove-it-lite/` |
| Codex | `.agents/skills/prove-it-lite/` |
| Cursor | `.cursor/skills/prove-it-lite/` |
| Gemini CLI | `.gemini/skills/prove-it-lite/` |
| GitHub Copilot | `.github/skills/prove-it-lite/` |
| OpenCode | `.opencode/skills/prove-it-lite/` |

Personal/global skill directories vary by agent. Use the platform's documented skills directory and keep the folder name `prove-it-lite`.

If your agent does not support Agent Skills, copy the body of `SKILL.md` into the project's agent instructions. In that fallback mode the guidance becomes always-on rather than conditionally loaded.

## Use

Once installed, ask for normal engineering work:

```text
Fix the authorization regression in this API and prove the fix.
```

```text
Audit this migration before I ship it.
```

```text
Refactor this worker without changing behavior and verify the important paths.
```

```text
Map the actual runtime architecture of this repository.
```

The skill is designed to activate for non-trivial engineering work without requiring a special command. Agents that support explicit skill invocation can also invoke `prove-it-lite` directly.

## Philosophy

The goal is not maximum ceremony. The goal is **the minimum rigor required to justify the conclusion**.

A CSS fix should stay small. A schema migration should not. A security-sensitive path should earn stronger evidence than a copy edit. Sophisticated techniques are tools, not prestige defaults.

For broad technical due diligence, Lite also pushes the agent to inspect the relevant corpus, evaluate architecture/engineering/security/reliability/data/performance/operations/product/governance, identify both risks and valuable capabilities, and separate incremental improvements from high-leverage or transformational opportunities without inventing ROI.

Most importantly: writing code is not proof that the task is complete.

**Prove it.**

## Prove It vs Prove It Lite

| | Prove It Lite | Prove It |
| --- | --- | --- |
| Install surface | One `SKILL.md` | Modular repository + skill entrypoint |
| Core engineering discipline | Yes | Yes |
| Conditional specialist guidance | Compressed inline | Dedicated profiles |
| Task templates | No | Yes |
| Model adapters | No | Yes |
| Prompt composer | No | Yes |
| Static eval harness | No | Yes |
| Universal generated prompt | No | Yes |
| Optional local MCP proof engine | No | Yes |
| Best for | Drop-in daily use | Development, customization, evaluation, auditable proof |

## Status

Current version: **0.4.0**. Lite intentionally stays small; new machinery belongs in full Prove It unless it materially improves the single-skill experience.

## License

MIT. See [`LICENSE`](LICENSE).
