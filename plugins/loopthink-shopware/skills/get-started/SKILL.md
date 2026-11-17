---
name: get-started
description: Set up Shopware by Loopthink or work out why it returns nothing. Use when the user has just added the app, asks what it can do, gets a "connect it at …" message, or a tool says it is not switched on.
---

# Get started with Shopware by Loopthink

The app works with the Shopware account the user connected in Loopthink, and only
where their member group was granted access. The tools are always the same:

- `connection_status`: whether Shopware is connected, and the link to connect it
- `shopware_search_orders`, `shopware_get_order`, `shopware_search_order_line_items`, `shopware_list_order_documents`: orders
- `shopware_search_customers`, `shopware_get_customer`: customers
- `shopware_search_products`, `shopware_get_product`, `shopware_list_product_stock`, `shopware_list_product_reviews`: products and stock
- `shopware_list_categories`, `shopware_list_manufacturers`, `shopware_list_sales_channels`, `shopware_list_promotions`, `shopware_list_newsletter_recipients`: the rest of the shop
- `shopware_list_state_transitions`: which states an order, payment or delivery can move to
- `shopware_transition_order_state`, `shopware_transition_order_payment_state`, `shopware_transition_order_delivery_state`, `shopware_update_product_stock`: changes, only where the workspace switched them on

## 1. Find out what is connected

Call `connection_status`.

- **`connected: true`.** Go on: `shopware_search_orders` with a `sort` and a small `limit` is a good first call. With more than one Shopware server,
  pass its name as `server`.
- **`connected: false`.** Give the user the `connectUrl` and continue with step 2.

## 2. Connect Shopware

Send the user to the link. Never ask for a key, token or password in the chat:
credentials are entered on the Loopthink page only.

The page asks for the address of your shop and the access key ID and secret access key of a Shopware integration (Settings > System > Integrations).
Loopthink runs one read to test it and stores the credentials encrypted.

Then ask the question again. The tools do not change, so nothing needs
refreshing or reconnecting in Claude.

## 3. A tool says it is not switched on

Every tool that changes something is off on a new server. A workspace admin
turns it on for the server in the Loopthink web app and grants it to the member
group. Pass the link from the message on to the user.

## Notes for answering

- The search tools take Shopware criteria: `filter`, `sort`, `associations` and `aggregations`. Aggregate instead of paging through every order.
- Ids are 32 character hex strings. Find them with a search tool first.
- Before a state change, call `shopware_list_state_transitions` to see which transitions are possible.
- A state change can send the shop's mail to the customer (`send_mail`). Ask the user whether it should.
- Confirm every state change and stock update with the user first.
