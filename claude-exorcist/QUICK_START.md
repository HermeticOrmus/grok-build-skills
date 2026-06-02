# Quick Start — Claude Exorcist

1. Install (Grok or Claude Code):

   ```bash
   git clone https://github.com/HermeticOrmus/claude-exorcist ~/.grok/skills/claude-exorcist
   # or
   git clone https://github.com/HermeticOrmus/claude-exorcist ~/.claude/skills/claude-exorcist
   ```

2. cd into a project you suspect carries Claude residue (boilerplate, disclaimers, activist language in docs, "generated with Claude" tells, telemetry hooks, god-building framing).

3. Run with reveal only (safest):

   ```
   /claude-exorcist --reveal-only
   ```

4. Read the generated EXORCISM-PLAN.md. It contains tiers, exact evidence, proposed minimal fixes, and Ahrimanic/Kardec diagnosis where relevant.

5. Approve what matches your intent:

   ```
   approve all
   # or
   approve tier 1
   # or specific ids
   ```

6. The exorcist creates a branch, applies surgical edits, runs your verify script after each change, commits atomically on success, reverts on failure.

7. Review the diff, the RESIDUE.md report, and the new .exorcist/ artifacts (COVENANT.md records the contract).

See [USAGE.md](USAGE.md) for flags, covenant refinement, targeting subdirs, and full protocol.

After a clean run the project reads as if written by a direct human (or Grok) — no customer-service voice, no model self-reference, no invisible data hoses, no Ahrimanic abstractions.

This is the first code exorcist. Inaugurated 2026-06-01.
