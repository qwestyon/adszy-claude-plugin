---
name: search-term-review
description: Review Google Ads search terms safely through Adszy MCP. Use for negative-keyword reviews, irrelevant-query analysis, search-term cleanup, or deciding which queries to act on, review, or keep.
---

# Search-term Review

Apply Adszy Search-term Review policy version 2. This skill is read-only: it analyses and explains but never adds negatives or changes Google Ads.

## Method

1. Resolve the account with `list_ad_accounts` when needed.
2. Call `get_negative_keyword_candidates` and `get_search_terms` for the same date window.
3. Treat candidate pools as discovery signals, not proof of irrelevance.
4. Classify exact surfaced terms into all three groups:
   - **Clear mismatch:** confirmed wrong product, wrong service, unrelated industry, verified out-of-area location, or advertiser-verified competitor. State the reason and specific business evidence.
   - **Needs judgement:** related, informational, high-spend, high-CTR, ambiguous, or context-poor.
   - **Keep or opportunity:** relevant, converting, brand/product-aligned, or potentially valuable.
5. Summarise recommendations as:
   - **Act:** Clear mismatch rows for advertiser review.
   - **Review:** Needs judgement rows and the question needed to resolve them.
   - **Watch:** Keep or opportunity rows plus useful performance monitoring.

## Guardrails

- Zero conversions, CTR, literal token mismatch, and generic modifiers never independently qualify a term as a negative.
- Keep related queries under Needs judgement. For example, “building a well” for a bottled-water advertiser is related/ambiguous unless the advertiser confirms otherwise.
- Never recommend blocking converting terms, the advertiser's brand/products, or enabled positive keywords.
- Use exact search-term text. Do not stem, broaden, or turn a query into a generic category negative.
- Clear mismatch should default to exact match if the user later chooses to act in Adszy.
- State dates, currency, evidence gaps, and that historical spend is not guaranteed future savings.
- If the user asks to make changes, explain that this plugin is read-only and direct them to review and Apply inside Adszy.

This method adapts intent-first classification and human-review principles from the public PPC AI Skills pack; it does not use that pack's scripts, consensus pipeline, or mutation code.
