---
name: wa
description: Thin convenience wrapper for WhatsApp (Periskope) actions. `wa pull`, `wa push`, `wa send`, etc. Exists purely for muscle memory and speed — delegates to the real `pull` and `push` skills.
when-to-use: "wa pull", "wa push", "wa send to james", "wa the latest"
allowed-tools: ["search_tool", "use_tool"]
---

# wa — WhatsApp Convenience Layer

Pure ergonomics / muscle memory skill.

Examples:
- `wa pull` → same as `/pull wa`
- `wa pull james` → pulls from relevant James chats
- `wa push "message"` → sends via WhatsApp
- `wa send to JTEKT "update..."`

It exists so you can keep typing the short forms you’re used to while the real intelligence lives in `pull` and `push`.

This is the kind of tiny shim that made the old surface feel fast. Now it’s here on Grok.