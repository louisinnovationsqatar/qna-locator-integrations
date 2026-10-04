# QNA-Locator integrations

Integration guides for **QNA-Locator**, the Qatar National Address API by Louis Innovations
(https://qna.louis-innovations.com). Use it to turn a Blue Plate address (zone, street and building
number) into coordinates, with ready Google Maps and Waze links, at checkout or in any app.

This repository holds documentation only. The plugins and SDKs are downloaded from your QNA-Locator
dashboard under **Integration plugins** after you sign up, so every package matches your account and
the current API version.

## Start here

1. Create a free account at https://qna.louis-innovations.com/signup with your company email and a
   Qatar mobile number (500 requests a month free; Pro plans add 5,000 requests a day).
2. Create your API key on the dashboard. Keep it on your server.
3. Pick your platform:

| Platform | Guide |
|---|---|
| WooCommerce (WordPress) | [guides/woocommerce.md](guides/woocommerce.md) |
| Any backend (HTTP) | [guides/api.md](guides/api.md) |
| JavaScript and TypeScript (Node.js) | [guides/javascript.md](guides/javascript.md) |
| React and Next.js | [guides/react.md](guides/react.md) |
| PHP and Laravel | [guides/php-laravel.md](guides/php-laravel.md) |
| Dart and Flutter | [guides/dart-flutter.md](guides/dart-flutter.md) |

## Limits that matter when you integrate

- Free: 500 requests per calendar month. Pro: 5,000 requests a day. Counted per account.
- Up to 120 calls a minute per account, and up to 20,000 different addresses located per month.
  Looking up the same address again does not count towards the address limit.
- Calls from a web page work only from websites you register on the dashboard (up to 10). Server
  calls need no registration.
- Every call returns `X-Request-Id`; quote it when you contact support.

Full reference: https://qna.louis-innovations.com/docs

## Support

info@louis-innovations.com, +974 3371 0925. Abtikarat Louis Trading and Services W.L.L.,
CR 173808, Doha, Qatar.

Copyright (c) 2026 Louis Innovations. Documentation licensed under CC BY 4.0.
