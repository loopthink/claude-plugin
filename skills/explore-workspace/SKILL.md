---
name: explore-workspace
description: Map what a Loopthink workspace exposes — which MCP servers, tables, CRM entities and tools are reachable — before querying it. Use when the user asks what data or tools Loopthink gives them access to, what is in a connected database or CRM, or when you need to find the right Loopthink tool for a question.
---

# Explore a Loopthink workspace

Loopthink aggregates several MCP servers behind one connector. Before answering a
data question, find out what is actually reachable — guessing table or entity
names wastes tool calls against systems whose schema you cannot see.

## Read the tool names first

Every tool is `{serverKey}__{toolName}`. The prefix tells you which backend it
belongs to, and the tool set tells you what kind of backend it is:

| Pattern you see | What it usually means |
| --- | --- |
| `listTables`, `*_scan`, `*_query`, `*_get` | A database server. One `scan`/`query`/`get` trio per table. |
| `search_*`, `get_*` on entity nouns | A CRM server (HubSpot, Salesforce). One set per enabled entity. |
| Verb-shaped, domain-specific names | Authored tools — a curated SQL statement or HTTP call an admin wrote by hand. |

Grouping the tool list by prefix is usually enough to describe the workspace. Do
that from the tool list you already have rather than calling anything.

## Then use the discovery tools

Database servers expose a discovery tool (commonly `listTables`) — call it before
any table-level tool so you use the real table names and key attributes. For CRM
servers, the enabled entities are visible from the tool names themselves.

Read tool descriptions carefully. Authored tools often encode business meaning
that the name alone does not ("active customers" may mean a specific status
filter), and their parameters are typed and validated server-side.

## Reporting back

When the user asks what they have access to, give them the shape, not a raw dump:

- One line per MCP server: what backend it is and what it covers.
- The tables or entities under each, by their real names.
- Anything conspicuously absent that they might expect, with the reason from
  the `connect` skill — a missing server is a missing grant, not a missing tool.

## Do not

- Do not infer a table exists because a related one does. Call the discovery tool.
- Do not describe masked fields as empty or missing. They exist; the policy hides
  their values.
- Do not enumerate every tool parameter unless asked — it buries the answer.
