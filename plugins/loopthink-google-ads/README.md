# Loopthink for Google Ads

Ask Google Ads in plain language. Campaigns, keywords and costs. No API key, no setup.

Ask Google Ads in plain language. Campaigns, keywords and costs. No API key, no setup.

What you can ask:
- What did each campaign cost and convert last week?
- Which keywords spend money without converting?
- Which search terms triggered my ads in the last 30 days?
- Add these search terms as negative keywords.
- Lower the daily budget of my most expensive campaign to 30 euros.

How it works:
1. Add the app and sign in with Google or Microsoft. Your Loopthink account is created on the spot.
2. Connect Google Ads with the Google account that has access to your ad accounts, and pick the accounts to share.
3. Ask in Claude. Nothing needs refreshing after you connect.

Changes, with guard rails:
- Reports work right away. Changes only where your workspace turns on "Allow changes" for the account.
- The app creates and updates budgets, campaigns, ad groups, ads, keywords and negative keyword lists.
- It never starts a campaign and never removes anything. New campaigns are created paused, and you switch them on in Google Ads.
- Every change is checked with Google first, and Claude asks you before it is applied.
- No developer token and no API key. Your Google sign-in stays in Loopthink and never passes through Claude.

Agencies and manager accounts:
- Client accounts under a manager account (MCC) work. You pick which ones the app may use.

Built for teams:
- Every person signs in with their own account.
- Access is granted per member group, reports and changes separately.
- Every report and every change is logged with who ran it, including the values before and after.

## What it can do

- Show whether Google Ads is connected and how to connect it
- List the Google Ads accounts you can use, including client accounts under a manager account
- Report campaigns, ad groups, ads and keywords: cost, clicks, impressions, CTR and conversions
- Report the search terms that triggered your ads
- Create and update budgets, campaigns, ad groups, ads and keywords, with a preview before applying
- Add negative keywords and fill negative keyword lists
- Never starts a campaign and never removes anything; new campaigns are created paused

## Try asking

- What did each campaign cost and convert last week?
- Which keywords spent the most without a conversion in the last 30 days?
- Add the search terms without conversions as negative keywords.

## Install

In Claude, add **Loopthink for Google Ads** from the directory. In Claude Code:

```bash
claude plugin marketplace add loopthink/claude-plugin
```

```bash
claude plugin install loopthink-google-ads@loopthink-ai
```

Then sign in: run `/mcp`, select `google-ads`, choose **Authenticate**. A
first sign-in creates a free Loopthink workspace. `/loopthink-google-ads:get-started`
walks through connecting and the first question.

## What is in this plugin

| Component | Name | What it does |
| --- | --- | --- |
| MCP server | `google-ads` | Remote connector at `https://mcp.eu.loopthink.ai/mcp/google-ads`, OAuth 2.0 with PKCE and dynamic client registration |
| Skill | `/loopthink-google-ads:get-started` | Connect the system, find out why a tool returns nothing, and how to ask |

The plugin ships no binaries and runs no code on your machine. It contributes
one remote MCP endpoint and one skill. The tool list is the same for every
user; what a tool returns depends on what you connected and what your member
group was granted.

## Security and data handling

- Credentials for the connected system are entered in the Loopthink web app,
  never in the chat, and are not passed to Claude.
- Every person signs in with their own account. Access is granted per member
  group, and every call is logged with who ran it.
- Masking rules set in Loopthink run on the server before a result is returned.
- Loopthink is operated in the EU.

## Support

- Setup guide: <https://www.loopthink.ai/connect/google-ads>
- Support: <https://www.loopthink.ai/support>
- Privacy policy: <https://www.loopthink.ai/privacy-policy>
- Terms: <https://www.loopthink.ai/terms-and-conditions>
- Issues: <https://github.com/loopthink/claude-plugin/issues>

## License

MIT. The license covers this plugin's contents. Use of the Loopthink service is
governed by your Loopthink agreement.
