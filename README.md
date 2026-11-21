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
| [Google Search Console by Loopthink](plugins/loopthink-search-console) | `loopthink-search-console` | Ask Google Search Console in plain language. Queries, pages, clicks and rankings. Read-only, no API key. |
| [Google Ads by Loopthink](plugins/loopthink-google-ads) | `loopthink-google-ads` | Ask Google Ads in plain language. Campaigns, keywords and costs. No API key, no setup. |
| [Google Analytics by Loopthink](plugins/loopthink-google-analytics) | `loopthink-google-analytics` | Ask GA4 in plain language. Sessions, conversions and landing pages. Read-only, no API key. |
| [SFTP by Loopthink](plugins/loopthink-sftp) | `loopthink-sftp` | Browse and read the files on your SFTP server in plain language. Uploads only where you allow them. |
| [SSH by Loopthink](plugins/loopthink-ssh) | `loopthink-ssh` | Check and run your Linux servers in plain language. Disk, memory, services, logs and any command. |
| [PostgreSQL by Loopthink](plugins/loopthink-postgres) | `loopthink-postgres` | Ask your PostgreSQL database questions in plain language. Read-only unless you allow changes, with every statement logged. |
| [MySQL by Loopthink](plugins/loopthink-mysql) | `loopthink-mysql` | Ask your MySQL database questions in plain language. Read-only unless you allow changes, with every statement logged. |
| [SQL Server by Loopthink](plugins/loopthink-mssql) | `loopthink-mssql` | Ask your SQL Server database questions in plain language. Read-only unless you allow changes, with every statement logged. |
| [S3 by Loopthink](plugins/loopthink-s3) | `loopthink-s3` | Browse and read the objects in your S3 bucket in plain language. Amazon S3 and S3-compatible storage. Uploads only where you allow them. |
| [Lexware Office by Loopthink](plugins/loopthink-lexware-office) | `loopthink-lexware-office` | Ask about the invoices, quotations, vouchers, contacts and payments in your Lexware Office account in plain language. Read-only unless you allow more. |
| [sevDesk by Loopthink](plugins/loopthink-sevdesk) | `loopthink-sevdesk` | Ask about the invoices, orders, vouchers, contacts and bank transactions in your sevDesk account in plain language. Read-only unless you allow more. |
| [Odoo by Loopthink](plugins/loopthink-odoo) | `loopthink-odoo` | Ask about the contacts, sales, invoices, stock, CRM and projects in your Odoo database in plain language. Read-only unless you allow more. Odoo 19 and newer. |
| [Shopware by Loopthink](plugins/loopthink-shopware) | `loopthink-shopware` | Ask about the orders, customers, products and stock of your Shopware 6 shop in plain language. Read-only unless you allow more. |
| [IMAP by Loopthink](plugins/loopthink-imap) | `loopthink-imap` | Let your whole team ask a shared mailbox in plain language, without handing out the mailbox password. Read-only by default, masked and logged by Loopthink. |

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
