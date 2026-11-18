# GuavaGrade for AI tools

Connect your AI assistant to [GuavaGrade](https://guavagrade.com). It reads your website reports and fixes the problems in your site's code: accessibility issues with their failing elements, security headers, speed, search, forms and more. Then you run the check again and it reads the new results.

Every tool connects to the same MCP server:

```text
https://guavagrade.com/mcp
```

You sign in with your GuavaGrade account and click Allow. **AI connections come with a GuavaGrade full report**; get one with a site pass at [guavagrade.com/buy](https://guavagrade.com/buy). The connection is read-only: your AI can't start checks, change reports, buy anything or see payment details. Disconnect it any time from your dashboard.

This repository holds the plugin and skill for each tool. Step-by-step setup with copy buttons is at [guavagrade.com/ai](https://guavagrade.com/ai).

## Claude (web, desktop and Cowork)

1. Open **Customize > Connectors**. On Team and Enterprise plans, an owner opens **Organization settings > Connectors**.
2. Choose **Add custom connector**. Name it GuavaGrade and paste `https://guavagrade.com/mcp`.
3. Click **Add**, then **Connect**. Sign in and click Allow.

Free Claude plans allow one custom connector.

## Claude Code

Add the server, then run `/mcp`, pick `guavagrade` and sign in:

```sh
claude mcp add --transport http --scope user guavagrade https://guavagrade.com/mcp
```

Or install the plugin, which adds the server and the `guavagrade` fix skill:

```sh
claude plugin marketplace add Awesome-Cause/guavagrade-ai
claude plugin install guavagrade@guavagrade-ai
```

## ChatGPT

1. Open [chatgpt.com/plugins](https://chatgpt.com/plugins), click **+**, then **Add custom MCP server**.
2. Name it GuavaGrade, paste `https://guavagrade.com/mcp` and choose OAuth.
3. Create and install it, sign in, then type `@GuavaGrade` in a chat.

Available on ChatGPT plans that allow custom MCP servers. On Business and Enterprise plans, an admin may need to add it.

## Codex (CLI, IDE extension and desktop)

```sh
codex mcp add guavagrade --url https://guavagrade.com/mcp
codex mcp login guavagrade
```

Or in `~/.codex/config.toml`, then run `codex mcp login guavagrade`:

```toml
[mcp_servers.guavagrade]
url = "https://guavagrade.com/mcp"
```

Or install the plugin, which adds the server and the `guavagrade` fix skill. It also appears in the ChatGPT desktop app's Plugins directory:

```sh
codex plugin marketplace add Awesome-Cause/guavagrade-ai
codex plugin add guavagrade@guavagrade-ai
codex mcp login guavagrade
```

## Amp

```sh
amp mcp add guavagrade https://guavagrade.com/mcp
```

Amp opens the sign-in page the next time it starts. Or install the skill, which loads the server only when you ask Amp to fix findings:

```sh
amp skill add Awesome-Cause/guavagrade-ai/skills/guavagrade
```

In orbs, where a browser sign-in can't open, add it as a remote server instead and sign in from your own machine:

```sh
amp mcp remote --personal add GuavaGrade https://guavagrade.com/mcp --auth oauth
amp mcp remote --personal login GuavaGrade
```

## Command Code

```sh
cmd mcp add --transport http --scope user guavagrade https://guavagrade.com/mcp
```

Command Code starts the sign-in the first time it connects, or run `cmd mcp auth guavagrade`. Add the fix skill too:

```sh
cmd skills add Awesome-Cause/guavagrade-ai/skills/guavagrade
```

## OpenCode

```sh
opencode mcp add guavagrade --global --url https://guavagrade.com/mcp
opencode mcp auth guavagrade
```

Or in `opencode.jsonc`:

```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "servers": {
      "guavagrade": { "type": "remote", "url": "https://guavagrade.com/mcp" }
    }
  }
}
```

To add the fix skill, copy `skills/guavagrade` into `~/.config/opencode/skills/`, or into `.opencode/skills/` or `.agents/skills/` in your project.

## Cursor

Click **Add to Cursor** at [guavagrade.com/ai](https://guavagrade.com/ai). Cursor opens and asks to install the server; sign in when it asks.

Or add it to `~/.cursor/mcp.json`:

```json
{ "mcpServers": { "guavagrade": { "url": "https://guavagrade.com/mcp" } } }
```

This repository is also a Cursor plugin marketplace. Teams can import it in the Cursor dashboard under Plugins & MCPs, which adds the server and the `guavagrade` fix skill.

## VS Code and other MCP clients

Any app that supports remote MCP servers with OAuth sign-in connects with the same address.

VS Code (`.vscode/mcp.json`):

```json
{ "servers": { "guavagrade": { "type": "http", "url": "https://guavagrade.com/mcp" } } }
```

## Tools

| Tool | What it reads |
| --- | --- |
| `list_reports` | Your full reports and free checks, with status, grade and ID |
| `get_report` | Overall and area grades, summary, pages checked and top fixes in priority order |
| `get_section` | One area's findings, evidence and recommended solutions |
| `list_issues` | Accessibility issues with impact and the pages they are on |
| `get_issue` | One accessibility issue's pages and failing elements (CSS selector and HTML) |
| `get_free_check` | A free check's grades and findings |

Every tool is read-only. Automated checks find many problems, not all of them, and an AI can make mistakes. Review its changes, then run the check again on guavagrade.com to confirm each fix.

## What's in this repository

| Path | For |
| --- | --- |
| `.claude-plugin/marketplace.json` | Claude Code plugin marketplace (also read by the ChatGPT desktop app) |
| `.agents/plugins/marketplace.json` | Codex and ChatGPT desktop plugin marketplace |
| `.cursor-plugin/marketplace.json` | Cursor plugin marketplace |
| `plugins/guavagrade/` | The plugin: manifests for Claude, OpenAI and Cursor, the MCP server, the skill and the icon |
| `skills/guavagrade/` | The fix skill on its own for Amp, Command Code, OpenCode and other Agent Skills tools. Its `mcpServers` frontmatter gives Amp the server; other tools ignore it |

`skills/guavagrade/SKILL.md` and `plugins/guavagrade/skills/guavagrade/SKILL.md` must stay identical; CI checks this.

## Support

- Privacy: [guavagrade.com/privacy](https://guavagrade.com/privacy)
- Terms: [guavagrade.com/terms](https://guavagrade.com/terms)
- Email: [hello@guavagrade.com](mailto:hello@guavagrade.com)

MIT licensed.
