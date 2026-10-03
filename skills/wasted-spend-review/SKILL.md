---
name: wasted-spend-review
description: Find and explain likely wasted Google Ads spend through Adszy MCP. Use for search-term reviews, negative-keyword candidates, irrelevant-query analysis, zero-conversion spend, or requests to reduce PPC waste.
---

# Wasted Spend Review

Build a read-only candidate list grounded in search-term and keyword evidence.

## Workflow

1. Resolve the account with `list_ad_accounts` when needed.
2. For search terms, follow the `search-term-review` policy and use the same date window for `get_negative_keyword_candidates` and `get_search_terms`.
3. Use `get_keywords` only when positive-keyword context is needed.
4. Return recommendations in three friendly groups:
   - **Act:** verified Clear mismatch or another well-supported, reversible account action.
   - **Review:** Needs judgement, weak evidence, or a decision that needs advertiser context.
   - **Watch:** relevant opportunities and signals worth monitoring without changing now.
5. For each item, give the entity, evidence, reason, confidence, and next review step.

## Guardrails

- Never claim a negative keyword was added or applied.
- Do not treat every zero-conversion term as irrelevant; consider spend, clicks, window length, conversion lag, and business intent.
- Keep strict mismatches separate from judgement calls.
- Candidate pools are discovery signals, not approvals. Zero conversions, CTR, token mismatch, and generic modifiers never independently prove irrelevance.
- Never place related, converting, brand/product-aligned, or potentially valuable search terms under Act as negatives.
- State the analysis dates and currency.
- Describe savings as avoidable historical spend, not guaranteed future savings.
- If the user asks to make changes, explain that Adszy MCP is read-only and provide a review list instead.
