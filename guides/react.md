# React and Next.js

Package: **@louis-innovations/qna-locator-react** (download from the dashboard, **Integration plugins**).
Needs the JavaScript SDK and React 18 or later.

`BluePlateAddressPicker` shows three linked lists (Zone, Street, Building, labelled in English and
Arabic) and gives you the located address with its map links.

## Recommended: through your own server (key stays private)

```tsx
// app/api/qna/[...path]/route.ts (Next.js): forwards to QNA-Locator with your key
import { QnaLocator } from '@louis-innovations/qna-locator';
const qna = new QnaLocator({ apiKey: process.env.QNA_LOCATOR_API_KEY! });
// expose zones, streets, buildings and locate as GET handlers that call qna.*
```

```tsx
import { BluePlateAddressPicker } from '@louis-innovations/qna-locator-react';

<BluePlateAddressPicker
  fetcher={myFetcherThatCallsMyOwnApi}
  showMapLinks
  onChange={(address) => setDeliveryAddress(address)}
/>
```

## Direct from the browser

Register your website on the dashboard first, then pass `apiKey` instead of `fetcher`. Anyone can
read a key that is sent to a browser, so prefer the server route above.
