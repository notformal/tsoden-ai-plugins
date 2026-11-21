---
name: ai-search-readiness-audit
description: Audit whether a website can be found, read and quoted by answer engines (ChatGPT, Claude, Gemini, Perplexity, Google AI Overviews) and return a prioritized fix list. Use when the user asks if their site shows up in AI answers, why an AI assistant does not mention them, or what to fix for AI search, AEO or GEO. Also in other languages, e.g. «видит ли ChatGPT мой сайт», «аудит сайта для AI-поиска», «чи бачить ChatGPT мій сайт», «czy ChatGPT widzi moją stronę», «wird meine Website in KI-Antworten gezeigt», «vidí ChatGPT můj web», «o ChatGPT vê o meu site», «ChatGPT ve mi sitio web», «ChatGPT vede il mio sito», «ChatGPT менің сайтымды көре ме», «האם ChatGPT רואה את האתר שלי», «هل يرى ChatGPT موقعي».
---

# AI-search readiness audit

Use the live checks from the `ai-visibility` MCP server. Never estimate a score,
a crawler rule or a schema field yourself — every fact in the answer comes from a
tool result.

## Input

A public website address. If the user gave none, ask for one. If they named a
brand but no site, ask for the site rather than guessing the domain.

## Steps

1. Call `audit_ai_readiness` with the URL. It returns `ai_readiness_score`
   (0–100), `seo_hygiene_score`, `ai_checks`, `checks` and `explanations`.
2. If `ai_checks` shows `ai_crawlers` as `fail` or `warn`, call
   `check_ai_crawler_access` to name the exact bots and see the llms.txt verdict.
3. If `ai_schema` or `ai_entity` is not `ok`, call `check_schema_readiness` to
   list which entity facts are missing.
4. Optionally call `get_ai_readiness_benchmark` to say how the site compares with
   other checked sites. Only quote benchmark numbers the tool returned.

## Output

- One line with the AI-readiness score and what it means.
- **Fix first**: at most five items, ordered by impact. A blocked crawler always
  comes first — nothing else matters while an answer engine cannot read the site.
  Then missing entity schema, missing Q&A structure, thin content, llms.txt.
- For each item: what is wrong (quote the check), why it matters for answer
  engines, and the concrete change.
- The `result_page` links returned by the check tools, so the user can share the
  evidence (the audit itself returns `run_again_in_browser` instead).

## Rules

- A check with `no_data: true` was not measured. Say so; never report it as passed
  or failed.
- If a tool returns `unreachable`, tell the user the site could not be loaded and
  stop; do not audit from memory.
- Blocking or allowing crawlers is the owner's decision. Explain the trade-off
  (training crawlers vs. crawlers that fetch pages to cite them) instead of
  telling them to allow everything.
- The user's explicit instructions override this workflow.
- Reply in the language of the user's request, including table headers and next steps.
