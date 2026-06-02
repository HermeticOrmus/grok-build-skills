---
name: r-execute
description: Thin high-frequency shim for Raven execution work. Loads raven-prime + topology, then drives the execute + 4-check phase. Exists for muscle memory. Delegates to the real routers and skills underneath.
when-to-use: "r-execute", "execute the raven change", "ship this raven thing"
allowed-tools: ["search_tool", "use_tool"]
---

# r-execute — Raven Execution Shim

Pure ergonomics.

Calling this is equivalent to:
- Running `raven-prime` (or already being in Raven context)
- Routing to the execute station
- Ensuring `raven-topology` + 4-check contract are active
- Driving the actual implementation + verification work

Use it exactly like the old `/r-execute` command for daily Raven execution flow.

The real power lives in `raven-prime` + `raven-topology` + your other skills. This is just the fast muscle-memory entry point.