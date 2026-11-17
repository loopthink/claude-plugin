---
name: get-started
description: Set up SSH by Loopthink or work out why it returns nothing. Use when the user has just added the app, asks what it can do, gets a "connect it at …" message, or asks for a command the fixed tools do not cover.
---

# Get started with SSH by Loopthink

The app checks the Linux servers the user connected in Loopthink, and only the
ones their member group was granted. The tools are always the same. All but
the last run one fixed, read-only command:

- `connection_status`: which servers are connected, and the link to connect one
- `ssh_system_info`: kernel, distribution, uptime and load
- `ssh_disk_usage`: space of every mounted file system
- `ssh_memory_usage`: memory and swap
- `ssh_top_processes`: the processes using the most CPU
- `ssh_service_status`: state and last log lines of a systemd service
- `ssh_tail_log`: the last lines of a log file under /var/log
- `ssh_list_dir`: the entries of a folder
- `ssh_run_command`: any command as the connected user

## 1. Find out what is connected

Call `connection_status`.

- **`connected: true`.** `ssh_system_info` is a good first look. With more than
  one server, pass its name as `server`.
- **`connected: false`.** Give the user the `connectUrl` and continue with step 2.

## 2. Connect a server

Send the user to the link. Never ask for a host, password or key in the chat:
credentials are entered in the Loopthink web app only.

1. Sign in to Loopthink and add SSH.
2. Enter host, port, user name and the private key or password. The user's
   own rights are all any command gets, so a user of its own is best.
3. We log in once to test it.

Then ask the question again. The tools do not change, so nothing needs
refreshing or reconnecting in Claude.

## 3. Running a command

- Prefer the fixed tools when they answer the question.
- Say what a command will do before running one that changes the server
  (restart, install, delete, edit). Claude asks the user before every call.
- Commands run without a terminal. Editors, pagers, `top` without `-b` and
  password prompts hang until the 20 s limit, so use non-interactive forms
  (`top -bn1`, `sudo -n`, `--no-pager`).
- An answer that the server "only reads" means an admin switched commands off
  for it. A workspace admin allows them again in the server's settings.
- A tool that answers "not switched on" was disabled for that server by a
  workspace admin, or not granted to the member group.
- The server has to be reachable from the internet.

## Notes for answering

- `ssh_service_status`: exit code 3 means the service is not running, 4 that it
  does not exist.
- The first line of `ssh_top_processes` is the header.
