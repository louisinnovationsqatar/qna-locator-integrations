# PHP and Laravel

Packages (download from the dashboard, **Integration plugins**):
**louis-innovations/qna-locator** (PHP 8.1+) and **louis-innovations/qna-locator-laravel**
(Laravel 10, 11 and 12). Add the unzipped folders as Composer path repositories.

```json
"repositories": [
  { "type": "path", "url": "./packages/qna-locator-php" },
  { "type": "path", "url": "./packages/qna-locator-laravel" }
]
```

## Plain PHP

```php
use LouisInnovations\QnaLocator\Client;

$qna = new Client(getenv('QNA_LOCATOR_API_KEY'));
$place = $qna->locate('55', '950', '234');
echo $place->googleMapsUrl;
```

## Laravel

Set `QNA_LOCATOR_API_KEY` in `.env`, then:

```php
use LouisInnovations\QnaLocator\Laravel\Facades\QnaLocator;
use LouisInnovations\QnaLocator\Laravel\Rules\BluePlate;

$place = QnaLocator::locate('55', '950', '234');

$rule = new BluePlate();
$request->validate([
    // "55 950 234", "55/950/234" or ['zone' => .., 'street' => .., 'building' => ..]
    'address' => ['required', $rule],
]);

if ($rule->isUnverified()) {
    // QNA-Locator could not be reached; the address passed without being checked.
}
```

The rule rejects an address that does not exist. If the service cannot be reached it lets the form
through and logs a warning, so customers are never blocked by an outage. Use `BluePlate::strict()` to
refuse instead.
