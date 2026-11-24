# Loopthink for Odoo

Let your whole team ask your Odoo database in plain language, without giving everyone an Odoo login or an API key. Limited to the models you enable, read-only by default and logged by Loopthink. Odoo 19 and newer.

Let your whole team ask your Odoo database in plain language, without giving everyone an Odoo login or an API key. Limited to the models you enable, read-only by default and logged by Loopthink. Odoo 19 and newer.

Claude looks up the models and fields, searches the records and answers from them: contacts, sales, invoices, stock, CRM and projects. Loopthink sits between the two and enforces the rules on every call.

What Loopthink adds on top of Odoo:
- A model allow-list. The app only reaches the models enabled for the server, 15 common ones to start with. An admin adds or removes models in Loopthink, and a model that is not enabled answers with a notice.
- Team access without shared keys. Odoo is connected once. Every person signs in with their own account, and each member group is granted reading and writing separately.
- An audit log. Every call is recorded with who ran it.
- Guarded changes. Creating and updating records are separate tools that stay off until an admin allows them. Then Claude asks before each change. Nothing is ever deleted.
- Masking. Fields with personal data can be masked per server before they reach the chat.

What you can ask:
- Which sales orders were confirmed this week, and what is their total?
- Which customer invoices are posted but not paid?
- Which products are below five pieces in stock?
- How many open leads does each salesperson have?
- How many hours were logged on project Website Relaunch this month?

How it works:
1. Add the app and sign in with Google or Microsoft. Your Loopthink account is created on the spot.
2. Right after sign-in, a form on our page asks for the address of your Odoo and an API key (in Odoo under My Preferences > Account Security > New API Key), and whether changes are allowed. We run one read to test it. Credentials are entered there, never in the chat.
3. Ask in Claude. Nothing needs refreshing after you connect.

Good to know:
- The API key carries the access rights and record rules of its Odoo user. A user of its own with only the apps it needs is the safest choice.
- The API key is stored encrypted and never shown again.
- Needs Odoo 19 or newer (JSON-2 API). On Odoo Online the external API is part of the Custom plan.

## What it can do

- Show whether Odoo is connected and how to connect it
- List the enabled models and the fields of each
- Search records of a model with an Odoo domain and chosen fields
- Count records for totals
- Read records by id, and list the companies of the database
- Reach only the models the workspace enabled for the server
- Grant access per member group, reading and writing separately, and log every call
- Create or update records, only where the workspace switched that on

## Try asking

- Which sales orders were confirmed in Odoo this week?
- Which customer invoices in Odoo are still unpaid?
- Which products are low in stock in Odoo?

## Install

In Claude, add **Loopthink for Odoo** from the directory. In Claude Code:

```bash
claude plugin marketplace add loopthink/claude-plugin
```

```bash
claude plugin install loopthink-odoo@loopthink-ai
```

Then sign in: run `/mcp`, select `odoo`, choose **Authenticate**. A
first sign-in creates a free Loopthink workspace. `/loopthink-odoo:get-started`
walks through connecting and the first question.

## What is in this plugin

| Component | Name | What it does |
| --- | --- | --- |
| MCP server | `odoo` | Remote connector at `https://mcp.eu.loopthink.ai/mcp/odoo`, OAuth 2.0 with PKCE and dynamic client registration |
| Skill | `/loopthink-odoo:get-started` | Connect the system, find out why a tool returns nothing, and how to ask |

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

- Setup guide: <https://www.loopthink.ai/connect/odoo>
- Support: <https://www.loopthink.ai/support>
- Privacy policy: <https://www.loopthink.ai/privacy-policy>
- Terms: <https://www.loopthink.ai/terms-and-conditions>
- Issues: <https://github.com/loopthink/claude-plugin/issues>

## License

MIT. The license covers this plugin's contents. Use of the Loopthink service is
governed by your Loopthink agreement.
