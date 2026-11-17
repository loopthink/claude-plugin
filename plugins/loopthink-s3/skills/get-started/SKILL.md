---
name: get-started
description: Set up S3 by Loopthink or work out why it returns no objects. Use when the user has just added the app, asks what it can do, gets a "connect it at …" message, or a tool says it is not switched on.
---

# Get started with S3 by Loopthink

The app reads the S3 buckets the user connected in Loopthink, and only the
ones their member group was granted. The tools are always the same:

- `connection_status`: which buckets are connected, and the link to connect one
- `s3_list_objects`: the entries of a folder
- `s3_get_object_info`: size, type and date of one object
- `s3_get_object`: the content of a text object
- `s3_put_object`, `s3_copy_object`, `s3_move_object`, `s3_delete_object`:
  changes, only where the workspace switched them on for the bucket

## 1. Find out what is connected

Call `connection_status`.

- **`connected: true`.** Call `s3_list_objects` with an empty `path` for the top
  of the bucket. With more than one bucket, pass its name as `server`.
- **`connected: false`.** Give the user the `connectUrl` and continue with step 2.

## 2. Connect a bucket

Send the user to the link. Never ask for an access key in the chat:
credentials are entered on the Loopthink page only.

The page asks for the bucket name, its region, an access key ID and secret
access key, and optionally a folder (prefix) the app is confined to. For
S3-compatible storage it also takes the provider's endpoint. Loopthink lists
the bucket once to test it.

Then ask the question again. The tools do not change, so nothing needs
refreshing or reconnecting in Claude.

## 3. A tool says it is not switched on

Writing, copying, moving and deleting are off on every new bucket. A workspace
admin turns each one on in the Loopthink web app and grants it to the member
group. Pass the link from the message on to the user.

## Notes for answering

- All paths are relative to the folder the bucket is confined to. An empty path
  is the top; nothing outside exists for the app.
- A listing is one folder level. Long folders come in pages: pass
  `next_continuation_token` on as `continuation_token`.
- Check the size with `s3_get_object_info` before reading a large object. Only
  text is read; a binary object answers with its type and size.
- Confirm every write, copy, move and delete with the user first. Pass
  `overwrite: true` only when the user asked to replace the object.
