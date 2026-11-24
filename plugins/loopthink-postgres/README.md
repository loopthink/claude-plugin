# Loopthink for PostgreSQL

Let your whole team ask your PostgreSQL database in plain language, without handing out database passwords or SQL access. Guarded, masked and logged by Loopthink.

Let your whole team ask your PostgreSQL database in plain language, without handing out database passwords or SQL access. Guarded, masked and logged by Loopthink.

Claude explores the schema, writes the query and answers from the rows. Loopthink sits between the two and enforces the rules on every call.

What Loopthink adds on top of the database:
- A guarded query path. Every question runs as one SELECT inside a read-only transaction, capped at 500 rows and 20 seconds. A statement that would change data is refused by the database itself.
- Masking. Rules you set in Loopthink are applied to the rows before they reach Claude, so personal data stays out of the chat.
- Team access without shared passwords. The database is connected once. Every person signs in with their own account, and each member group is granted reading and changing separately.
- An audit log. Every statement is recorded with who ran it.
- Safe changes. Changing data is a separate tool that is switched off until an admin allows it. Then Claude asks before every INSERT, UPDATE or DELETE, one statement per call, UPDATE and DELETE need a WHERE clause, and a statement that would change more than 1000 rows is rolled back.
- No schema changes, ever: no CREATE, ALTER, DROP or TRUNCATE.

What you can ask:
- Which tables are in my database, and what is in them?
- How many orders did we get per month this year?
- Who are our ten largest customers by revenue?
- Which products have not been ordered in the last 90 days?
- Compare this quarter's revenue with the same quarter last year.
- Set the status of order 4711 to shipped.

How it works:
1. Add the app and sign in with Google or Microsoft. Your Loopthink account is created on the spot.
2. Right after sign-in, a form on our page asks for host, port, database, user and password, and whether changes are allowed. We log in once to test it. Credentials are entered there, never in the chat.
3. Ask in Claude. It looks up the tables and columns first, writes one SELECT, and answers from the rows. Nothing needs refreshing after you connect.

Good to know:
- The password is stored encrypted and never shown again. Use a database user with only the rights it needs.
- A workspace admin can change masking, group access and the permission to change data at any time in the Loopthink web app.
- The database has to be reachable from the internet.

## What it can do

- Show which PostgreSQL databases are connected and how to connect one
- List the tables and views of the database
- Describe the columns of a table with their types
- Run one read-only SELECT inside a read-only transaction and return the rows
- Mask personal data in the rows by the workspace's rules before they reach the chat
- Limit rows and run time of every statement, and log it with the person who ran it
- Grant access per member group, reading and changing separately
- Insert, update or delete rows, only where the workspace allowed changes

## Try asking

- Which tables are in my database?
- How many rows does each table have?
- Show me the ten newest entries of the largest table.

## Install

In Claude, add **Loopthink for PostgreSQL** from the directory. In Claude Code:

```bash
claude plugin marketplace add loopthink/claude-plugin
```

```bash
claude plugin install loopthink-postgres@loopthink-ai
```

Then sign in: run `/mcp`, select `postgres`, choose **Authenticate**. A
first sign-in creates a free Loopthink workspace. `/loopthink-postgres:get-started`
walks through connecting and the first question.

## What is in this plugin

| Component | Name | What it does |
| --- | --- | --- |
| MCP server | `postgres` | Remote connector at `https://mcp.eu.loopthink.ai/mcp/postgres`, OAuth 2.0 with PKCE and dynamic client registration |
| Skill | `/loopthink-postgres:get-started` | Connect the system, find out why a tool returns nothing, and how to ask |

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
