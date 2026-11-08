# Little Monk plugin for Claude Code

Plan your day and keep notes in [Little Monk](https://littlemonk.app) from Claude Code. This repository is a Claude Code plugin marketplace with one plugin, `little-monk`. It adds:

- the Little Monk MCP server, `https://app.littlemonk.app/mcp` (remote, Streamable HTTP, OAuth sign-in, no API key);
- a skill that teaches Claude the planner's words and rules: Tasks, deep work Sessions, Unscheduled, Captures and Ideas, and that only you mark a task done.

Using Little Monk with an assistant needs Little Monk Pro.

## Install

In Claude Code:

```text
/plugin marketplace add sebinthomas92/little-monk-mcp
/plugin install little-monk@little-monk
```

Or from a terminal:

```bash
claude plugin marketplace add sebinthomas92/little-monk-mcp
claude plugin install little-monk@little-monk
```

Then sign in once:

1. Start Claude Code and type `/mcp`.
2. Choose `plugin:little-monk:little-monk` and **Authenticate**.
3. Your browser opens. Sign in with your Little Monk email and password and choose **Allow**.

Try: "What's on my plan today?", "Add a task to call the bank tomorrow at 10", "Plan 90 minutes of deep work on the report this afternoon".

## Update or remove

```bash
claude plugin marketplace update little-monk
claude plugin uninstall little-monk@little-monk
```

To disconnect Claude Code from your library, open [Account](https://app.littlemonk.app/account) in the Little Monk web app.

## Without the plugin

The server alone works too (no skill):

```bash
claude mcp add --transport http --scope user little-monk https://app.littlemonk.app/mcp
```

## Links

- Setup guide: https://app.littlemonk.app/docs/connect/claude-code
- Privacy policy: https://littlemonk.app/privacy
- Support: support@littlemonk.app

## Layout

```text
.claude-plugin/marketplace.json                 marketplace "little-monk"
plugins/little-monk/.claude-plugin/plugin.json  plugin manifest
plugins/little-monk/.mcp.json                   MCP server (https://app.littlemonk.app/mcp)
plugins/little-monk/skills/little-monk/SKILL.md planner vocabulary and rules
```

The source of truth is `distribution/claude-code-plugin/` in the private `little-monk-web` repository; this public repository is a copy of that folder. Check both with `claude plugin validate .` and `claude plugin validate plugins/little-monk`.

## MCP Registry

`server.json` lists the server in the official MCP Registry as `io.github.sebinthomas92/little-monk` (remote only, no package). `.github/workflows/publish-mcp.yml` publishes it with GitHub OIDC on a `v*` tag or when run by hand. Bump `version` in `server.json` before each publish.
