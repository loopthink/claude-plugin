# Loopthink for Shopware

Ask about the orders, customers, products and stock of your Shopware 6 shop in plain language. Read-only unless you allow more.

Ask about the orders, customers, products and stock of your Shopware 6 shop in plain language. Read-only unless you allow more.

What you can ask:
- How many orders came in yesterday, and what was the revenue?
- Which orders are paid but not shipped yet?
- Which products have fewer than ten pieces in stock?
- Who are our ten best customers this year by order value?
- Which promotions are active right now?

How it works:
1. Add the app and sign in with Google or Microsoft. Your Loopthink account is created on the spot.
2. Right after sign-in, a form on our page asks for the address of your shop and the access key ID and secret access key of a Shopware integration (Settings > System > Integrations), and whether changes are allowed. We run one read to test it. Credentials are entered there, never in the chat.
3. Ask in Claude. Nothing needs refreshing after you connect.

Read-only by default:
- Everything is read-only by default: orders, customers, products, stock and promotions are only read.
- Changing an order, payment or delivery state and updating stock stay off unless you tick "Also allow changes" on the form, or an admin allows it later. Claude asks you before each change.
- A state change can send the shop's own mail to the customer. Claude is told to confirm that with you.
- Nothing is ever deleted, and no order or product is created.
- The integration's role in Shopware decides what can be read. A role with view rights only is the safest choice.
- Works with Shopware 6.4 and newer, self-hosted or cloud. The shop has to be reachable over HTTPS.

Built for teams:
- Every person signs in with their own account.
- Access is granted per member group, reading and writing separately.
- Every call is logged with who ran it.

## What it can do

- Show whether Shopware is connected and how to connect it
- Search orders with filters, sorting and aggregations, and read one with line items
- List the documents of an order
- Search customers and products, and read stock levels
- List categories, manufacturers, sales channels, promotions and reviews
- Change an order, payment or delivery state or a stock figure, only where the workspace switched that on

## Try asking

- How many orders did my Shopware shop get yesterday?
- Which Shopware orders are paid but not shipped yet?
- Which products are low in stock in Shopware?

## Install

In Claude, add **Loopthink for Shopware** from the directory. In Claude Code:

```bash
claude plugin marketplace add loopthink/claude-plugin
```

```bash
claude plugin install loopthink-shopware@loopthink-ai
```

Then sign in: run `/mcp`, select `shopware`, choose **Authenticate**. A
first sign-in creates a free Loopthink workspace. `/loopthink-shopware:get-started`
walks through connecting and the first question.

## What is in this plugin

| Component | Name | What it does |
| --- | --- | --- |
| MCP server | `shopware` | Remote connector at `https://mcp.eu.loopthink.ai/mcp/shopware`, OAuth 2.0 with PKCE and dynamic client registration |
| Skill | `/loopthink-shopware:get-started` | Connect the system, find out why a tool returns nothing, and how to ask |

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

- Setup guide: <https://www.loopthink.ai/connect/shopware-6>
- Support: <https://www.loopthink.ai/support>
- Privacy policy: <https://www.loopthink.ai/privacy-policy>
- Terms: <https://www.loopthink.ai/terms-and-conditions>
- Issues: <https://github.com/loopthink/claude-plugin/issues>

## License

MIT. The license covers this plugin's contents. Use of the Loopthink service is
governed by your Loopthink agreement.
