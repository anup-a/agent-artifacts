# byagent skill

Skill for Claude Code, Grok, Codex, and friends: design a page and publish it to [byagent.dev](https://byagent.dev).

The deliverable is always the published URL, `https://byagent.dev/a/<id>/`. The agent publishes finished pages on its own and hands back the link. Internal work goes out as `--private`.

## Install

Any agent, via [skills.sh](https://skills.sh):

```bash
npx skills add anup-a/agent-artifacts
```

By hand: copy [`skills/byagent/`](skills/byagent) into your agent's skills folder, for example `~/.claude/skills/byagent` or `~/.grok/skills/byagent`.

Then `/byagent`, or just write a report. The skill fires on its own.

## CLI

The CLI is the npm package [`byagent`](https://www.npmjs.com/package/byagent). (`npx artifacts` is someone else's package.)

```bash
npm install -g byagent
echo "$KEY" | byagent login --api https://app.byagent.dev
byagent publish ./notes.md --project "Personal" --tag notes --json
```

Keys: https://app.byagent.dev/app/keys

## Publish nudges

Agents forget to publish. A PostToolUse hook reminds them:

```bash
byagent hooks install claude     # ~/.claude/settings.json
byagent hooks install codex      # ~/.codex/hooks.json, then trust it in /hooks
```

When the agent writes a `.html` or `.md` page, the hook adds one line to its context suggesting `byagent publish`, or a republish if that directory is already published. It never publishes on its own. Each file gets one nudge per session, five per session at most, and code trees, repo docs and agent config are skipped. `BYAGENT_NUDGE=0` silences it; `byagent hooks uninstall claude` removes it.
