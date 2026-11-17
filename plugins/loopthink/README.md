# Loopthink for Claude Code

Governed access to your company's databases, CRMs and internal APIs — from inside
Claude Code.

[Loopthink](https://www.loopthink.ai) is an MCP control plane. Admins connect
systems once, curate which tools each one exposes, and grant them to member
groups. This plugin bundles the resulting connector plus the skills Claude needs
to use it well: what a workspace exposes, how to query it without scanning a
production table, and what to do when a masked field or a missing grant shows up.

One OAuth sign-in, no API keys, no per-system setup.

## Install

```bash
claude plugin marketplace add loopthink/claude-plugin
```

```bash
claude plugin install loopthink@loopthink-ai
```

Then authenticate: run `/mcp`, select `loopthink`, choose **Authenticate**, sign
in, and pick a workspace. Ask Claude to *"set up Loopthink"* and it will walk you
through it.

Full walkthrough: <https://www.loopthink.ai/connect/claude>

## What you get

| Component | Name | What it does |
| --- | --- | --- |
| MCP server | `loopthink` | Streamable-HTTP connector at `https://mcp.eu.loopthink.ai/mcp`, OAuth 2.0 with PKCE and dynamic client registration |
| Skill | `/loopthink:connect` | Connect, switch workspace, and diagnose an empty tool list |
| Skill | `/loopthink:explore-workspace` | Map the servers, tables, entities and tools you can reach |
| Skill | `/loopthink:query-data` | Access patterns, pagination, cross-system joins, masked fields |
| Subagent | `loopthink:data-analyst` | Runs multi-step data questions in its own context and returns the finding |

Tools arrive namespaced as `{serverKey}__{toolName}` — the prefix identifies which
MCP server in your workspace they belong to, so `orders__get_order` and
`crm__search_contacts` can coexist.

## Requirements

- Claude Code v2.1.143 or later
- A Loopthink account and membership in at least one workspace
- Your member group granted access to at least one MCP server in that workspace

That last one matters: the connector publishes only what the signed-in user's
member group was granted, with **no owner or admin bypass**. A workspace owner
with no group grant sees zero tools. If your tool list is empty after a successful
sign-in, that is where to look first — `/loopthink:connect` has the runbook.

## Security and data handling

- **Authentication.** OAuth 2.0 with PKCE and dynamic client registration. You
  sign in at `mcp.eu.loopthink.ai`; Claude Code never sees your credentials.
  Tokens are short-lived, scoped to a single workspace, and re-validate your
  permissions on every refresh — a revoked grant takes effect within one token
  lifetime.
- **Least privilege.** Claude sees only the tools your member group was granted,
  optionally narrowed to a subset per group.
- **Masking.** Field-level masking rules run server-side, before results are
  returned. Masked values never reach the model, and the bundled skills instruct
  Claude not to attempt to route around them.
- **Read-only by default.** Tools are read-only unless a workspace admin
  explicitly enabled writes.
- **Data residency.** Loopthink runs in the AWS European Sovereign Cloud — EU
  region, EU operations, EU personnel.
- **No local execution.** This plugin ships no binaries and runs no code on your
  machine. It contributes one remote MCP endpoint, three skills, and one subagent
  definition. Nothing here reads or writes outside the plugin directory.

The `loopthink:data-analyst` subagent is restricted to `Read`, `Write`, and the
`loopthink` MCP tools — it has no shell access.

Privacy policy: <https://www.loopthink.ai/privacy-policy>

## Development

Run against a local checkout without installing:

```bash
claude --plugin-dir ./plugins/loopthink
```

Validate before pushing:

```bash
claude plugin validate ./plugins/loopthink --strict
```

To point the connector at a different environment (a staging workspace, or a
regional deployment other than the EU one), edit the `url` in `.mcp.json`.

## Support

- Setup guide — <https://www.loopthink.ai/connect/claude>
- Issues — <https://github.com/loopthink/claude-plugin/issues>
- Imprint and contact — <https://www.loopthink.ai/imprint>

## License

MIT — see [LICENSE](LICENSE). The license covers this plugin's contents. Use of
the Loopthink service itself is governed by your Loopthink agreement.
