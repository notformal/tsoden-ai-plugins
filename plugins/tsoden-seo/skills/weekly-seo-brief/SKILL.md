---
name: weekly-seo-brief
description: Write a short weekly SEO and AI-visibility brief for one project from the user's Tsoden account — what moved, why it matters, what to do next. Use when the user asks for a weekly update, a status report for a client or manager, or "what happened this week". Also in other languages, e.g. «SEO-отчёт за неделю», «що змінилося за тиждень у SEO», «tygodniowy raport SEO», «wöchentlicher SEO-Bericht», «týždenný SEO report», «týdenní SEO report», «relatório semanal de SEO», «informe semanal de SEO», «report SEO settimanale», «апталық SEO есебі», «דוח SEO שבועי», «تقرير SEO الأسبوعي».
---

# Weekly SEO brief

## Steps

1. `list_clients` → pick the project.
2. `get_client` for the domain and tracked keyword count; `list_jobs` to find the
   latest completed ranking check and its date.
3. `get_top_movers` and `get_ranking_opportunities`.
4. `get_visibility_history` for the search trend.
5. `get_answer_engine_visibility` for AI-answer visibility (skip the section if
   the project tracks no prompts).

## Output (keep it under 250 words)

1. **Headline** — one sentence with the most important change.
2. **Rankings** — visibility trend; top 3 gains and top 3 losses (keyword · was →
   now).
3. **AI answers** — mention rate and its change, if tracked.
4. **Opportunities** — up to 3 keywords close to the top where a small push pays.
5. **Next week** — up to 3 concrete actions.

State the check dates the brief is based on. If the latest check is older than
7 days, say so and offer to start one (confirm first; it spends plan limits).

## Rules

- Reply in the language of the user's request, including table headers and next steps.
