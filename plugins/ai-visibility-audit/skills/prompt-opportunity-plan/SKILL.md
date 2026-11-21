---
name: prompt-opportunity-plan
description: Find the questions people ask answer engines where a brand could be recommended, and turn them into a tracking and content plan. Use when the user asks which prompts to track, how to get mentioned by ChatGPT or Perplexity for their category, or what content to write for AI search. Also in other languages, e.g. «какие запросы отслеживать в ChatGPT», «як потрапити у відповіді ChatGPT», «jak trafić do odpowiedzi ChatGPT», «wie werde ich von ChatGPT empfohlen», «jak se dostat do odpovědí AI», «como aparecer nas respostas do ChatGPT», «cómo aparecer en las respuestas de ChatGPT», «come comparire nelle risposte di ChatGPT», «ChatGPT жауаптарына қалай шығуға болады», «איך להופיע בתשובות של ChatGPT», «كيف أظهر في إجابات ChatGPT».
---

# Prompt opportunity plan

## Steps

1. Call `find_prompt_opportunities` with the site URL.
2. Group the returned prompts by intent: category/best-of ("best X for Y"),
   comparison ("X vs Y"), problem ("how to fix Z"), local ("X near <city>").
3. For each group pick the 3–5 prompts that match what the site actually offers.
   Drop prompts the business cannot credibly answer.
4. For each chosen prompt, name the page that should answer it (existing URL from
   the site, or "new page needed") and what that page must contain to be quotable:
   a direct answer in the first paragraph, facts with numbers, a comparison table
   or FAQ block.

## Output

- A table: prompt · intent · page that answers it · what to add.
- The `result_page` link from the tool.
- A note that ranking in answers must be measured over time: the same prompts
  should be re-asked weekly across engines, because answers change.

## Rules

- Present prompts as opportunities, not as proof the brand is or is not mentioned
  today — this tool does not query the answer engines.
- Do not promise placement in any answer engine.
- Reply in the language of the user's request, including table headers and next steps.
