# Troubleshooting

## Subagents fail to return valid JSON or produce prose instead of array

The subagent prompts in the skill explicitly demand "JSON array only" and reference `references/ahriman-kardec-training.md`. 

- Re-read the COVENANT.md into the subagent context.
- Use `spawn_subagent` with type "explore" (read-only).
- If the model drifts, the `--reveal-only` plan will be incomplete — run again or manually curate the EXORCISM-PLAN.md before approving.

## Verify command fails after a burn (or no .exorcist/verify)

During Phase 0 the skill asks for or discovers your build/test command (e.g. `npm run build && npm test`, `pytest && mypy --strict`).

- Create or edit `.exorcist/verify` (make it executable) with the exact one-liner or script that must pass for the project to be considered healthy.
- The exorcist runs it after *every* search_replace and reverts on non-zero.
- For projects without tests, a simple `echo "verify: structure only" && ls -l src/` or similar can stand in, but prefer real typecheck/build.

## "No intent/covenant = no exorcism" or Phase 0 aborts

The skill refuses to hunt without a declared functional intent + residue ban.

- Let it write `.exorcist/COVENANT.md` (it seeds from README, package.json, existing AGENTS.md/CLAUDE.md).
- Edit the covenant if the auto-detected intent is wrong, then re-invoke with `/claude-exorcist` (or the --burn path after editing).
- Sacred: never bypass.

## Git branch or commit issues during exorcism

The skill prefers a fresh `exorcist/<timestamp>` branch and atomic per-finding commits with OCS messages.

- If you are not on a clean working tree, stash or commit first.
- 3 consecutive verify failures on the same run will halt and leave the branch for manual inspection + `git restore .`
- You can always `git checkout main && git branch -D exorcist/xxx` to abort.

## Residue that "should" be there (user wants the theater)

User is sovereign.

- During approval or mid-run: `pin <id>` adds the finding to `.exorcist/ignore` for this project.
- Or edit `.exorcist/ignore` directly with globs or file:span before approving.
- The covenant can be refined with `covenant` command for the current run.

## SKILL.md or references changes not taking effect

If you edited the skill itself:

- For the active install: `cd ~/.grok/skills/claude-exorcist && git pull` (or re-clone).
- Restart the session host (Grok/Claude Code) so the skill registry reloads the SKILL.md.
- The public repo at HermeticOrmus/claude-exorcist is the source of truth.

## Ahrimanic / god-building language that the user *intentionally* wrote

Pin it. The exorcist only removes what violates the covenant for that project. Intentional branding, historical quotes, or domain-specific language that the owner wants to keep is left alone.

See `references/examples.md` and `references/ahriman-kardec-training.md` for before/after patterns and the diagnostic lens.

## The plan looks empty or missed obvious residue

Run with `--reveal-only` again after refining the covenant (narrower or broader ban list).

Large monorepos: the ignore list + covenant scope protect vendor/, node_modules/, generated/, third-party text.

For very large targets, consider running on a subdirectory first.

## Still stuck

- Read the full protocol in `SKILL.md` (Phases 0-4 + sacred rules).
- The EXORCISM-PLAN.md and run dir under `.exorcist/runs/` contain the exact findings and rationale.
- Re-run the skill with more explicit user guidance in the initial prompt ("only docs and comments, no code changes").

This tool is deliberately strict. The goal is clean signal, not speed.
