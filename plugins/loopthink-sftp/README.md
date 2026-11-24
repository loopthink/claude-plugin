# Loopthink for SFTP

Let your whole team ask about the files on your SFTP server in plain language, without handing out the login. Confined to one folder, read-only by default and logged by Loopthink.

Let your whole team ask about the files on your SFTP server in plain language, without handing out the login. Confined to one folder, read-only by default and logged by Loopthink.

Claude lists the folders, reads the files and answers from their content. Loopthink sits between the two and enforces the rules on every call.

What Loopthink adds on top of the server:
- Confinement. The connection is locked to one root folder. Nothing above it can be listed, read or written, whatever the SFTP user itself could reach.
- Team access without a shared login. The server is connected once. Every person signs in with their own account, and each member group is granted reading and writing separately.
- An audit log. Every call is recorded with who ran it.
- Guarded changes. Writing, moving and deleting are separate tools that stay off until an admin allows them. Then Claude asks before each one, and an existing file is only replaced when you say so.
- A pinned host key. The key is pinned on the first connection, and a changed key blocks every call until an admin confirms it.
- Limits. Text files are read up to 2 MB, uploads go up to 5 MB.

What you can ask:
- Which files arrived in the inbound folder today?
- Read yesterday's statement and sum the amounts per account.
- How large is the export from last night, and when was it written?
- Compare the two newest CSV files in the outbox.
- Put this order as XML into the outbound folder.

How it works:
1. Add the app and sign in with Google or Microsoft. Your Loopthink account is created on the spot.
2. Right after sign-in, a form on our page asks for your SFTP server: host, user name, a password or private key, and whether changes are allowed. We log in once to test it. Credentials are entered there, never in the chat.
3. Ask in Claude. Nothing needs refreshing after you connect.

Good to know:
- The password or key is stored encrypted and never shown again.
- A workspace admin can change the root folder, group access and the permission to write at any time in the Loopthink web app.

## What it can do

- Show which SFTP servers are connected and how to connect one
- List a folder with name, type, size and last modified time
- Read text files such as CSV, XML, JSON, MT940 and logs
- Check size, date and permissions of a file without reading it
- Keep every call inside the root folder the workspace confined the server to
- Grant access per member group, reading and writing separately, and log every call
- Write, move or delete a file, only where the workspace switched that on

## Try asking

- Which files are in the root folder of my SFTP server?
- Read the newest CSV file in the inbound folder and summarise it.
- How large is the newest file in the outbox, and when was it written?

## Install

In Claude, add **Loopthink for SFTP** from the directory. In Claude Code:

```bash
claude plugin marketplace add loopthink/claude-plugin
```

```bash
claude plugin install loopthink-sftp@loopthink-ai
```

Then sign in: run `/mcp`, select `sftp`, choose **Authenticate**. A
first sign-in creates a free Loopthink workspace. `/loopthink-sftp:get-started`
walks through connecting and the first question.

## What is in this plugin

| Component | Name | What it does |
| --- | --- | --- |
| MCP server | `sftp` | Remote connector at `https://mcp.eu.loopthink.ai/mcp/sftp`, OAuth 2.0 with PKCE and dynamic client registration |
| Skill | `/loopthink-sftp:get-started` | Connect the system, find out why a tool returns nothing, and how to ask |

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

- Setup guide: <https://www.loopthink.ai/connect/sftp>
- Support: <https://www.loopthink.ai/support>
- Privacy policy: <https://www.loopthink.ai/privacy-policy>
- Terms: <https://www.loopthink.ai/terms-and-conditions>
- Issues: <https://github.com/loopthink/claude-plugin/issues>

## License

MIT. The license covers this plugin's contents. Use of the Loopthink service is
governed by your Loopthink agreement.
