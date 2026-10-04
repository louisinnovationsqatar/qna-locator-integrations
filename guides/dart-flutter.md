# Dart and Flutter

Packages (download from the dashboard, **Integration plugins**): **qna_locator** (Dart 3) and
**qna_locator_flutter**. Add the unzipped folders as path dependencies.

```yaml
dependencies:
  qna_locator:
    path: ./packages/qna_locator
  qna_locator_flutter:
    path: ./packages/qna_locator_flutter
```

```dart
final client = QnaLocatorClient(apiKey: apiKeyOnYourServer);
final place = await client.locate('55', '950', '234');
print(place.googleMapsUrl);
```

`BluePlateAddressPicker` gives your checkout three linked lists (Zone, Street, Building, labelled in
English and Arabic) and optional buttons that open the address in Google Maps or Waze:

```dart
BluePlateAddressPicker(
  client: client,
  onChanged: (LocatedAddress? address) {
    if (address == null) return; // selection incomplete or not found
    // address.latitude, address.longitude, address.googleMapsUrl, address.wazeUrl
  },
  showMapButtons: true,
);
```

A key built into a mobile app can be extracted. Call QNA-Locator from your own backend and let the
app talk to that backend.
