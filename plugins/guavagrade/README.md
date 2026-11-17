# GuavaGrade plugin

Connects your AI coding tool to [GuavaGrade](https://guavagrade.com), so it can read your website reports and fix the problems in your site's code.

The plugin adds two things:

- **The GuavaGrade MCP server** (`https://guavagrade.com/mcp`) with six read-only tools: `list_reports`, `get_report`, `get_section`, `list_issues`, `get_issue` and `get_free_check`. Your AI reads your grades, top fixes, accessibility issues with their failing elements (CSS selector and HTML), and findings for security, speed, search and the other areas.
- **The `guavagrade` skill**, which tells your AI how to work through a report: fix the top problems in order, trace failing elements back to your templates and components, explain fixes that belong in your hosting or CMS instead of your code, and remind you to check again after deploying.

## Setup

1. You need a GuavaGrade full report. Get one with a site pass at [guavagrade.com/buy](https://guavagrade.com/buy).
2. Install the plugin. In Claude Code:

   ```sh
   claude plugin marketplace add Awesome-Cause/guavagrade-ai
   claude plugin install guavagrade@guavagrade-ai
   ```

   In Codex, run `codex plugin marketplace add Awesome-Cause/guavagrade-ai` and install GuavaGrade from the Plugins directory.
3. Sign in with your GuavaGrade account when your AI tool asks, and click Allow.
4. Ask your AI to "fix the top problems in my GuavaGrade report".

The connection is read-only. Your AI can't start checks, change reports, buy anything or see payment details. Disconnect it any time from your GuavaGrade dashboard.

Automated checks find many problems, not all of them. Review your AI's changes, then run the check again on guavagrade.com to confirm each fix.

- Setup for every AI tool: [guavagrade.com/ai](https://guavagrade.com/ai)
- Privacy: [guavagrade.com/privacy](https://guavagrade.com/privacy)
- Terms: [guavagrade.com/terms](https://guavagrade.com/terms)
- Support: [hello@guavagrade.com](mailto:hello@guavagrade.com)
