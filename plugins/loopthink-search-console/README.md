# Google Search Console by Loopthink

Ask Google Search Console in plain language. Queries, pages, clicks and rankings. Read-only, no API key.

Ask Google Search Console in plain language. Queries, pages, clicks and rankings. Read-only, no API key.

What you can ask:
- Which queries bring the most clicks?
- Which pages lost impressions last month?
- Which pages get impressions but few clicks?
- Where do I rank on page two and could move up?
- Do my sitemaps report errors?

How it works:
1. Add the app and sign in with Google or Microsoft. Your Loopthink account is created on the spot.
2. Connect Search Console with the Google account that has access to your properties, and pick the ones to share.
3. Ask in Claude. Nothing needs refreshing after you connect.

Read-only:
- The app never changes anything in Search Console.
- Your Google sign-in stays in Loopthink and never passes through Claude.

Built for teams:
- Every person signs in with their own account.
- Access is granted per member group.
- Every tool call is logged with who ran it.

## What it can do

- Show whether Search Console is connected and how to connect it
- List the Search Console properties you can query
- Report clicks, impressions, CTR and position by query, page, country, device or date
- Show submitted sitemaps with their errors and URL counts

## Try asking

- Which queries lost the most clicks in the last 28 days?
- Which pages get impressions but few clicks?
- Do my sitemaps report any errors?

## Install

In Claude, add **Google Search Console by Loopthink** from the directory. In Claude Code:

```bash
claude plugin marketplace add loopthink/claude-plugin
```

```bash
claude plugin install loopthink-search-console@loopthink-ai
```

Then sign in: run `/mcp`, select `google-search-console`, choose **Authenticate**. A
first sign-in creates a free Loopthink workspace. `/loopthink-search-console:get-started`
walks through connecting and the first question.

## What is in this plugin

| Component | Name | What it does |
| --- | --- | --- |
| MCP server | `google-search-console` | Remote connector at `https://mcp.eu.loopthink.ai/chatgpt/google-search-console`, OAuth 2.0 with PKCE and dynamic client registration |
| Skill | `/loopthink-search-console:get-started` | Connect the system, find out why a tool returns nothing, and how to ask |

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

- Setup guide: <https://www.loopthink.ai/connect/google-search-console>
- Support: <https://www.loopthink.ai/support>
- Privacy policy: <https://www.loopthink.ai/privacy-policy>
- Terms: <https://www.loopthink.ai/terms-and-conditions>
- Issues: <https://github.com/loopthink/claude-plugin/issues>

## License

MIT. The license covers this plugin's contents. Use of the Loopthink service is
governed by your Loopthink agreement.
