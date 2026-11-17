---
name: get-started
description: Set up Lexware Office by Loopthink or work out why it returns nothing. Use when the user has just added the app, asks what it can do, gets a "connect it at …" message, or a tool says it is not switched on.
---

# Get started with Lexware Office by Loopthink

The app works with the Lexware Office account the user connected in Loopthink, and only
where their member group was granted access. The tools are always the same:

- `connection_status`: whether Lexware Office is connected, and the link to connect it
- `lexware_list_vouchers`: documents of every type by type, status and date; returns ids
- `lexware_get_invoice` and the other `lexware_get_` tools`: one document by id
- `lexware_get_payments`: what is paid and open on a document
- `lexware_list_contacts`, `lexware_list_articles`: master data
- `lexware_create_customer`: creates a customer contact, only where the workspace switched it on

## 1. Find out what is connected

Call `connection_status`.

- **`connected: true`.** Go on: `lexware_list_vouchers` needs `voucherType` and `voucherStatus`; use `any` for either when the user did not narrow it down. With more than one Lexware Office server,
  pass its name as `server`.
- **`connected: false`.** Give the user the `connectUrl` and continue with step 2.

## 2. Connect Lexware Office

Send the user to the link. Never ask for a key, token or password in the chat:
credentials are entered on the Loopthink page only.

The page asks for your Lexware Office API key (created at app.lexware.de/addons/public-api, shown only once).
Loopthink runs one read to test it and stores the credentials encrypted.

Then ask the question again. The tools do not change, so nothing needs
refreshing or reconnecting in Claude.

## 3. A tool says it is not switched on

Every tool that changes something is off on a new server. A workspace admin
turns it on for the server in the Loopthink web app and grants it to the member
group. Pass the link from the message on to the user.

## Notes for answering

- Amounts come in the currency of the document. Sum only what has the same currency.
- `lexware_list_vouchers` is paged (`page`, `size`). For totals, page until `last` is true instead of guessing.
- Lexware Office allows two requests per second. Read what the question needs, not every document.
- Confirm a new contact with the user before calling `lexware_create_customer`.
