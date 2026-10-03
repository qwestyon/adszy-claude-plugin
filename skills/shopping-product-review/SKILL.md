---
name: shopping-product-review
description: Review Shopping and Performance Max product performance through Adszy MCP. Use for hero and zombie products, products wasting spend, Merchant Center disapprovals or serving issues, product feed quality, and Shopping or Performance Max search terms.
---

# Shopping Product Review

Use Adszy's read-only product tools to find which products earn their spend, which waste it, and what is stopping products from serving.

## Workflow

1. Resolve the account with `list_ad_accounts` when it is ambiguous.
2. Call `get_products` for totals, segments (hero, sidekick, villain, zombie) and the top products by spend, ROAS or conversions.
3. Add only what the question needs:
   - `get_product_issues` for Merchant Center serving problems, not-eligible products and out-of-stock products still spending.
   - `get_feed_audit` for feed completeness and attribute quality.
   - `get_shopping_search_terms` for the queries behind Shopping and Performance Max spend, including the wasted list.
4. Return a short brief:
   - what is working (hero products and why);
   - where spend is at risk (villains, zombies, serving issues), with the evidence;
   - feed fixes ranked by spend at risk;
   - next safe checks.

## Guardrails

- These tools read Adszy's stored product snapshot: a fixed recent window refreshed overnight. State the snapshot date and window, and do not present it as real time or as the user's requested custom range.
- The product tools return data only for e-commerce accounts with Shopping or Performance Max product data. If they come back empty, say the account has no product data rather than calling it healthy.
- Segments are labels from Adszy's rules, not verdicts. Give the reason and ROAS target behind each one.
- A zero-conversion product is not automatically a problem. Consider spend, clicks, window length and conversion lag.
- Never claim Adszy changed the feed, Merchant Center or the account; every tool is read-only.
- State the account currency.
