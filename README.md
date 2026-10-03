# Adszy for Claude

Google Ads analysis in Claude. Ask about your Google Ads account in plain English — "what needs attention today?", "where am I wasting spend?", "which products are dragging ROAS down?" — and Claude answers from your real account data through Adszy's read-only tools.

## What's included

- **The Adszy connector** (`https://mcp.adszy.ai/mcp`): curated, read-only Google Ads tools covering account performance, period comparisons, campaign settings, budget pacing, keywords, search terms, negative-keyword candidates, ads and ad strength, change history, disapprovals, Google's recommendations, anomalies, auction insights, conversion actions, landing pages, devices, locations, and Shopping / Performance Max products, product issues and feed quality.
- **Five skills** that teach Claude how to use those tools well:
  - `account-health-triage`: what needs attention in the account right now
  - `performance-brief`: week-on-week or month-on-month recaps and client-ready reports
  - `search-term-review`: grouping search terms safely before you add negatives
  - `wasted-spend-review`: likely wasted spend, with the evidence
  - `shopping-product-review`: Shopping and Performance Max products, Merchant Center issues and feed quality

## What you need

- An Adszy account (free to start) at [adszy.ai](https://adszy.ai) with at least one Google Ads account linked.
- MCP calls use the monthly allowance on your Adszy plan. Ask Claude "how much Adszy allowance do I have left?" at any time.

## Setup

1. Install this plugin.
2. Connect Adszy when Claude asks. Claude opens Adszy's sign-in page: sign in, review the read-only request, choose your default Google Ads account and approve.
3. Ask a question, for example:
   - What needs attention in my Google Ads account today?
   - Give me a weekly Google Ads digest and tell me what changed.
   - Find wasted spend and explain the evidence.
   - Which Shopping products are spending without converting?

Full documentation: [adszy.ai/mcp](https://adszy.ai/mcp).

## Read-only by design

No Adszy tool can create, edit, pause or delete anything in Google Ads, or change budgets, bids, targeting, keywords or ads. If you ask Claude to make a change, it will give you a review list instead; changes are made by you, inside Adszy or Google Ads.

## What this plugin runs, sends and stores

- **Runs locally:** nothing. The plugin contains Markdown skills and one remote MCP server entry. There are no hooks, scripts, binaries or package installs.
- **Network:** Claude connects to one server, `https://mcp.adszy.ai/mcp`, over HTTPS using OAuth 2.0 (scope `ads.read`). Each tool call sends the tool name and its arguments (for example an account ID and a date range). Adszy returns the Google Ads data needed to answer, for the accounts you have linked and approved.
- **Not sent:** your Google OAuth tokens and Adszy credentials never reach Claude. Adszy does not read your Claude conversations, memory or files.
- **Stored by Adszy:** connection records and usage counters, OAuth codes (up to 10 minutes), access tokens (up to 1 hour) and refresh tokens (up to 30 days, or until revoked). Revoke access at any time from Adszy Settings → MCP.

## Privacy policy

Adszy's privacy policy, including how MCP data is handled and retained, is at [adszy.ai/legal](https://adszy.ai/legal).

## Support

Email [support@adszy.ai](mailto:support@adszy.ai).

---

Google Ads is a trademark of Google LLC. Adszy is not affiliated with or endorsed by Google.
