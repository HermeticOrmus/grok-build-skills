---
name: calcinate
description: Surgical, intent-anchored bloat removal using parallel specialized detection subagents, strict JSON contracts, tiered judgment, and gated per-item execution with automatic verify + revert. The gold-standard pattern for safe, reversible, high-confidence "burn what doesn't serve" work. Adapted from the original Magnum Opus calcination operation for Grok's subagent model.
when-to-use: "calcinate", "burn the bloat", "surgical cleanup", "remove dead code", "verifiable surgery", "parallel detection with contracts", "safe refactor with revert gates"
allowed-tools: ["read_file", "grep", "list_dir", "run_terminal_command", "search_tool", "use_tool"]
---

# Calcinate — Verifiable Parallel Surgery (Grok Native)

> "That which does not serve the Work must burn."

This skill captures the highest-leverage engineering pattern from the original calcination operation: **declare explicit intent as a contract, dispatch specialized detection agents in parallel with strict output contracts, synthesize a tiered plan, then execute with per-item verification and automatic revert on failure**.

It is one of the richest portable intellectual capital pieces from the old system. The alchemical framing is kept lightly for continuity; the real value is the rigorous, observable, safe parallel work pattern that Grok's native subagents make even more powerful.

---

## Core Principles (Non-Negotiable)

1. **No intent = no burn.** You must have a clear, user-confirmed multi-layer intent before any detection or deletion.
2. **Detect only in parallel phase.** Subagents return structured findings only. No edits.
3. **Strict contracts.** Every finding has severity (1-5), intent_mismatch (0.0-1.0), risk_note, and evidence.
4. **Tiered judgment + gates.** Different risk levels require different levels of user approval.
5. **Verify on green, revert on red.** Per-item verification with automatic restore on failure. Three consecutive failures halts the run.
6. **Sacred ignore list.** Anything in `.calcinate/ignore` is never touched.
7. **Per-item commits** (or clear atomic changes) during the burn phase.
8. **No constructive suggestions** during detection. This skill only removes what doesn't serve the declared intent. Adding belongs to coagulation-style work.

---

## Phase 0 — Declare Intent (The Preservation Contract)

Before anything else, establish or refresh `.calcinate/INTENT.md` in the target directory.

The intent has three layers:

- **Business intent** (1-2 sentences): What does this software actually do for users? What problem does it solve?
- **Architectural intent** (3-5 bullets): Stack, key boundaries, runtime model, explicit non-goals.
- **Stylistic intent** (3-5 bullets): Language conventions, naming, composition rules, test style, forbidden patterns.

**Process**:
1. Scan for existing `.calcinate/INTENT.md`.
2. If present, show it and ask the user: Reuse / Refresh / Rebuild.
3. If building or refreshing, gather signals from README, package manifests, entry points, recent commits, CLAUDE.md / AGENTS.md, etc.
4. Propose a draft using the three-layer structure.
5. Walk the user through confirming/editing each layer (use `ask_user_question` style).
6. Write the file. Also create `.calcinate/ignore` (initially empty or with obvious sacred paths) and `.calcinate/verify` (the command or script that proves the project still works after changes — e.g. `npm test && npm run typecheck`).

This file is the source of truth. Any code that clearly serves the declared intent is protected, even if it looks ugly or "rot-like" to a generic linter.

---

## Phase 1 — Parallel Detection (Reveal)

Dispatch 4 specialized detection subagents in parallel using Grok's native subagent capabilities.

The four categories (run as `explore` type subagents or with very constrained capability modes):

1. **code-rot** — Dead exports, unreachable branches, swallow catches, commented-out blocks, duplicate-and-drift, god files, defensive internal code.
2. **structural-bloat** — Overly deep nesting, god classes/modules, unnecessary abstraction layers, duplicated module structures.
3. **dep-bloat** — Unused dependencies, dev deps that leaked into prod, multiple versions of the same thing, heavy deps used for tiny things.
4. **doc-test-rot** — Outdated docs, tests that only test the framework, low-value tests that would be better as types or examples.

**For each subagent, provide**:
- The full verbatim `INTENT.md`
- A focused hunt list (specific patterns to look for in this category)
- The target path
- The strict output contract (JSON array only, no prose)

Example JSON finding shape (every subagent must return this or `[]`):

```json
{
  "id": "unique-kebab-slug",
  "path": "relative/path/to/file.ts",
  "lines": "42-67",
  "category": "code-rot",
  "subcategory": "dead-export",
  "severity": 4,
  "intent_mismatch": 0.85,
  "proposed_action": "delete",
  "risk_note": "Exported only from index barrel; no direct consumers found",
  "evidence": "grep found zero non-test imports of 'DeadComponent'"
}
```

Run all four in one parallel step (Grok's subagent system excels at this).

Collect results, write to `.calcinate/runs/<timestamp>/findings.json`.

---

## Phase 2 — Judgment & Tiered Plan

- Deduplicate overlapping findings (same path + lines).
- Score and tier:

  **Tier 1** (autonomous on "approve all"): High confidence dead weight, low risk, high intent mismatch.
  **Tier 2** (log each): Clear bloat but slightly higher risk or lower mismatch.
  **Tier 3** (individual approval): Structural moves/extractions that need judgment.
  **Tier 4** (discuss only): High risk + high mismatch, or findings that suggest the intent itself needs updating.

- Produce `CALCINATION-PLAN.md` (both in the run folder and a top-level copy) with tiered sections, sorted by priority.
- Present a crisp summary to the user: counts per tier + top 5 per tier + clear approval commands (`approve all`, `approve tier 1`, `approve id1 id2`, `skip id`, `pin id`, `intent id`).

If `--reveal-only`, stop here. The plan is the deliverable.

---

## Phase 3 — Gated Burn (Execute with Safety)

- Require explicit user approval before any mutation.
- Prefer working on a fresh branch (`calcinate/<timestamp>`).
- For each approved item in order:
  1. Apply the minimal change (delete, inline, extract, etc.).
  2. Run the verify command from `.calcinate/verify`.
  3. **Green** → commit atomically with clear message.
  4. **Red** → automatic `git restore .` + clean, mark failed, increment consecutive-fail counter.
  5. 3 consecutive failures → hard halt and ask the user. Usually the intent or verify command is the problem, not the findings.

- Support mid-burn commands: `pin`, `skip`, `intent` (refine intent for that finding), etc.
- `--dry-run` mode for simulation.

---

## Phase 4 — Residue Report

After burn (or on demand), produce a crisp residue report:

- Outcome counts per tier (burned / failed / skipped / pinned / discussed)
- LOC removed / files deleted / deps pruned
- Full list of commits from the run
- Items deferred (lower confidence findings for next pass)
- Recommendation: if many Tier 4 items, suggest refreshing intent

---

## Why This Pattern Is Extremely Powerful in Grok

Grok's subagent system (typed `explore` agents, personas, capability modes, worktree isolation, `resume_from` chaining) is a natural fit for this style of work — often cleaner and more observable than the original implementation.

The combination of:
- Explicit multi-layer intent as contract
- Parallel specialized detection with strict JSON contracts
- Tiered risk judgment
- Per-item verify + automatic revert
- 3-strike safety halt

...produces dramatically safer, more reviewable, higher-confidence "surgery" than typical agentic cleanup.

This is one of the best patterns to internalize and reuse across many kinds of maintenance, refactoring, and codebase health work.

---

**Calcine to clarify. Then coagulate to build.**

See also the global doctrine in `~/.grok/AGENTS.md` (especially surgical changes, simplicity first, and goal-driven execution).