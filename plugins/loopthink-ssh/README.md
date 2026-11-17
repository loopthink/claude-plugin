# SSH by Loopthink

Check and run your Linux servers in plain language. Disk, memory, services, logs and any command.

Check and run your Linux servers in plain language. Disk, memory, services, logs and any command.

What you can ask:
- Is the disk on my server filling up?
- Is nginx running, and what do its last log lines say?
- Which processes use the most CPU right now?
- Show the last 200 lines of /var/log/nginx/error.log and group the errors.
- How long has the server been up, and what is the load?
- Restart nginx and show me its status afterwards.

How it works:
1. Add the app and sign in with Google or Microsoft. Your Loopthink account is created on the spot.
2. Right after sign-in, a form on our page asks for your server: host, user name and a password or private key. We log in once to test it. Credentials are entered there, never in the chat.
3. Ask in Claude. Nothing needs refreshing after you connect.

Fixed tools and a free command:
- Seven fixed commands for the usual questions: uname and uptime, df, free, ps, systemctl status, tail and ls. Their values are checked against a pattern or an allow-list and quoted.
- Any other command runs through ssh_run_command. Claude asks you before each one.
- Every command runs as the user you connected, with exactly its rights. Use a user of its own.
- An admin can switch ssh_run_command off for a server in Loopthink.
- The server's host key is pinned on the first connection, and a changed key blocks every call until an admin confirms it.

Built for teams:
- Every person signs in with their own account.
- Access is granted per member group and per tool.
- Every call is logged with who ran it and the exact command.

## What it can do

- Show which servers are connected and how to connect one
- Kernel, distribution, uptime and load of a host
- Disk space of every mounted file system, and memory and swap
- The processes using the most CPU
- State and recent log lines of a systemd service
- The last lines of a log file under /var/log
- Runs any command as the connected user, after you confirm it

## Try asking

- Is the disk on my server filling up?
- Is nginx running, and what do its last log lines say?
- Which processes use the most CPU right now?

## Install

In Claude, add **SSH by Loopthink** from the directory. In Claude Code:

```bash
claude plugin marketplace add loopthink/claude-plugin
```

```bash
claude plugin install loopthink-ssh@loopthink-ai
```

Then sign in: run `/mcp`, select `ssh`, choose **Authenticate**. A
first sign-in creates a free Loopthink workspace. `/loopthink-ssh:get-started`
walks through connecting and the first question.

## What is in this plugin

| Component | Name | What it does |
| --- | --- | --- |
| MCP server | `ssh` | Remote connector at `https://mcp.eu.loopthink.ai/chatgpt/ssh`, OAuth 2.0 with PKCE and dynamic client registration |
| Skill | `/loopthink-ssh:get-started` | Connect the system, find out why a tool returns nothing, and how to ask |

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

- Setup guide: <https://www.loopthink.ai/connect/ssh>
- Support: <https://www.loopthink.ai/support>
- Privacy policy: <https://www.loopthink.ai/privacy-policy>
- Terms: <https://www.loopthink.ai/terms-and-conditions>
- Issues: <https://github.com/loopthink/claude-plugin/issues>

## License

MIT. The license covers this plugin's contents. Use of the Loopthink service is
governed by your Loopthink agreement.
