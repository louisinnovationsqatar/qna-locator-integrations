# WooCommerce

The **QNA-Locator Blue Plate Address** plugin adds Zone, Street and Building fields to your checkout
for Qatar addresses, checks them against QNA-Locator, and saves the address on the order with its
coordinates and Google Maps and Waze links.

## Install

1. Sign in at https://qna.louis-innovations.com and open **Integration plugins**.
2. Download the WooCommerce plugin zip.
3. In WordPress: **Plugins, Add New, Upload Plugin**, choose the zip, then **Activate**.
4. Open **WooCommerce, Settings, Integration, QNA-Locator** and paste your API key.

## What your customers see

When the country is Qatar, checkout shows three linked lists: Zone, Street and Building (labels in
English and Arabic). Choosing a zone loads its streets; choosing a street loads its buildings.
It works with the classic checkout and the block checkout (WooCommerce 8.9 and later).

## What you get on each order

- The Blue Plate (zone, street, building), the coordinates, and buttons to open the address in
  Google Maps or Waze, on the order screen, in the customer's account and in order emails.
- Returning customers find their last Blue Plate filled in.

## Good to know

- The key stays on your server: the browser talks only to your own WordPress site, so you do not need
  to register your website on the dashboard.
- Zones, streets and buildings are cached for 12 hours to save your quota.
- If QNA-Locator cannot be reached, the order is still accepted with the numbers the customer
  entered and marked "unverified", so you never lose a sale.

Requirements: WordPress 6.0+, WooCommerce 7.0+, PHP 7.4+.
