---
name: get-started
description: Set up Loopthink for SFTP or work out why it returns no files. Use when the user has just added the app, asks what it can do, gets a "connect it at …" message, or a file tool says it is not switched on.
---

# Get started with Loopthink for SFTP

The app reads the SFTP servers the user connected in Loopthink, and only the
ones their member group was granted. The tools are always the same:

- `connection_status`: which SFTP servers are connected, and the link to connect one
- `sftp_list_dir`: the entries of a folder
- `sftp_get_file_info`: size, date and permissions of one file or folder
- `sftp_get_file`: the content of a file
- `sftp_put_file`, `sftp_move_file`, `sftp_delete_file`: changes, only where the
  workspace switched them on for the server

## 1. Find out what is connected

Call `connection_status`.

- **`connected: true`.** Call `sftp_list_dir` with an empty `path` for the root
  folder. With more than one server, pass its name as `server`.
- **`connected: false`.** Give the user the `connectUrl` and continue with step 2.

## 2. Connect an SFTP server

Send the user to the link. Never ask for a host, password or key in the chat:
credentials are entered in the Loopthink web app only.

1. Sign in to Loopthink and add SFTP.
2. Enter host, port, user name and the password or private key, and optionally
   the root folder the app is confined to.
3. Run "Test connection" and compare the host key fingerprint.

Then ask the question again. The tools do not change, so nothing needs
refreshing or reconnecting in Claude.

## 3. A tool says it is not switched on

Writing, moving and deleting are off on every new server. A workspace admin
turns each one on for the server in the Loopthink web app and grants it to the
member group. Pass the link from the message on to the user.

## Notes for answering

- All paths are relative to the root folder of the server. An empty path is
  the root itself; paths above it do not exist for the app.
- Check the size with `sftp_get_file_info` before reading a large file. Text is
  cut at `max_bytes` and marked `truncated: true`.
- Confirm every write, move and delete with the user first. Pass
  `overwrite: true` only when the user asked to replace the file.
- The server has to be reachable from the internet.
