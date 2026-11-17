# S3 by Loopthink

Browse and read the objects in your S3 bucket in plain language. Amazon S3 and S3-compatible storage. Uploads only where you allow them.

Browse and read the objects in your S3 bucket in plain language. Amazon S3 and S3-compatible storage. Uploads only where you allow them.

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

Confined and read-only by default:
- One connection is one bucket. It can be confined to a folder (prefix); nothing outside it can be listed, read or written.
- Listing and reading work right away. Writing, copying, moving and deleting stay off unless you tick "Also allow changes" on the form, or an admin allows them later.
- Claude asks you before an object is written, copied, moved or deleted. An existing object is only replaced when you say so.
- Use an IAM user whose policy only reaches this bucket. The setup steps on the form show the policy.
- Text objects are read up to 2 MB, uploads go up to 5 MB. Binary objects are not read.

Amazon S3 and compatible storage:
- Works with Amazon S3 in every region.
- Works with S3-compatible storage through its endpoint, such as Hetzner Object Storage, IONOS, Wasabi, Backblaze B2 and Cloudflare R2.

Built for teams:
- Every person signs in with their own account.
- Access is granted per member group, reading and writing separately.
- Every call is logged with who ran it.

## What it can do

- Show which S3 buckets are connected and how to connect one
- List a folder of the bucket with name, type, size and last modified time
- Read text objects such as CSV, JSON, XML and logs
- Check size, type and date of an object without reading it
- Write, copy, move or delete an object, only where the workspace switched that on
- Stays inside the bucket and the folder the connection is confined to

## Try asking

- Which files are at the top of my S3 bucket?
- Read the newest CSV file in the exports folder and summarise it.
- How large is the newest object in the backups folder?

## Install

In Claude, add **S3 by Loopthink** from the directory. In Claude Code:

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
| MCP server | `s3` | Remote connector at `https://mcp.eu.loopthink.ai/chatgpt/s3`, OAuth 2.0 with PKCE and dynamic client registration |
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
