# SFTP by Loopthink

Browse and read the files on your SFTP server in plain language. Uploads only where you allow them.

Browse and read the files on your SFTP server in plain language. Uploads only where you allow them.

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

Confined and read-only by default:
- The server is confined to one root folder. Nothing above it can be read or written.
- Listing and reading work right away. Writing, moving and deleting stay off unless you tick "Also allow changes" on the form, or an admin allows them later.
- Claude asks you before a file is written, moved or deleted. An existing file is only replaced when you say so.
- The server's host key is pinned on the first connection. A changed key blocks every call until an admin confirms it.
- Text files are read up to 2 MB, uploads go up to 5 MB.

Built for teams:
- Every person signs in with their own account.
- Access is granted per member group, reading and writing separately.
- Every call is logged with who ran it.

## What it can do

- Show which SFTP servers are connected and how to connect one
- List a folder with name, type, size and last modified time
- Read text files such as CSV, XML, JSON, MT940 and logs
- Check size, date and permissions of a file without reading it
- Write, move or delete a file, only where the workspace switched that on
- Stays inside the root folder the server is confined to

## Try asking

- Which files are in the root folder of my SFTP server?
- Read the newest CSV file in the inbound folder and summarise it.
- How large is the newest file in the outbox, and when was it written?

## Install

In Claude, add **SFTP by Loopthink** from the directory. In Claude Code:

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
| MCP server | `sftp` | Remote connector at `https://mcp.eu.loopthink.ai/chatgpt/sftp`, OAuth 2.0 with PKCE and dynamic client registration |
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
