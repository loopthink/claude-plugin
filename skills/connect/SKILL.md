---
name: connect
description: Connect, reconnect, or switch workspaces on the Loopthink MCP connector, and diagnose a Loopthink connection that authenticates but exposes no tools. Use when the user asks to set up or sign in to Loopthink, says Loopthink tools are missing or empty, wants to switch Loopthink workspaces, or hits an auth error against mcp.eu.loopthink.ai.
---

# Connect to Loopthink

The `loopthink` MCP server ships with this plugin and points at
`https://mcp.eu.loopthink.ai/mcp`. It authenticates with OAuth 2.0 (PKCE +
dynamic client registration). There is no API key to configure.

## First connection

Walk the user through it — do not try to authenticate on their behalf:

1. `/mcp` → select `loopthink` → **Authenticate**.
2. Sign in with their Loopthink account in the browser window that opens.
3. Pick a workspace if they belong to more than one.
4. `/mcp` again to confirm a non-zero tool count.

Tools arrive namespaced as `{serverKey}__{toolName}` — the prefix is the MCP
server inside the workspace, so `orders__get_order` and `crm__get_contact` may
both be present and hit entirely different backends.

## Switching workspaces

The token is scoped to one workspace. To switch: `/mcp` → `loopthink` →
**Clear authentication**, then authenticate again and pick the other workspace.
There is no in-session switch.

## Empty tool list after a successful sign-in

This is expected behaviour, not a failure, in the common case. The connector
publishes the union of MCP servers that the signed-in user's **member group** was
granted — with no owner/admin bypass. A workspace owner with no group grant sees
zero tools.

Diagnose in this order:

1. **Confirm the sign-in actually completed.** `/mcp` should show `loopthink` as
   connected. If it shows an auth error, clear authentication and retry.
2. **Confirm the workspace.** If they picked the wrong one during login, the tool
   list will be empty or unfamiliar. Re-authenticate and pick again.
3. **Check the grant.** In the Loopthink web app (<https://app.eu.loopthink.ai>):
   the MCP server → **Access** tab → is the user's member group listed with
   *All tools* or a *Selected* subset? If not, an owner or admin adds it there.
   If the user belongs to no group at all, fix that under **Members** first.
4. **Reconnect.** `/mcp` → `loopthink` → **Reconnect**. Permission changes are
   re-validated on token refresh, so a reconnect applies them immediately instead
   of waiting out the current token.

Only after all four come back clean is it worth suspecting a server-side problem.
Point the user at <https://www.loopthink.ai/connect-claude/> and the workspace
owner in that case.

## Things that are not bugs

- **A field returned as `***` or a pseudonym.** Server-side masking policy. It
  cannot be bypassed from the client, and you should not try — do not ask the
  user for the unmasked value or route around the tool.
- **A tool that refuses to write.** Tools are read-only unless a workspace admin
  enabled writes explicitly.
- **A tool that disappeared between sessions.** A grant was changed upstream.
