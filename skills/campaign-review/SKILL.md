---
name: campaign-review
description: Review the user's own ad campaign performance and manage running campaigns. Use when the user asks how their campaigns are doing, wants spend, clicks, or conversion numbers, wants a weekly or Monday review, or wants to pause, resume, or change the budget of a campaign.
---

# Campaign performance review and management

These tools act on the USER'S OWN connected ad accounts (Meta, Google, TikTok), never on competitor data.

## The review

1. `list_ad_accounts` to see what is connected. If nothing is, `connect_ad_account` returns the browser link to connect one.
2. `get_account_performance` pulls real spend, impressions, clicks, and conversions. Pass a campaignId to drill into one campaign, including Google keyword-level diagnostics.
3. `list_campaigns` shows everything running with status and budget.

Report only numbers the tools return. Currency follows the ad account's own billing currency, and outputs label it when it is not USD.

A good review answers three questions in plain language: what is spending, what is converting, and what single change matters most this week. Make one concrete recommendation, not a list of ten.

## Making changes

- `update_budget`, `pause_campaign`, `resume_campaign`, `update_campaign_locations` (Google), `update_keywords` and `add_negative_keywords` (Google, when available).
- Budget changes and resumes are TWO-STEP: preview plus confirmToken first, execute only after the user's explicit OK.
- `resume_campaign` starts real spend. Always surface the warning.
- `pause_campaign` is single-step since it only stops spend.

## Recurring reviews

There is no scheduler in this connection, but two good habits work well:
- The user can simply ask for a review any time ("Monday review, please") and you run the workflow fresh.
- For automatic weekly competitor digests by email, AdWhispr Pro members can flip the toggle at https://adwhispr.com/dashboard/settings under Email Alerts. That digest covers tracked competitors' ad changes, not the user's own campaign numbers.
