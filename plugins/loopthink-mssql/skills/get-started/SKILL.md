---
name: get-started
description: Set up SQL Server by Loopthink or work out why it returns no rows. Use when the user has just added the app, asks what it can do, gets a "connect it at …" message, or a tool says it is not switched on.
---

# Get started with SQL Server by Loopthink

The app reads the SQL Server databases the user connected in Loopthink, and only
the ones their member group was granted. The tools are always the same:

- `connection_status`: which databases are connected, and the link to connect one
- `mssql_list_tables`: the tables and views
- `mssql_describe_table`: the columns of one table
- `mssql_query`: one SELECT, checked and always rolled back, returning rows
- `mssql_execute`: one INSERT, UPDATE or DELETE, only where the workspace
  allowed changes for the database

## 1. Find out what is connected

Call `connection_status`.

- **`connected: true`.** Call `mssql_list_tables`. With more than one database,
  pass its name as `database`.
- **`connected: false`.** Give the user the `connectUrl` and continue with step 2.

## 2. Connect a database

Most people connect it while adding the app: right after sign-in, a form on the
Loopthink page asks for host, port, database, user and password, and tests the
login. Someone who skipped that uses the link. Never ask for a host or password
in the chat: credentials are entered on Loopthink's pages only.

Then ask the question again. The tools do not change, so nothing needs
refreshing or reconnecting in Claude.

## 3. A tool says it is not switched on

A database that was connected for saved queries only does not offer these
tools. A workspace admin switches on "Schema and read-only query tools" for it
in the Loopthink web app. Pass the link from the message on to the user.

## Notes for answering

- Look before you write: `mssql_list_tables`, then `mssql_describe_table` for
  every table the question touches. Do not guess column names.
- Write one SELECT in T-SQL: TOP instead of LIMIT, square brackets around names with spaces, no comments and no semicolon.
- Aggregate in SQL instead of reading rows and adding them up. At most 500 rows
  come back, and `truncated: true` says there were more.
- A query is stopped after 20 seconds. Narrow it with WHERE when that happens.
- `mssql_query` cannot change anything. For a change use `mssql_execute`:
  show the user the statement and wait for a yes, and check with a SELECT
  first which rows the WHERE clause matches. If it answers that changes are
  not switched on, pass the link on: a workspace admin allows them in Loopthink.
- The schema cannot be changed, and UPDATE or DELETE without WHERE is refused.
- The database has to be reachable from the internet.
