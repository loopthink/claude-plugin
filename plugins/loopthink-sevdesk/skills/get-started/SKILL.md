---
name: get-started
description: Set up Loopthink for sevDesk or work out why it returns nothing. Use when the user has just added the app, asks what it can do, gets a "connect it at …" message, or a tool says it is not switched on.
---

# Get started with Loopthink for sevDesk

The app works with the sevDesk account the user connected in Loopthink, and only
where their member group was granted access. The tools are always the same:

- `connection_status`: whether sevDesk is connected, and the link to connect it
- `sevdesk_list_invoices`, `sevdesk_list_orders`, `sevdesk_list_credit_notes`, `sevdesk_list_vouchers`: documents by status, date and contact; return ids
- `sevdesk_get_invoice` and the other `sevdesk_get_` tools`: one record by id, with its positions where there are any
- `sevdesk_list_check_accounts`, `sevdesk_get_check_account_balance`, `sevdesk_list_transactions`: bank accounts, balances and transactions
- `sevdesk_list_contacts`, `sevdesk_list_parts`: master data
- `sevdesk_create_contact`: creates a contact, only where the workspace switched it on

## 1. Find out what is connected

Call `connection_status`.

- **`connected: true`.** Go on: `sevdesk_list_invoices` with a `status` (100 draft, 200 open, 1000 paid) is a good first call. With more than one sevDesk server,
  pass its name as `server`.
- **`connected: false`.** Give the user the `connectUrl` and continue with step 2.

## 2. Connect sevDesk

Send the user to the link. Never ask for a key, token or password in the chat:
credentials are entered on the Loopthink page only.

The page asks for your sevDesk API token (in sevDesk under Settings > Users, in the details of the user).
Loopthink runs one read to test it and stores the credentials encrypted.

Then ask the question again. The tools do not change, so nothing needs
refreshing or reconnecting in Claude.

## 3. A tool says it is not switched on

Every tool that changes something is off on a new server. A workspace admin
turns it on for the server in the Loopthink web app and grants it to the member
group. Pass the link from the message on to the user.

## Notes for answering

- Lists are paged with `limit` and `offset`. Pass `countAll: true` where the tool offers it to learn the total.
- A contact filter needs both `contact_id` and `contact_objectName` ("Contact").
- Dates in filters are Unix timestamps or ISO dates, as each tool's description says.
- Confirm a new contact with the user before calling `sevdesk_create_contact`.
