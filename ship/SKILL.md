---
name: ship
description: Full multi-destination shipping pipeline. Takes completed work and ships it to GitHub (or appropriate remote), Distillations, ormus.solutions journal, and social (X/LinkedIn) with proper voice, formatting, and notifications. Direct Grok-native replacement for the old ship skill.
when-to-use: "ship", "ship this", "release", "publish", "ship to github + site"
allowed-tools: ["read_file", "grep", "list_dir", "run_terminal_command", "search_tool", "use_tool"]
---

# Ship — Multi-Destination Release (Grok Native)

This is the production-grade shipping skill. It replicates the old `ship` workflow but built on Grok primitives.

It handles the full pipeline:
- Code / artifact finalization
- GitHub (or correct remote) push + tagging where appropriate
- Translation / adaptation for public Distillations / journal
- ormus.solutions journal post
- Social posting (X + LinkedIn) in the correct voice
- WhatsApp notification to the right groups/people

---

## Usage

```bash
/ship                    # Ships the current work (will ask for confirmation on scope)
/ship the S50 hub refactor
/ship james-prototypes update
```

The skill will:
1. Confirm what is being shipped
2. Handle the technical push
3. Generate the right public-facing versions (stripping internal context)
4. Post to the journal + social with your established voice
5. Notify via WhatsApp where relevant

---

## Voice & Quality Rules (Hard)

- No marketing fluff
- Direct, builder voice
- Proper Gold Hat / co-authored-by where it applies
- Internal details stripped for public surfaces
- Links and references cleaned

This skill enforces the same standards the old one did.

---

**Ship is now live on Grok.**

Use it the same way. It will feel familiar but with better underlying subagent orchestration for the synthesis and adaptation steps.