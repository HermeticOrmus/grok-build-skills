---
name: prime
description: Universal context router and prime mover. Detects Raven vs Personal/Hermetic vs S50/AUros vs Alqvimia vs neutral context, loads the correct priors and tone, then routes to the right specialized skill or workflow. The single best entry point for most serious work. Successor to mprime + r-prime + o-prime.
when-to-use: "prime", "route this", "what lane is this", "Raven or personal", "context detection", "mprime", "r-prime", "o-prime"
allowed-tools: ["read_file", "grep", "list_dir", "run_terminal_command", "search_tool", "use_tool"]
---

# Prime — Universal Context Router

This is the single highest-leverage entry point skill in the Grok-native Reality OS. It does what `mprime` + `r-prime` + `o-prime` did in the old system, but cleaner and more observable.

**Core contract**: Before doing any serious work, call this (or let it be auto-detected) so the correct priors, tone, and routing are loaded.

---

## Detection Order (Deterministic)

Check in this exact order. Stop at the first strong match.

### 1. Explicit Flags (highest priority)
- `--raven` or `--ormus` or `--s50` or `--alqvimia` or `--neutral` in the prompt → force that lane.
- `--explain` → describe the routing decision and loaded priors, then stop.

### 2. Explicit Project / Path Signals (cwd or task text)
**Raven**:
- `raven-cargo`, `raveneye`, `corvin`, `corvin-server`, `mcleod`, `JTEKT`, `command-center`, `4pl-portal`, `siemens.raven-cargo`, `lane.raven-cargo`, `outreach.raven-cargo`, etc.
- Paths under `~/projects/03-CLIENT/raven-cargo`, `~/tools/raven-*`, `~/projects/raven-*`
- SSH hostname is `corvin`, `corvin-server`, `corvin-tools`

**Personal / Hermetic / Alqvimia / S50**:
- `alqvimia`, `athanor`, `hermetic`, `tinctvra`, `ormus.solutions`, `auros`, `s50`, `second-50`, `dbodartm`
- Paths under `~/projects/athanor-*`, `~/projects/alqvimia-*`, `~/projects/ormus-*`, `~/projects/02-PERSONAL`, `~/.hermetic`
- `s50-platform`, `s50-website`, `auros-lromer`

### 3. Vocabulary & Stakeholder Signals
**Strong Raven indicators**:
- "James", "Diego", "Sam", "Hubert", "Linear", "ticket", "PR", "deploy", "Talon", "McLeod", "TMS", "JTEKT", "Siemens", "Auth0", "CF Access"

**Strong Personal / Hermetic indicators**:
- "alchemical", "hermetic", "Gold Hat", "distillation", "consciousness", "Sun/Moon/Mercury/Venus", "Ormus", "Alqvimia", "Athanor"

### 4. Time + Soft Tiebreaker (only when truly ambiguous)
- Weekdays 09:00–18:00 America/Panama time + no strong personal signals → lean Raven.
- Outside those hours or strong personal signals → lean Personal/Hermetic.

Never let the soft tiebreaker override a clear signal from steps 1-3.

---

## Routing + Prior Loading

Once the lane is decided, **announce the decision clearly** in one line, then load the appropriate priors and execute.

### Raven Lane
- Announce: `prime → Raven · reason: <one short phrase> · loading raven-topology + PM priors`
- Load (via skill invocation):
  - `raven-topology` (fleet map, 4-check contract, McLeod patterns, operational guardrails)
  - Any additional Raven-specific priors the task requires (Linear, specific customer, etc.)
- Tone: Professional PM / operator. Precise, direct, no fluff. Always surface the 4-check mindset on anything that touches production.
- Then route to the appropriate station skill or workflow:
  - Intake signals (WhatsApp, voice, "what did James say") → intake flow
  - Spec / scope language → spec flow
  - Plan / implementation plan → plan flow
  - Ship / execute / Talon / deploy → execute flow + 4-check verify gate
  - Verify / "is it live" → 4-check verify
  - Close / update / brief → close flow (Linear + WhatsApp push)
  - Query ("where does X run", auth state, portfolio) → use raven-topology directly

### Personal / Hermetic / Alqvimia / S50 Lane
- Announce: `prime → Personal · reason: <phrase> · loading Gold Hat + Vibe Engineer priors`
- Load doctrine from `~/.grok/AGENTS.md` (already global, but reinforce).
- Tone: Teaching + empowerment. Explain WHY. Name patterns. Offer the manual path when automation is used.
- Route to the appropriate personal flow (o-flow equivalents, client-specific plan skills, Alqvimia workflows, S50 brand work, etc.).

### Neutral / Meta Lane
- Announce: `prime → Neutral/meta · reason: no strong lane signals`
- Fall back to general high-quality meta-prompting with the core doctrine still active.

---

## Output Contract

Every time Prime runs, the final output (or a clear intermediate message) must contain:

1. The routing decision in one crisp line.
2. Which priors were loaded.
3. The next concrete step or the result of the routed workflow.
4. (When relevant) explicit reference to the 4-check verify or Vibe Engineer triggers.

Example good output:
```
prime → Raven · reason: cwd + "JTEKT" + Linear mention · loaded raven-topology + 4-check contract
Routing to r-execute for the JTEKT dashboard change. 4-check will be required on completion.
```

---

## Implementation Notes for This Skill

- This skill is intentionally **not** a thin router. It is the place where lane-specific priors and tone are injected so that downstream work inherits the correct Reality OS context.
- It is idempotent: same inputs + same cwd should produce the same routing decision.
- When in doubt on a real task, call this skill first (or let auto-detection trigger it). It is cheap and prevents the "wrong priors" class of errors that used to require mprime/r-prime.
- Future evolution: specialized sub-skills for `raven-prime` (full station + lane detection) and personal equivalents can be extracted from this as they mature.

This is the new canonical entry point. Use it.

**Build what elevates. Reject what degrades.**