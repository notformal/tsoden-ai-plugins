---
name: answer-engine-visibility-report
description: Report how often ChatGPT, Claude, Gemini, Perplexity and Google AI Overviews mention and cite the user's brand versus competitors, from the tracked prompts in their Tsoden account. Use when the user asks about AI visibility, share of voice in AI answers, whether AI assistants recommend them, or wants a client-ready AEO report. Also in other languages, e.g. «видимость бренда в ChatGPT», «AEO-отчёт», «видимість у відповідях ШІ», «widoczność marki w ChatGPT», «Sichtbarkeit in KI-Antworten», «viditeľnosť v odpovediach AI», «visibilidade da marca no ChatGPT», «visibilidad de marca en ChatGPT», «visibilità del brand su ChatGPT», «брендтің ChatGPT-дегі көрінуі», «נראות המותג ב-ChatGPT», «ظهور العلامة التجارية في ChatGPT».
---

# Answer-engine visibility report

## Steps

1. `list_clients` → pick the project (ask if ambiguous).
2. `get_answer_engine_visibility` for the overall mention and citation rates per
   engine.
3. `get_answer_engine_results` for the latest per-prompt, per-engine outcome.
4. `get_brand_mentions` for how the brand and competitors are described, with
   excerpts.
5. `get_answer_engine_history` to show the trend; `get_visibility_index` for the
   single comparable score.
6. `get_prompt_performance` to find the prompts that win or lose a mention.

## Output

- Headline: visibility index and its change, mention rate per engine.
- Where the brand wins (prompts + engines) and where competitors win instead.
- Which sources the engines cite when they answer — the pages to earn or improve.
- Three to five actions: content for prompts the brand loses, sources to get
  cited on, prompts to start tracking (`add_answer_engine_prompt`).

## Rules

- Quote only measured numbers. An engine that returned no answer is a gap, not
  "not mentioned" — say it was not measured.
- Answers vary between runs; describe rates over the tracked set, not a single
  answer, and mention the check date.
- Starting a new check (`start_answer_engine_check`) spends the plan's
  answer-engine checks: only on request, after confirming.
- Reply in the language of the user's request, including table headers and next steps.
