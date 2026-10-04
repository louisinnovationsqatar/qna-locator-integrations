# JavaScript and TypeScript

Package: **@louis-innovations/qna-locator** (download from the dashboard, **Integration plugins**).
Zero dependencies; Node.js 18+ and modern browsers.

```bash
npm install ./qna-locator-js
```

```ts
import { QnaLocator, QnaLocatorError } from '@louis-innovations/qna-locator';

const qna = new QnaLocator({ apiKey: process.env.QNA_LOCATOR_API_KEY! });

try {
  const place = await qna.locate({ zone: '55', street: '950', building: '234' });
  console.log(place.latitude, place.longitude, place.googleMapsUrl, place.wazeUrl);
} catch (err) {
  if (err instanceof QnaLocatorError && err.code === 'NOT_FOUND') {
    // ask the customer to check the Blue Plate
  }
}
```

Other calls: `zones()`, `streets(zone)`, `buildings(zone, street)`.
Errors carry `status`, `code` (`UNAUTHORIZED`, `NOT_REGISTERED`, `NOT_FOUND`, `RATE_LIMITED`, `BUSY`,
`SERVER`, `TIMEOUT`, `NETWORK`, `BAD_REQUEST`), `requestId` and `retryAfterSeconds`.
The client retries busy (503) and network failures twice; it never retries a 429 for you.

Keep the key on your server. For a browser app, call your own backend, which calls QNA-Locator.
