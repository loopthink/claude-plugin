# Loopthink plugins for Claude

[Loopthink](https://www.loopthink.ai) is the AI Gateway for teams. You connect
the systems you already run once, and your team reaches them from Claude with
one sign-in each, access per member group, masking on the server and a log of
every call.

This repository holds the Claude plugins for it: one for the whole workspace,
and one per product for people who want exactly that system in Claude.

## Install

```bash
claude plugin marketplace add loopthink/claude-plugin
```

```bash
claude plugin install loopthink@loopthink-ai
```

Replace `loopthink` with any name from the table. Then run `/mcp`, select the
server and choose **Authenticate**.

## Plugins

| Plugin | Name | What it does |
| --- | --- | --- |
| [Loopthink](plugins/loopthink) | `loopthink` | Everything your workspace granted you through one connector, with skills for exploring and querying it |
| [Loopthink for Google Search Console](plugins/loopthink-search-console) | `loopthink-search-console` | Ask Google Search Console in plain language. Queries, pages, clicks and rankings. Read-only, no API key. |
| [Loopthink for Google Ads](plugins/loopthink-google-ads) | `loopthink-google-ads` | Ask Google Ads in plain language. Campaigns, keywords and costs. No API key, no setup. |
| [Loopthink for Google Analytics](plugins/loopthink-google-analytics) | `loopthink-google-analytics` | Ask GA4 in plain language. Sessions, conversions and landing pages. Read-only, no API key. |
| [Loopthink for SFTP](plugins/loopthink-sftp) | `loopthink-sftp` | Let your whole team ask about the files on your SFTP server in plain language, without handing out the login. Confined to one folder, read-only by default and logged by Loopthink. |
| [Loopthink for SSH](plugins/loopthink-ssh) | `loopthink-ssh` | Check and run your Linux servers in plain language. Disk, memory, services, logs and any command. |
| [Loopthink for PostgreSQL](plugins/loopthink-postgres) | `loopthink-postgres` | Let your whole team ask your PostgreSQL database in plain language, without handing out database passwords or SQL access. Guarded, masked and logged by Loopthink. |
| [Loopthink for MySQL](plugins/loopthink-mysql) | `loopthink-mysql` | Ask your MySQL database questions in plain language. Read-only unless you allow changes, with every statement logged. |
| [Loopthink for SQL Server](plugins/loopthink-mssql) | `loopthink-mssql` | Ask your SQL Server database questions in plain language. Read-only unless you allow changes, with every statement logged. |
| [Loopthink for S3](plugins/loopthink-s3) | `loopthink-s3` | Let your whole team ask about the files in your S3 bucket in plain language, without handing out access keys. Confined to one bucket or folder, read-only by default and logged by Loopthink. |
| [Loopthink for Lexware Office](plugins/loopthink-lexware-office) | `loopthink-lexware-office` | Ask about the invoices, quotations, vouchers, contacts and payments in your Lexware Office account in plain language. Read-only unless you allow more. |
| [Loopthink for sevDesk](plugins/loopthink-sevdesk) | `loopthink-sevdesk` | Ask about the invoices, orders, vouchers, contacts and bank transactions in your sevDesk account in plain language. Read-only unless you allow more. |
| [Loopthink for Odoo](plugins/loopthink-odoo) | `loopthink-odoo` | Let your whole team ask your Odoo database in plain language, without giving everyone an Odoo login or an API key. Limited to the models you enable, read-only by default and logged by Loopthink. Odoo 19 and newer. |
| [Loopthink for Shopware](plugins/loopthink-shopware) | `loopthink-shopware` | Ask about the orders, customers, products and stock of your Shopware 6 shop in plain language. Read-only unless you allow more. |
| [Loopthink for IMAP](plugins/loopthink-imap) | `loopthink-imap` | Let your whole team ask a shared mailbox in plain language, without handing out the mailbox password. Read-only by default, masked and logged by Loopthink. |

Each product plugin is one remote MCP connector with a fixed tool list and a
`get-started` skill. None of them ships binaries or runs code on your machine.

## Development

```bash
claude --plugin-dir ./plugins/loopthink
```

```bash
claude plugin validate ./plugins/loopthink
```

## Support

- Website: <https://www.loopthink.ai>
- Issues: <https://github.com/loopthink/claude-plugin/issues>
- Privacy policy: <https://www.loopthink.ai/privacy-policy>

## License

MIT, see [LICENSE](LICENSE). The license covers the plugins' contents. Use of
the Loopthink service is governed by your Loopthink agreement.
