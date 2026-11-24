# Loopthink for Lexware Office

Ask about the invoices, quotations, vouchers, contacts and payments in your Lexware Office account in plain language. Read-only unless you allow more.

Ask about the invoices, quotations, vouchers, contacts and payments in your Lexware Office account in plain language. Read-only unless you allow more.

What you can ask:
- Which invoices are still open, and how much is outstanding in total?
- Show me the quotations from this month that were not accepted yet.
- What did we invoice customer Acme this year?
- Which invoices became overdue last week?
- Which articles do we sell, and at what net price?

How it works:
1. Add the app and sign in with Google or Microsoft. Your Loopthink account is created on the spot.
2. Right after sign-in, a form on our page asks for your Lexware Office API key (created at app.lexware.de/addons/public-api, shown only once), and whether changes are allowed. We run one read to test it. Credentials are entered there, never in the chat.
3. Ask in Claude. Nothing needs refreshing after you connect.

Read-only by default:
- Everything is read-only by default: documents, contacts, articles and payments are only read.
- The one tool that changes something creates a customer contact. It stays off unless you tick "Also allow changes" on the form, or an admin allows it later, and Claude asks you before each one.
- Nothing is ever deleted or booked, and no document is created, changed or sent.
- Fields with personal data can be masked per server before they reach the chat.
- Lexware Office allows two requests per second. Large evaluations take a moment.

Built for teams:
- Every person signs in with their own account.
- Access is granted per member group, reading and writing separately.
- Every call is logged with who ran it.

## What it can do

- Show whether Lexware Office is connected and how to connect it
- Find invoices, quotations, credit notes and other vouchers by type, status and date
- Read one document with its line items, totals and payment terms
- Tell what is paid and what is still open on a document
- Look up contacts, articles, payment conditions and posting categories
- Create a customer contact, only where the workspace switched that on

## Try asking

- Which invoices are still open in Lexware Office?
- What did we invoice this month, by customer?
- Which quotations are still waiting for an answer?

## Install

In Claude, add **Loopthink for Lexware Office** from the directory. In Claude Code:

```bash
claude plugin marketplace add loopthink/claude-plugin
```

```bash
claude plugin install loopthink-lexware-office@loopthink-ai
```

Then sign in: run `/mcp`, select `lexware-office`, choose **Authenticate**. A
first sign-in creates a free Loopthink workspace. `/loopthink-lexware-office:get-started`
walks through connecting and the first question.

## What is in this plugin

| Component | Name | What it does |
| --- | --- | --- |
| MCP server | `lexware-office` | Remote connector at `https://mcp.eu.loopthink.ai/mcp/lexware-office`, OAuth 2.0 with PKCE and dynamic client registration |
| Skill | `/loopthink-lexware-office:get-started` | Connect the system, find out why a tool returns nothing, and how to ask |

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

- Setup guide: <https://www.loopthink.ai/connect/lexware-office>
- Support: <https://www.loopthink.ai/support>
- Privacy policy: <https://www.loopthink.ai/privacy-policy>
- Terms: <https://www.loopthink.ai/terms-and-conditions>
- Issues: <https://github.com/loopthink/claude-plugin/issues>

## License

MIT. The license covers this plugin's contents. Use of the Loopthink service is
governed by your Loopthink agreement.
