> git branch, dirty state, and context window usage in your Claude Code footer

Status line configuration for [Claude Code](https://docs.anthropic.com/en/docs/claude-code) that displays your current directory, git branch, uncommitted changes, and context window usage at a glance.

```
────────────────────────────────────────────────────────────────────────────────
  cerebro | feat/END-6382-oauth-client-credentials | 3% ✓
  ⏵⏵ bypass permissions on (shift+tab to cycle) · PR #9201
```

## What it shows

| Segment | Description |
|---------|-------------|
| `cerebro` | Relative path from project root (basename when at root, `...`-prefixed when in a subdirectory) |
| `main ✗` | Current git branch, with ✗ if there are uncommitted changes |
| `12% ✓` | Context window usage with icon: ✓ (<50%), → (<60%), ◇ (<80%), ✕ (≥80%) |

## Setup

Copy `settings.json` into your Claude Code config:

```bash
# If you don't have a settings.json yet:
mkdir -p ~/.claude
cp settings.json ~/.claude/settings.json

# If you already have one, merge the statusLine key:
jq -s '.[0] * .[1]' ~/.claude/settings.json settings.json > /tmp/merged.json \
  && mv /tmp/merged.json ~/.claude/settings.json
```

Or paste the `statusLine` block directly into your existing `~/.claude/settings.json`.

Requires `jq` and `git` on your `PATH`.

---

[MIT](LICENSE) © 2026 Kerry Ivan Kurian
