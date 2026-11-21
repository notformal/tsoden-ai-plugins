---
name: content-scale-safety
description: Keep a site out of Google's scaled-content demotion when generating or publishing articles, and plan the recovery of a site that was already demoted. Use before writing or publishing many articles, translating a blog into new languages, or when traffic collapsed after a content push. Also in other languages, e.g. «сайт упал после публикации статей», «безопасно ли публиковать AI-статьи», «сайт впав після статей», «spadek ruchu po publikacji artykułów», «Abstrafung nach KI-Artikeln», «propad návštěvnosti po článcích», «o site caiu depois de publicar artigos», «el sitio cayó tras publicar artículos», «il sito è crollato dopo gli articoli», «мақалалардан кейін сайт трафигі түсті», «האתר ירד אחרי פרסום מאמרים», «انخفضت زيارات الموقع بعد نشر المقالات».
---

# Content scale safety

Google demotes a whole domain, not one page, when it sees content made at
scale: thousands of generated articles, many languages without demand, most of
the corpus never indexed. Recovery takes weeks or months, so prevention comes first.

## Before generating or publishing

1. `list_clients` → find the project.
2. `get_content_safety` with `lang` set to the language of the planned article.
   If `safe_to_publish` is false, stop and report each blocked rule's `message`.
   A rule in state `not_measured` is not a pass: say what is missing.
3. Also stop and tell the user instead of producing more articles when any of these holds
   (`get_search_console_data` gives the detail):
   - impressions fell by half or more against the previous period of the same length;
   - half or more of the articles older than four weeks have no impressions;
   - the plan adds a language where the project tracks no keywords (no measured demand);
   - the batch would publish more than about one new article a day on one site.
4. Write fewer, better pages: one page per real query, with first-hand detail,
   a named author and sources. Never translate a whole blog into languages
   without demand, and never keep English slugs on translated pages.

## When the server refuses to publish

The publish endpoint refuses on its own when the site is publishing too fast,
losing impressions, carrying unindexed articles or writing in a language without
tracked demand. That refusal is final. Do not work around it by splitting the
batch, switching destination or project, or rewording the article. Report the
reason to the user word for word.

## Recovery plan for a demoted site

1. Stop all automatic publishing.
2. `get_content_safety` returns `recovery_plan`: `keep` (pages with clicks),
   `improve` (impressions, no clicks), `remove` (our articles 4+ weeks old with no
   impressions) and `young` (too new to judge). Pages Google never showed are not in
   Search Console; for those, ask for a crawl or the site's own page list.
3. Pages with no impressions: remove them (410) and drop them from the sitemap.
   Start with languages without demand.
4. Pages with impressions but no clicks: merge pages on the same topic into
   one stronger page and 301-redirect the rest to it.
5. Pages with clicks: improve them with experience, data, author and a fresh update date.
6. Re-check Search Console after two to three weeks. Resume publishing slowly,
   only for queries with measured demand.

## Rules

- Never promise a recovery date: a site-wide demotion lifts only after the
  content changes and Google re-evaluates the site.
- A missing Search Console connection means "not measured", not "fine".
- Reply in the language of the user's request, including table headers and next steps.
