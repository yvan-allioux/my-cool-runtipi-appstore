# LanguageTool

LanguageTool is an open-source grammar, style, and spell checker that supports more than 30 languages. It can be used as a self-hosted alternative to cloud-based grammar checkers like Grammarly.

## Features

- Grammar and style checking for 30+ languages
- HTTP API accessible at `/v2/check`
- Compatible with browser extensions (Firefox, Chrome)
- LibreOffice/OpenOffice integration
- FastText language detection (pre-installed)
- Optional n-gram data support for enhanced error detection

## Usage

Once installed, the API is available at:

```
http://<your-server>:<port>/v2/check
```

Example API call:

```
curl -d "language=en-US&text=A sentence with a error in the Hitchhiker's Guide tot able Galaxy." http://localhost:8010/v2/check
```

## Browser Extensions

You can configure the LanguageTool browser extension to use your self-hosted instance by setting the server URL in the extension settings.

## N-gram Data (Optional)

For improved error detection, you can download n-gram datasets and place them in the app data directory under `data/ngrams/`. Download n-gram data from: https://languagetool.org/download/ngram-data/

Expected directory structure:

```
data/ngrams/
  en/
    1grams/
    2grams/
    3grams/
  fr/
    1grams/
    2grams/
    3grams/
```
