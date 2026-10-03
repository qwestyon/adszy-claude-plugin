---
name: performance-brief
description: Create an evidence-backed Google Ads performance brief through Adszy MCP. Use for week-over-week, month-over-month, or year-over-year comparisons, stakeholder updates, client reports, and concise performance recaps.
---

# Performance Brief

Turn Adszy's read-only metrics into a concise stakeholder-ready narrative.

## Workflow

1. Resolve the account with `list_ad_accounts` when it is ambiguous.
2. For a weekly recap or "what should I focus on" request, call `summarize_period` first. It gathers a dated comparison, campaign movers and a bounded set of diagnostics in one MCP call.
3. For a specific comparison or client brief, call `compare_periods` with the user's requested window, then `get_account_summary` for campaign detail.
4. Use a focused diagnostic tool only when needed: `get_change_history`, `get_budget_pacing`, `get_anomalies`, `get_landing_pages`, `get_devices`, or `get_locations`.
5. Write:
   - executive summary;
   - key metric changes;
   - campaign drivers;
   - risks or unknowns;
   - recommended next checks.

## Guardrails

- State both date ranges and the account currency.
- State coverage and any partial or missing datasets in a weekly digest.
- Use absolute and percentage changes where available.
- Do not invent explanations for movements. Separate measured drivers from hypotheses.
- Flag low volume, missing conversion data, and attribution limitations.
- Do not imply that Adszy applied any recommendation.
- Keep the brief readable without hiding material negative findings.
