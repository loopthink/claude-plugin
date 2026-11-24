# Loopthink for sevDesk

Ask about the invoices, orders, vouchers, contacts and bank transactions in your sevDesk account in plain language. Read-only unless you allow more.

Ask about the invoices, orders, vouchers, contacts and bank transactions in your sevDesk account in plain language. Read-only unless you allow more.

What you can ask:
- Which invoices are open or overdue, and what is the total?
- What did we invoice per customer this quarter?
- Which bank transactions from last week are not booked yet?
- What is the balance of our business account today?
- Which receipts did we record for supplier Acme this year?

How it works:
1. Add the app and sign in with Google or Microsoft. Your Loopthink account is created on the spot.
2. Right after sign-in, a form on our page asks for your sevDesk API token (in sevDesk under Settings > Users, in the details of the user), and whether changes are allowed. We run one read to test it. Credentials are entered there, never in the chat.
3. Ask in Claude. Nothing needs refreshing after you connect.

Read-only by default:
- Everything is read-only by default: invoices, orders, vouchers, contacts, accounts and transactions are only read.
- The one tool that changes something creates a contact. It stays off unless you tick "Also allow changes" on the form, or an admin allows it later, and Claude asks you before each one.
- Nothing is ever deleted or booked, and no document is created, changed or sent.
- Fields with personal data can be masked per server before they reach the chat.
- The token has the rights of its sevDesk user. A user of its own with a small role is the safest choice.

Built for teams:
- Every person signs in with their own account.
- Access is granted per member group, reading and writing separately.
- Every call is logged with who ran it.

## What it can do

- Show whether sevDesk is connected and how to connect it
- Find invoices, orders, credit notes and receipt vouchers by status, date and contact
- Read one document with its positions
- Read bank accounts, balances and transactions
- Look up contacts, parts with stock, and tags
- Create a contact, only where the workspace switched that on

## Try asking

- Which invoices are still open in sevDesk?
- What is the balance of my bank accounts in sevDesk?
- Which transactions from this month are not booked yet?

## Install

In Claude, add **Loopthink for sevDesk** from the directory. In Claude Code:

```bash
claude plugin marketplace add loopthink/claude-plugin
```

```bash
claude plugin install loopthink-sevdesk@loopthink-ai
```

Then sign in: run `/mcp`, select `sevdesk`, choose **Authenticate**. A
first sign-in creates a free Loopthink workspace. `/loopthink-sevdesk:get-started`
walks through connecting and the first question.

## What is in this plugin

| Component | Name | What it does |
| --- | --- | --- |
| MCP server | `sevdesk` | Remote connector at `https://mcp.eu.loopthink.ai/mcp/sevdesk`, OAuth 2.0 with PKCE and dynamic client registration |
| Skill | `/loopthink-sevdesk:get-started` | Connect the system, find out why a tool returns nothing, and how to ask |

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

- Setup guide: <https://www.loopthink.ai/connect/sevdesk>
- Support: <https://www.loopthink.ai/support>
- Privacy policy: <https://www.loopthink.ai/privacy-policy>
- Terms: <https://www.loopthink.ai/terms-and-conditions>
- Issues: <https://github.com/loopthink/claude-plugin/issues>

## License

MIT. The license covers this plugin's contents. Use of the Loopthink service is
governed by your Loopthink agreement.
