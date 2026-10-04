# HTTP API

Base URL: `https://qna.louis-innovations.com/api/v1`
Authentication: `Authorization: Bearer <your API key>` on every request.

## Endpoints

| Call | Returns |
|---|---|
| `GET /zones` | `{"zones":[{"zoneNumber":"55"}]}` |
| `GET /streets?zone=55` | `{"zone":"55","streets":[{"streetNumber":"950"}]}` |
| `GET /buildings?zone=55&street=950` | `{"zone":"55","street":"950","buildings":[{"buildingNumber":"8"}]}` |
| `GET /locate?zone=55&street=950&building=234` | `{"zone":"55","street":"950","building":"234","latitude":"25.25","longitude":"51.53","googleMapsUrl":"...","wazeUrl":"..."}` |

`/buildings` lists building numbers only. Coordinates come from `/locate`, one address at a time.

```bash
curl "https://qna.louis-innovations.com/api/v1/locate?zone=55&street=950&building=234" \
  -H "Authorization: Bearer $QNA_LOCATOR_API_KEY"
```

## Errors

| Status | Meaning | What to do |
|---|---|---|
| 400 | Missing or malformed zone, street or building | Fix the input; numbers only, up to 6 digits |
| 401 | Missing, wrong or revoked key | Check the key on your dashboard |
| 403 | Call from a website that is not registered | Register the site, or call from your server |
| 404 | Address not found | Ask the customer to check the Blue Plate |
| 429 | Limit reached | Read `period` and `resetsAt` in the body and `Retry-After` |
| 503 | Busy, request queued too long | Retry after `Retry-After` seconds; it was not counted |
| 500 / 504 | Failure on our side | Retry; it was not counted. Quote `requestId` |

Response headers: `X-Request-Id`, `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Period`.

## Good practice

- Keep the key on your server; never ship it inside a mobile app or public JavaScript.
- Cache `/zones`, `/streets` and `/buildings` for a few hours; they change rarely.
- Save the coordinates and map links with the order, so you do not look the same address up again.
