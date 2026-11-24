# Loopthink for MySQL

Ask your MySQL database questions in plain language. Read-only unless you allow changes, with every statement logged.

Ask your MySQL database questions in plain language. Read-only unless you allow changes, with every statement logged.

What you can ask:
- Which tables are in my database, and what is in them?
- How many orders did we get per month this year?
- Who are our ten largest customers by revenue?
- Which products have not been ordered in the last 90 days?
- Compare this quarter's revenue with the same quarter last year.
- Set the status of order 4711 to shipped.

How it works:
1. Add the app and sign in with Google or Microsoft. Your Loopthink account is created on the spot.
2. Right after sign-in, a form on our page asks for host, port, database, user and password. We log in once to test it. Credentials are entered there, never in the chat.
3. Ask in Claude. It looks up the tables and columns, writes one SELECT, and answers from the rows.

Read-only by default:
- Every query runs inside a read-only transaction. A statement that would change data is refused by the database itself.
- Changing data is a separate tool that is switched off. It only works after you tick "Also allow changes" when connecting, or a workspace admin allows it later.
- With changes allowed, Claude asks you before every INSERT, UPDATE or DELETE. One statement per call, UPDATE and DELETE need a WHERE clause, and a statement that would change more than 1000 rows is rolled back.
- The schema cannot be changed: no CREATE, ALTER, DROP or TRUNCATE.
- At most 500 rows come back per query, and a query is stopped after 20 seconds.
- The password is stored encrypted and never shown again. Use a database user with only the rights it needs.
- Masking rules set in Loopthink are applied before rows reach Claude.

Built for teams:
- Every person signs in with their own account.
- Access is granted per member group, reading and changing separately.
- Every statement is logged with who ran it.

## What it can do

- Show which MySQL databases are connected and how to connect one
- List the tables and views of the database
- Describe the columns of a table with their types
- Run one read-only SELECT and return the rows
- Insert, update or delete rows, only where the workspace allowed changes
- Limits rows and run time of every statement

## Try asking

- Which tables are in my database?
- How many rows does each table have?
- Show me the ten newest entries of the largest table.

## Install

In Claude, add **Loopthink for MySQL** from the directory. In Claude Code:

```bash
claude plugin marketplace add loopthink/claude-plugin
```

```bash
claude plugin install loopthink-mysql@loopthink-ai
```

Then sign in: run `/mcp`, select `mysql`, choose **Authenticate**. A
first sign-in creates a free Loopthink workspace. `/loopthink-mysql:get-started`
walks through connecting and the first question.

## What is in this plugin

| Component | Name | What it does |
| --- | --- | --- |
| MCP server | `mysql` | Remote connector at `https://mcp.eu.loopthink.ai/mcp/mysql`, OAuth 2.0 with PKCE and dynamic client registration |
| Skill | `/loopthink-mysql:get-started` | Connect the system, find out why a tool returns nothing, and how to ask |

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

- Setup guide: <https://www.loopthink.ai>
- Support: <https://www.loopthink.ai/support>
- Privacy policy: <https://www.loopthink.ai/privacy-policy>
- Terms: <https://www.loopthink.ai/terms-and-conditions>
- Issues: <https://github.com/loopthink/claude-plugin/issues>

## License

MIT. The license covers this plugin's contents. Use of the Loopthink service is
governed by your Loopthink agreement.
