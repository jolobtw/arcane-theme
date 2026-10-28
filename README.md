# 🔮 Arcane Theme

**Unified Master Design System & Live Auto-Sync Tokens for Terminal UI Apps.**

Arcane Theme provides a consistent, Obsidian-grade TrueColor terminal aesthetic across multiple applications and languages (such as **Tome** in Go and **JIRA TUI** in Python / Textual).

---

## ⚡ Live Auto-Sync Architecture

You never need to recompile or rewrite app code just to tweak styling:
1. **Single Source of Truth**: Edit [`theme.json`](./theme.json) in this repository.
2. **Local Cache**: Apps cache the active theme at `~/.config/arcane/theme.json` (on both macOS and Windows).
3. **Background Auto-Sync**: On launch, apps read the local cache instantly (< 1ms) and spawn a silent, non-blocking background fetch from GitHub. When you push new colors or symbols to this repo, your apps automatically inherit them on their next launch!

---

## 🎨 Design Tokens

- **Canvas Background**: `#13141C` (Deep Arcane Slate)
- **Panel Background**: `#181A24` (Midnight Slate)
- **Badge & Selection**: `#262938` (Calm Slate)
- **Border Active**: `#FF7A00` (Flame Orange)
- **Border Muted**: `#2E3244` (Slate Gray)
- **Gradient Horizon**: `#FF4500` → `#FFD166` (Flame to Gold)

---

## 🐍 Using with Python / Textual (e.g. JIRA TUI)

Copy `python/arcane_theme.py` into your project (or point Claude to this repository).

```python
from arcane_theme import load_theme, format_rich_header

# 1. Load active tokens (with automatic GitHub sync in background)
theme = load_theme()

# 2. Render standard 2-row header matching Tome:
header_text = format_rich_header(
    app_title="JIRA",
    tagline="Terminal Ticket Navigator",
    badges=["󰌹 Sprint 42", "󰈙 14 Open"],
    width=terminal_width,
)
```

---

## 🐹 Using with Go / Lipgloss (e.g. Tome)

Tome natively implements the Live Auto-Sync client. It reads `~/.config/arcane/theme.json` and syncs with `github.com/jolobtw/arcane-theme`.
