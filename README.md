# agent-artifacts

Skill for Claude Code, Grok, Codex, and friends: design a page and publish it to [byagent.dev](https://byagent.dev).

The deliverable is always `https://byagent.dev/a/<id>/`. If there is even a 1% chance the page gets opened again, publish it.

## Install

Claude Code:

```bash
git clone https://github.com/anup-a/agent-artifacts ~/.claude/skills/agent-artifacts
```

Grok:

```bash
git clone https://github.com/anup-a/agent-artifacts ~/.grok/skills/agent-artifacts
```

Then `/agent-artifacts`, or just write a report — the skill fires on its own.

## CLI

Not on npm (`npx artifacts` is someone else's package). Default checkout:

```bash
art() { node "$HOME/orca/projects/artifacts/cli/bin/artifacts.js" "$@"; }
```

Keys: https://app.byagent.dev/app/keys
