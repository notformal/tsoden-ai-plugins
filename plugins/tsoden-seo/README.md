# Tsoden SEO & AEO

Ask about your Google rankings and your brand's visibility in answer engines
(ChatGPT, Claude, Gemini, Perplexity, Google AI Overviews) from your Tsoden
SERP Checker account: see what moved, compare competitors, read reports and
start checks.

## What it does

The plugin connects one remote MCP server, `https://serp.tsoden.ai/mcp`,
operated by Tsoden SERP Checker. You sign in on serp.tsoden.ai and approve
access (OAuth 2.1 with PKCE); the assistant receives an access token and never
your password.

- **Read**: projects, tracked keywords, ranking checks and history, top movers,
  ranking opportunities, search features, competitors, answer-engine visibility,
  brand mentions, tracked prompts, reputation overview, Search Console data,
  analytics reports, article drafts, account balance.
- **Write, after you confirm**: create a project; add keywords, competitors and
  tracked prompts; start a ranking check or an answer-engine check (these count
  toward your plan's limits); write, edit, review and publish article drafts.
- **Not available through the plugin**: deleting projects, creating or reading
  API keys, payment details.

Four skills use those tools: `rank-drop-diagnosis`,
`answer-engine-visibility-report`, `weekly-seo-brief` and
`content-scale-safety`. The server also offers the public website checks of the
AI Visibility Audit plugin.

## Requirements

A Tsoden SERP Checker account with a confirmed email. Access through assistants follows the account's plan.

## Example prompts

- Which of my keywords dropped since the last check, and what likely caused it?
- How often do ChatGPT and Perplexity mention my brand versus competitors?
- Give me this week's SEO brief for my main project.

## What it runs, sends and stores

The plugin runs no local code, hooks or scripts. Tool calls go to
`serp.tsoden.ai` with your access token and act with your permissions, on your
account's data only. The server logs each tool call like any API call. It does
not read the conversation, files or memory. Disconnect at any time under
Profile → Connected assistants on serp.tsoden.ai; access ends immediately.

## Privacy policy

https://serp.tsoden.ai/privacy-policy

## Troubleshooting and support

If sign-in does not finish, reconnect the server and approve access again. A
`quota_exhausted` answer means the plan's checks for the period are used up;
ask for the account balance to see what is left. Setup guide:
https://serp.tsoden.ai/integrations/ai-assistants. Support:
https://serp.tsoden.ai/support/chat or info@tsoden.ai.

License: MIT
