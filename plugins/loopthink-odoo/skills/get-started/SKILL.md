---
name: get-started
description: Set up Loopthink for Odoo or work out why it returns nothing. Use when the user has just added the app, asks what it can do, gets a "connect it at …" message, or a tool says it is not switched on.
---

# Get started with Loopthink for Odoo

The app works with the Odoo account the user connected in Loopthink, and only
where their member group was granted access. The tools are always the same:

- `connection_status`: whether Odoo is connected, and the link to connect it
- `odoo_list_models`: the models enabled for the server, such as `res.partner` or `sale.order`
- `odoo_list_fields`: the fields of one model
- `odoo_search_read`, `odoo_read`, `odoo_count`: search with a domain, read by id, count
- `odoo_list_companies`, `odoo_search_models`, `odoo_get_server_version`: about the database itself
- `odoo_create`, `odoo_write`: create and update records, only where the workspace allowed changes

## 1. Find out what is connected

Call `connection_status`.

- **`connected: true`.** Go on: call `odoo_list_models`, then `odoo_list_fields` with the `model` you need before the first `odoo_search_read`. With more than one Odoo server,
  pass its name as `server`.
- **`connected: false`.** Give the user the `connectUrl` and continue with step 2.

## 2. Connect Odoo

Send the user to the link. Never ask for a key, token or password in the chat:
credentials are entered on the Loopthink page only.

The page asks for the address of your Odoo and an API key (in Odoo under My Preferences > Account Security > New API Key).
Loopthink runs one read to test it and stores the credentials encrypted.

Then ask the question again. The tools do not change, so nothing needs
refreshing or reconnecting in Claude.

## 3. A tool says it is not switched on

Every tool that changes something is off on a new server. A workspace admin
turns it on for the server in the Loopthink web app and grants it to the member
group. Pass the link from the message on to the user.

## Notes for answering

- Always pass `fields` to `odoo_search_read`. A record with every field is large.
- A domain is a list of `[field, operator, value]` conditions, for example `[["state","=","sale"]]`. Many2one fields filter by id.
- Use `odoo_count` for totals instead of reading every record.
- A model that is "not enabled" has to be enabled for the server by a workspace admin in Loopthink. Pass the link on.
- Confirm every `odoo_create` and `odoo_write` with the user first.
