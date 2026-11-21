# IMAP by Loopthink

Let your whole team ask a shared mailbox in plain language, without handing out the mailbox password. Read-only by default, masked and logged by Loopthink.

Let your whole team ask a shared mailbox in plain language, without handing out the mailbox password. Read-only by default, masked and logged by Loopthink.

Claude searches the folders, reads the messages and their text attachments, and answers from them. Loopthink sits between the two and enforces the rules on every call.

What Loopthink adds on top of the mailbox:
- Team access without a shared password. The mailbox is connected once. Every person signs in with their own account, and each member group is granted reading and changing separately.
- Reading that leaves no trace. Messages are fetched without setting the read flag, so the inbox looks the same for the people working in it.
- Masking. Sender, recipients, subject and body can be masked per field before they reach Claude.
- An audit log. Every call is recorded with who ran it.
- Guarded changes. Marking as read and moving are separate tools that stay off until an admin allows them. Then Claude asks before each one.
- Hard limits. No tool sends, replies to, forwards or deletes mail. Text attachments are read up to 2 MB.

What you can ask:
- Which unread messages came in today, and what do they want?
- Find the invoices from last month and list sender, date and amount.
- Read the CSV attached to the newest report mail and sum it per country.
- Mark the three order confirmations as read and move them to Processed.

How it works:
1. Add the app and sign in with Google or Microsoft.
2. A form on our page asks for your mailbox: IMAP server, user name, password or app password. We log in once to test it. Credentials are entered there, never in the chat.
3. Ask in Claude.

Good to know:
- Works with Gmail and Microsoft 365 (app password), IONOS, Strato, mailbox.org and any IMAP server reachable from the internet, always over TLS or STARTTLS.
- Best with a shared mailbox such as invoices@ or support@.
- The password is stored encrypted and never shown again.

## What it can do

- Show which mailboxes are connected and how to connect one
- List the folders of a mailbox, with message and unread counts
- Search a folder by sender, recipient, subject, text, date and unread
- Read a message as plain text without marking it as read
- List attachments and read text attachments such as CSV, XML and TXT
- Mask sender, recipients, subject and body by the workspace's rules before they reach the chat
- Grant access per member group, reading and changing separately, and log every call
- Mark as read or move a message, only where the workspace switched that on

## Try asking

- Which unread messages are in my inbox, and what do they want?
- Find the newest message with invoice in the subject and summarise it.
- Which folders does my mailbox have, and how many unread messages are in each?

## Install

In Claude, add **IMAP by Loopthink** from the directory. In Claude Code:

```bash
claude plugin marketplace add loopthink/claude-plugin
```

```bash
claude plugin install loopthink-imap@loopthink-ai
```

Then sign in: run `/mcp`, select `imap`, choose **Authenticate**. A
first sign-in creates a free Loopthink workspace. `/loopthink-imap:get-started`
walks through connecting and the first question.

## What is in this plugin

| Component | Name | What it does |
| --- | --- | --- |
| MCP server | `imap` | Remote connector at `https://mcp.eu.loopthink.ai/chatgpt/imap`, OAuth 2.0 with PKCE and dynamic client registration |
| Skill | `/loopthink-imap:get-started` | Connect the system, find out why a tool returns nothing, and how to ask |

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

- Setup guide: <https://www.loopthink.ai/connect/imap>
- Support: <https://www.loopthink.ai/support>
- Privacy policy: <https://www.loopthink.ai/privacy-policy>
- Terms: <https://www.loopthink.ai/terms-and-conditions>
- Issues: <https://github.com/loopthink/claude-plugin/issues>

## License

MIT. The license covers this plugin's contents. Use of the Loopthink service is
governed by your Loopthink agreement.
