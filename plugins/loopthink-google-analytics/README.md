# Loopthink for Google Analytics

Ask GA4 in plain language. Sessions, conversions and landing pages. Read-only, no API key.

Ask GA4 in plain language. Sessions, conversions and landing pages. Read-only, no API key.

What you can ask:
- How many sessions and users did we have last week, compared with the week before?
- Which landing pages convert best?
- Where does our traffic come from?
- How many people are on the site right now?

How it works:
1. Add the app and sign in with Google or Microsoft. Your Loopthink account is created on the spot.
2. Connect Google Analytics with the Google account that has access to your GA4 properties, and pick the ones to share.
3. Ask in Claude. Nothing needs refreshing after you connect.

Read-only:
- The app never changes anything in Google Analytics.
- Your Google sign-in stays in Loopthink and never passes through Claude.

Built for teams:
- Every person signs in with their own account.
- Access is granted per member group.
- Every tool call is logged with who ran it.

## What it can do

- Show whether Google Analytics is connected and how to connect it
- List the GA4 properties you can query
- Report sessions, users, conversions and revenue by any GA4 dimension and date range
- Show realtime users on the site
- Look up the dimensions and metrics a property offers

## Try asking

- How many sessions did we have last week compared with the week before?
- Which landing pages bring the most conversions this month?
- Where does our traffic come from?

## Install

In Claude, add **Loopthink for Google Analytics** from the directory. In Claude Code:

```bash
claude plugin marketplace add loopthink/claude-plugin
```

```bash
claude plugin install loopthink-google-analytics@loopthink-ai
```

Then sign in: run `/mcp`, select `google-analytics`, choose **Authenticate**. A
first sign-in creates a free Loopthink workspace. `/loopthink-google-analytics:get-started`
walks through connecting and the first question.

## What is in this plugin

| Component | Name | What it does |
| --- | --- | --- |
| MCP server | `google-analytics` | Remote connector at `https://mcp.eu.loopthink.ai/mcp/google-analytics`, OAuth 2.0 with PKCE and dynamic client registration |
| Skill | `/loopthink-google-analytics:get-started` | Connect the system, find out why a tool returns nothing, and how to ask |

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

- Setup guide: <https://www.loopthink.ai/connect/google-analytics>
- Support: <https://www.loopthink.ai/support>
- Privacy policy: <https://www.loopthink.ai/privacy-policy>
- Terms: <https://www.loopthink.ai/terms-and-conditions>
- Issues: <https://github.com/loopthink/claude-plugin/issues>

## License

MIT. The license covers this plugin's contents. Use of the Loopthink service is
governed by your Loopthink agreement.
