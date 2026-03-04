# Playwright (Browserless Chrome)

Headless Chrome browser-as-a-service, compatible with Puppeteer, Playwright, and Selenium. Exposes a REST and WebSocket API for browser automation.

## Use Cases

- **Screenshots & PDFs** – Render any webpage to an image or PDF via API
- **Web scraping** – Automate data extraction with full JavaScript support
- **Automated testing** – Run Playwright or Puppeteer tests against a remote Chrome instance
- **Form automation** – Fill and submit forms programmatically

## API Access

Once running, the API is available at `http://<your-server>:20450`.

Authenticate requests by appending your token as a query parameter or header:

```
?token=your-secret-token
```

### Example: Screenshot

```bash
curl -X POST \
  "http://localhost:20450/screenshot?token=your-secret-token" \
  -H "Content-Type: application/json" \
  -d '{"url": "https://example.com"}' \
  --output screenshot.png
```

### Example: Connect with Playwright (Node.js)

```js
const { chromium } = require('playwright');

const browser = await chromium.connectOverCDP(
  'ws://localhost:20450?token=your-secret-token'
);
```

## Configuration

| Variable | Description | Default |
|---|---|---|
| `TOKEN` | API authentication token | *(required)* |
| `CONCURRENT` | Max simultaneous sessions | `5` |
| `TIMEOUT` | Session timeout in ms | `60000` |

## Documentation

Full API reference: [https://www.browserless.io/docs](https://www.browserless.io/docs)
