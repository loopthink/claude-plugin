# Loopthink setup

Guide the user through connecting the bundled `loopthink` MCP server. The plugin
ships the connector URL, so there is nothing to install and no API key to paste —
setup is an OAuth sign-in plus, usually, one permission check in the Loopthink web app.

## Prerequisites to confirm

- The user has a Loopthink account and belongs to at least one workspace.
- Their member group has been granted access to at least one MCP server in that
  workspace. Without a grant the connector authenticates fine but publishes zero
  tools — this is the single most common "it doesn't work" report.

## Steps

1. **Authenticate.** Ask the user to run `/mcp`, select `loopthink`, and choose
   *Authenticate*. Claude Code opens a browser window.
2. **Sign in.** They sign in with their Loopthink account on
   `mcp.eu.loopthink.ai`. Credentials go to Loopthink directly; Claude Code never
   sees them.
3. **Pick a workspace.** Users who belong to more than one workspace get a picker.
   The connection is scoped to the workspace they pick — to switch, they
   re-authenticate and pick a different one.
4. **Verify.** Run `/mcp` again and confirm `loopthink` shows as connected with a
   non-zero tool count. Tools are named `{serverKey}__{toolName}`, for example
   `crm__search_contacts`.

## If the tool list is empty

An empty tool list after a successful sign-in is almost always a permissions
result, not a bug. The connector unions only the MCP servers the signed-in user's
member group was explicitly granted — there is deliberately no owner or admin
bypass, so even a workspace owner sees nothing until a grant exists.

Tell the user to open the Loopthink web app at <https://app.eu.loopthink.ai>, then:

1. Go to the MCP server they expect to see → **Access** tab.
2. Confirm the user's member group is listed with either *All tools* or a
   *Selected* tool subset.
3. If it is missing, an owner or admin adds the group there. If the user is not in
   a member group yet, add them under **Members** first.
4. Back in Claude Code, run `/mcp` → *Reconnect*. Grants take effect within one
   token lifetime; reconnecting applies them immediately.

## Notes

- The connector is read-only unless a workspace admin explicitly enabled writes on
  a given tool. Do not assume a tool mutates state — check its description.
- Masking rules run server-side. If a field comes back as `***` or a pseudonym,
  that is the workspace's masking policy, not a truncation bug, and it cannot be
  worked around from the client.
- Everything runs in the AWS European Sovereign Cloud. Do not suggest routing
  Loopthink data through other services to "fix" a limitation.
