---
name: rank-drop-diagnosis
description: Diagnose why a project's Google rankings dropped or rose, using the measured positions in the user's Tsoden account. Use when the user asks why traffic or rankings fell, which keywords dropped, who overtook them, or what changed since the last check. Also in other languages, e.g. «почему упали позиции», «упал трафик из Google», «чому впали позиції», «dlaczego spadły pozycje», «warum sind meine Rankings gefallen», «prečo klesli pozície», «proč klesly pozice», «por que minhas posições caíram», «por qué bajaron mis posiciones», «perché sono calate le posizioni», «неге позициялар төмендеді», «למה המיקומים שלי ירדו», «لماذا انخفض ترتيب موقعي».
---

# Rank-drop diagnosis

Work only from data the `tsoden` tools return. A cause you cannot point to in the
data is a hypothesis and must be labelled as one.

## Steps

1. `list_clients` → find the project. If several match, ask which one.
2. `get_top_movers` for the project: the biggest losers and gainers between the
   two latest completed checks.
3. For the top losers:
   - `get_keyword_history` to see whether the drop is new or a trend;
   - `get_serp_features` to see whether a search feature (AI Overview, featured
     snippet, local pack, video) now takes the space;
   - `get_competitor_visibility` to see whether a tracked competitor rose at the
     same time.
4. If Search Console is connected, `get_search_console_data` to check whether
   clicks actually fell for those queries.

## Output

- Summary line: how many keywords fell, how many rose, the biggest move.
- Table of the top losers: keyword · was → now · likely cause · evidence.
- Likely causes, each tied to evidence: a new SERP feature, a competitor gain, a
  URL change (the ranking URL differs between checks), or an across-the-board
  drop (suggests a site-wide issue or an algorithm update).
- Next actions, most impactful first.

## Rules

- A missing position is not a ranking of zero: if a result is marked as no data
  or a failed measurement, say the check did not measure it.
- Do not start a new ranking check unless the user asks; checks spend plan limits.
  If they ask, confirm first, call `start_serp_check`, then poll `get_job`.
- If a tool answers that a feature is not in the user's plan, say so plainly and
  continue with what is available.
- Reply in the language of the user's request, including table headers and next steps.
