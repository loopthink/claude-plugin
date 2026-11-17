# Changelog

All notable changes to this plugin are documented here. This project adheres to
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## 2026-11-17

The repository now holds one plugin per folder under `plugins/`.

- `loopthink` 0.2.0: moved to `plugins/loopthink`, description and links follow
  the current listing. Skills, subagent and connector URL are unchanged.
- New, one per product, each with its own connector and a `get-started` skill:
  `loopthink-search-console`, `loopthink-google-ads`, `loopthink-google-analytics`,
  `loopthink-sftp`, `loopthink-ssh`, `loopthink-postgres`, `loopthink-mysql`,
  `loopthink-mssql`, `loopthink-s3`, `loopthink-lexware-office`,
  `loopthink-sevdesk`, `loopthink-odoo`, `loopthink-shopware`.

## [0.1.0] — 2026-08-07

Initial release.

- `loopthink` MCP server — streamable-HTTP connector at
  `https://mcp.eu.loopthink.ai/mcp`, OAuth 2.0 with PKCE and dynamic client
  registration, scoped to one workspace per connection.
- `/loopthink:connect` — connect, switch workspace, and diagnose an empty tool
  list.
- `/loopthink:explore-workspace` — map reachable MCP servers, tables, entities
  and tools.
- `/loopthink:query-data` — access patterns, pagination, cross-system joins, and
  handling of masked fields.
- `loopthink:data-analyst` subagent — multi-step data questions in an isolated
  context, restricted to `Read`, `Write` and the `loopthink` MCP tools.
- `SETUP.md` — setup guidance Claude follows after install.

[0.1.0]: https://github.com/loopthink/claude-plugin/releases/tag/v0.1.0
