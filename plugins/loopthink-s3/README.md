# Loopthink for S3

Let your whole team ask about the files in your S3 bucket in plain language, without handing out access keys. Confined to one bucket or folder, read-only by default and logged by Loopthink.

Let your whole team ask about the files in your S3 bucket in plain language, without handing out access keys. Confined to one bucket or folder, read-only by default and logged by Loopthink.

Claude lists the folders, reads the objects and answers from their content. Loopthink sits between the two and enforces the rules on every call. Works with Amazon S3 and S3-compatible storage.

What Loopthink adds on top of the bucket:
- Confinement. One connection is one bucket, and it can be locked to a folder (prefix). Nothing outside it can be listed, read or written.
- Team access without shared keys. The bucket is connected once. Every person signs in with their own account, and each member group is granted reading and writing separately.
- An audit log. Every call is recorded with who ran it.
- Guarded changes. Writing, copying, moving and deleting are separate tools that stay off until an admin allows them. Then Claude asks before each one, and an existing object is only replaced when you say so.
- Limits. Text objects are read up to 2 MB, uploads go up to 5 MB. Binary objects are not read.

What you can ask:
- Which exports landed in the reports folder today?
- Read yesterday's CSV export and sum the amounts per country.
- How large is the newest backup, and when was it written?
- Compare the two newest JSON files in the inbound folder.
- Put this summary as a text file into the outbox.

How it works:
1. Add the app and sign in with Google or Microsoft. Your Loopthink account is created on the spot.
2. Right after sign-in, a form on our page asks for your bucket: name, region, an access key ID and secret access key, and whether changes are allowed. We list the bucket once to test it. Credentials are entered there, never in the chat.
3. Ask in Claude. Nothing needs refreshing after you connect.

Amazon S3 and compatible storage:
- Works with Amazon S3 in every region.
- Works with S3-compatible storage through its endpoint, such as Hetzner Object Storage, IONOS, Wasabi, Backblaze B2 and Cloudflare R2.

Good to know:
- Use an IAM user whose policy only reaches this bucket. The setup steps on the form show the policy.
- The secret access key is stored encrypted and never shown again.
- A workspace admin can change the folder, group access and the permission to write at any time in the Loopthink web app.

## What it can do

- Show which S3 buckets are connected and how to connect one
- List a folder of the bucket with name, type, size and last modified time
- Read text objects such as CSV, JSON, XML and logs
- Check size, type and date of an object without reading it
- Keep every call inside the bucket and folder the workspace confined the connection to
- Grant access per member group, reading and writing separately, and log every call
- Write, copy, move or delete an object, only where the workspace switched that on

## Try asking

- Which files are at the top of my S3 bucket?
- Read the newest CSV file in the exports folder and summarise it.
- How large is the newest object in the backups folder?

## Install

In Claude, add **Loopthink for S3** from the directory. In Claude Code:

```bash
claude plugin marketplace add loopthink/claude-plugin
```

```bash
claude plugin install loopthink-s3@loopthink-ai
```

Then sign in: run `/mcp`, select `s3`, choose **Authenticate**. A
first sign-in creates a free Loopthink workspace. `/loopthink-s3:get-started`
walks through connecting and the first question.

## What is in this plugin

| Component | Name | What it does |
| --- | --- | --- |
| MCP server | `s3` | Remote connector at `https://mcp.eu.loopthink.ai/mcp/s3`, OAuth 2.0 with PKCE and dynamic client registration |
| Skill | `/loopthink-s3:get-started` | Connect the system, find out why a tool returns nothing, and how to ask |

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

- Setup guide: <https://www.loopthink.ai/connect/s3>
- Support: <https://www.loopthink.ai/support>
- Privacy policy: <https://www.loopthink.ai/privacy-policy>
- Terms: <https://www.loopthink.ai/terms-and-conditions>
- Issues: <https://github.com/loopthink/claude-plugin/issues>

## License

MIT. The license covers this plugin's contents. Use of the Loopthink service is
governed by your Loopthink agreement.
