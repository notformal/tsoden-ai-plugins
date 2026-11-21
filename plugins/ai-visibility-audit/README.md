# Tsoden AI Visibility Audit

Live checks of how ready a public website is to be found and quoted by answer
engines (ChatGPT, Claude, Gemini, Perplexity, Google AI Overviews), with skills
that turn the results into fixes. No account or sign-in is needed.

## What it does

The plugin connects one remote MCP server, `https://serp.tsoden.ai/mcp/free`,
operated by Tsoden SERP Checker. Its tools are read-only:

| Tool | What it returns |
|---|---|
| `audit_ai_readiness` | An AI-search readiness score and an SEO hygiene score with pass/warn/fail checks |
| `check_ai_crawler_access` | Which AI crawlers robots.txt allows or blocks, and whether llms.txt exists and is valid |
| `check_schema_readiness` | Which entity facts the page's JSON-LD gives an answer engine, and which are missing |
| `find_prompt_opportunities` | Questions people ask answer engines where the brand could be recommended |
| `get_ai_readiness_benchmark` | Aggregate figures from sites checked with these tools |
| `get_started` | What works without an account and how to connect the account server |

Four skills use those tools: `ai-search-readiness-audit` (a prioritized fix
list), `llms-txt-builder` (a ready-to-publish llms.txt), `entity-schema-builder`
(Organization or LocalBusiness JSON-LD built only from facts on the page) and
`prompt-opportunity-plan` (a prompt-tracking plan).

## Example prompts

- Is example.com ready to be quoted by ChatGPT and Perplexity? What should I fix first?
- Check which AI crawlers my robots.txt blocks and write me an llms.txt.
- Build Organization schema for my homepage from what is already on the page.

## What it runs, sends and stores

The plugin runs no local code, hooks or scripts. Each tool call sends the
website address you name to `serp.tsoden.ai`. The server fetches only public
pages of that site (the home page, a few internal pages, robots.txt,
sitemap.xml, llms.txt) and stores the result behind an unguessable link so the
result page can be shared. It does not read the conversation, files or memory.

## Privacy policy

https://serp.tsoden.ai/privacy-policy

## Troubleshooting and support

A check that answers `invalid_url` was given an address that is not a public
website. `rate_limited` means too many checks ran in a short time; try again in
a few minutes. Setup guide: https://serp.tsoden.ai/integrations/ai-assistants.
Support: https://serp.tsoden.ai/support/chat or info@tsoden.ai.

License: MIT
