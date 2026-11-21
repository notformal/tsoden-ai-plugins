---
name: entity-schema-builder
description: Check a page's structured data and generate Organization or LocalBusiness JSON-LD so answer engines can state who the brand is. Use when the user asks for schema markup, structured data, JSON-LD, or when an audit reports missing entity signals. Also in other languages, e.g. «микроразметка schema», «розмітка JSON-LD», «dane strukturalne», «strukturierte Daten», «štruktúrované dáta», «dados estruturados», «datos estructurados», «dati strutturati», «құрылымдық деректер», «נתונים מובנים», «البيانات المنظمة».
---

# Entity schema builder

## Steps

1. Call `check_schema_readiness` with the page URL. Note which entity signals
   are present and which are missing (name, url, logo, description, sameAs,
   contact/address).
2. Decide the type: `LocalBusiness` (or a more specific subtype such as `Dentist`,
   `Restaurant`, `Store`) when the business serves customers at an address;
   `Organization` otherwise. Ask if it is unclear.
3. Build JSON-LD from facts that are already on the page, in the tool result, or
   given by the user.

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "...",
  "url": "https://...",
  "logo": "https://.../logo.png",
  "description": "...",
  "sameAs": ["https://www.linkedin.com/company/...", "https://..."],
  "contactPoint": {"@type": "ContactPoint", "telephone": "...", "contactType": "customer support"}
}
</script>
```

## Rules

- Never invent an address, phone number, founding date, rating or social profile.
  Leave a clearly marked placeholder (`"TODO: add phone"`) and list what the user
  must fill in.
- Do not add `aggregateRating` or `review` unless the user supplies real, visible
  reviews — fabricated ratings break search-engine policies.
- Keep existing valid markup; add only what is missing, and say whether to merge
  it into an existing block or add a new one.
- After the user publishes it, re-run `check_schema_readiness` to confirm.
- Reply in the language of the user's request, including table headers and next steps.
