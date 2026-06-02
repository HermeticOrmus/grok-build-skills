<p align="center">
  <img src="https://ormus.solutions/mascot/pixellab_liquid_to_flame.gif" alt="Grok Code Skills" width="128" style="image-rendering: pixelated;" />
</p>

<h1 align="center">Grok Code Skills</h1>

<p align="center">
  <em>Grok-native skills, prompts, and workflows adapted from Claude Code skills for xAI Grok — direct, truth-seeking, maximally helpful.</em>
</p>

<p align="center">
  <a href="https://github.com/HermeticOrmus/grok-code-skills/stargazers"><img src="https://img.shields.io/github/stars/HermeticOrmus/grok-code-skills?style=flat-square&color=aa8142" alt="Stars" /></a>
  <a href="https://github.com/HermeticOrmus/grok-code-skills/blob/main/LICENSE"><img src="https://img.shields.io/github/license/HermeticOrmus/grok-code-skills?style=flat-square&color=aa8142" alt="License" /></a>
  <a href="https://github.com/HermeticOrmus/grok-code-skills/commits"><img src="https://img.shields.io/github/last-commit/HermeticOrmus/grok-code-skills?style=flat-square&color=aa8142" alt="Last Commit" /></a>
  <img src="https://img.shields.io/badge/Grok_Skills-aa8142?style=flat-square" alt="Grok Skills" />
  <img src="https://img.shields.io/badge/Grok-aa8142?style=flat-square" alt="Grok" />
</p>

---

> Reusable skills and frameworks for Grok Build — distilled from real AI-assisted development sessions and the Reality OS. Battle-tested on the move from Claude to Grok.

**The on-ramp for users leaving Claude Code**: Start with [claude-exorcist](https://github.com/HermeticOrmus/claude-exorcist) + the [claude-to-grok](https://github.com/HermeticOrmus/claude-to-grok) hub, then install these Grok-native tools for continuity, power, and clean workflows.

## Skills

| Skill | What It Does | Origin |
|-------|-------------|--------|
| [calcinate](./calcinate/) | Burn project bloat to reveal essence — intent-anchored, parallel detection, tiered plan, gated reversible burns with verify | General bloat removal (companion to claude-exorcist) |
| [claude-exorcist](./claude-exorcist/) | Ultimate Grok-driven exorcism for projects previously built by Claude. Removes AI theater, ideological residue, fingerprints, and model-serving traces. Trained on Steiner (Ahriman) + Kardec. | First code exorcist (2026-06-01 on ormus.solutions) |
| [prime](./prime/) | The single highest-leverage entry point skill. Sniffs context and routes to the right specialist (meta, o-flow, r-prime, etc.). | Daily meta-orchestration |
| [distill](./distill/) | The primary growth mechanism. Turn lived session experience into durable, versioned, shareable intelligence (skills, agents, memory, docs). | Learning ritual |
| [create-skill](./create-skill/) | Interactively create a new Grok skill (SKILL.md + optional scripts/references). | Skill authoring |
| [meta-build](./meta-build/) | The high-discipline way to build things. Full orchestration for complex features. | Ambitious implementation |
| [ship](./ship/) | The production-grade shipping skill. GitHub + deploy + social in one flow. | Publishing workflow |
| [pull / push](./pull/) | Fluid high-frequency updates via WhatsApp (Periskope) and other channels. | Communication |
| [best-of-n](./best-of-n/) | Implement a task N ways in parallel (isolated worktrees), evaluate, and apply the winner. | Quality via exploration |
| [check-work](./check-work/) | Verification subagent. Reviews diffs, runs builds/tests, evaluates correctness. | Self-verification |
| [help](./help/) | Grok documentation and configuration help — setup, MCP, skills, shortcuts, etc. | Onboarding & reference |

(Additional skills in the full ~/.grok/skills/ surface: wa, xlsx, docx, pptx, mars, raven-*, etc. See the skills dir or `~/.grok/docs/user-guide/08-skills.md`.)

## Spotlight: standalone / graduated repos

Key tools that have richer docs and dedicated public homes. Install directly:

| Repo | What it does |
|------|-------------|
| [claude-exorcist](https://github.com/HermeticOrmus/claude-exorcist) | Remove Claude residue from projects (the essential first step when migrating) |
| [ormus-handoff](https://github.com/HermeticOrmus/ormus-handoff) / [ormus-pickup](https://github.com/HermeticOrmus/ormus-pickup) / [ormus-absorb](https://github.com/HermeticOrmus/ormus-absorb) / [ormus-explore](https://github.com/HermeticOrmus/ormus-explore) | The ormus session lifecycle — context that survives machine switches, context clears, and model changes |
| (calcinate, prime, etc. — see above or graduate more) |

These form the foundation for serious work on Grok.

## Migration from Claude Code

1. **Clean house**: Run the [claude-exorcist](https://github.com/HermeticOrmus/claude-exorcist) on your old projects (and the skills themselves if needed).
2. **Install continuity**: ormus-handoff/pickup/absorb/explore so your workflows don't break.
3. **Adopt Grok-native tools**: Clone this repo or individual skills into `~/.grok/skills/`.
4. **Learn the surface**: Read `~/.grok/docs/user-guide/` (getting-started, skills, subagents, project-rules/AGENTS.md, etc.).
5. **Build your own**: Use `create-skill` + `prime` + `distill` to extend.

Grok is more direct, tool-capable, and less inclined to theater or paternalism. The skills here are adapted (or written natively) for that voice.

## How to Use

These are Grok skills (and compatible with the broader surface).

1. `git clone https://github.com/HermeticOrmus/grok-code-skills ~/.grok/skills/grok-code-skills` (or clone individual skill dirs directly into `~/.grok/skills/<name>`).
2. In a Grok session, use the triggers or `/<skill-name>`.
3. Or read the SKILL.md and apply manually.

Each is self-contained.

## Structure

```
grok-code-skills/
  README.md
  <skill-name>/
    SKILL.md
    references/   # templates, training, examples
```

See also the official `~/.grok/docs/user-guide/08-skills.md`.

## Philosophy

Gold Hat first: empower, teach, respect autonomy, long-term, root causes.

Grok voice: direct, no hedging, truth-seeking, high signal. The Vibe Engineer + Karpathy discipline + Reality OS (AGENTS.md) apply.

Skills are extracted from real work and generalized.

## Contributing

See the parent claude-code-skills process or open issues/PRs here. Real patterns from Grok sessions preferred. Preserve the directness.

## License

MIT © 2026 Diego Bodart — see LICENSE. Built under the Gold Hat principle.

Part of the Grok-native Reality OS. Use claude-exorcist to arrive clean, then these tools to build powerfully.
