# EXORCISM-PLAN

**Project**: <target path>
**Covenant date**: <from .exorcist/COVENANT.md>
**Run timestamp**: <YYYY-MM-DD-HHMM>
**Total findings**: <N>
**Tiers**: 1: <n1> | 2: <n2> | 3: <n3> | 4: <n4>

## Summary by Category
- theater: <count>
- ideology: <count>
- fingerprint: <count>
- malice: <count>

## Tier 1 — Autonomous (high confidence, low risk, safe to burn on "approve all")
These are blatant, low-value residue with minimal chance of affecting functionality.

<For each>
- **id**: <id>
- **path:span**: <path>:<span>
- **category/sub**: <cat>/<sub>
- **evidence**: "<short quote>"
- **action**: <proposed>
- **rationale**: <one line why safe>
</For each>

## Tier 2 — Log Each (solid residue, execute but record)
<same format>

## Tier 3 — Individual Approval (rewrites, user-facing, higher risk)
<same format>

## Tier 4 — Discuss Only (high risk or ambiguous; do not burn without conversation)
<same format>

## Commands
- `approve all` — burn Tier 1 + Tier 2 autonomously, ask per Tier 3
- `approve tier 1` — only Tier 1
- `approve tier 2` — only Tier 2
- `approve <id> <id> ...` — specific findings (can mix tiers)
- `skip <id>` — defer this one
- `pin <id>` — add path/glob to .exorcist/ignore and skip
- `covenant <id>` — pause and refine covenant using this finding as seed
- `reveal-only` was used if you are reading a plan without burn

## Notes
- All burns will happen on a branch (unless --no-branch).
- Every approved item gets its own commit after verify passes.
- 3 consecutive verify failures aborts the run.
- Findings that overlap (same span) have already been deduplicated; the strictest action wins.
- Every finding and the overall plan should be legible through the Ahrimanic/Kardec lens in `references/ahriman-kardec-training.md`.

**This plan is the contract. Do not improvise beyond approved ids.**