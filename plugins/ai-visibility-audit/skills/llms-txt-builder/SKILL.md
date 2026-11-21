---
name: llms-txt-builder
description: Check a site's existing /llms.txt and write a valid llms.txt (llmstxt.org format) that points answer engines at the pages worth quoting. Use when the user asks for an llms.txt, wants AI assistants to read the right pages, or the audit reports llms.txt as missing or invalid. Also in other languages, e.g. «создай llms.txt», «створи llms.txt», «utwórz llms.txt», «llms.txt erstellen», «vytvoř llms.txt», «criar llms.txt», «crear llms.txt», «crea llms.txt», «llms.txt файлын құру», «צור קובץ llms.txt», «أنشئ ملف llms.txt».
---

# llms.txt builder

## Steps

1. Call `check_ai_crawler_access` with the site URL. Read its `llms` object: does
   a file exist, and is it valid? Report what is there before proposing anything.
2. Collect the pages to list. Use pages the user names, pages you can see in the
   tool results, or ask. Never invent URLs — an llms.txt pointing at 404s is worse
   than none. If you only have the home page, ask the user for their 5–15 most
   important pages (pricing, product/service pages, docs, about, contact).
3. Write the file in the llmstxt.org format:

```
# <Site or product name>

> <One or two sentences: what the business is and who it serves.>

<Optional short paragraph with key facts an assistant should know.>

## <Section, e.g. Products>
- [<Page title>](<absolute URL>): <what the page answers>

## Optional
- [<Secondary page>](<absolute URL>): <note>
```

## Rules

- One H1, then a blockquote summary, then H2 sections of Markdown links.
- Absolute `https://` URLs only, each on the site's own domain.
- Describe each page by the question it answers, not by marketing copy.
- Keep it curated: 5–40 links. Put secondary pages under `## Optional`.
- Tell the user to publish it at `https://<domain>/llms.txt` as `text/plain` or
  `text/markdown`, then re-run `check_ai_crawler_access` to confirm it validates.
- llms.txt does not override robots.txt: if a crawler is blocked there, say so.
- Reply in the language of the user's request, including table headers and next steps.
