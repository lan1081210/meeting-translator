# Live Meeting Translator

[中文](README.md)

A web-based real-time meeting translator: microphone capture → speech recognition (Russian / English) → instant translation into Simplified Chinese via free translation APIs. Original and translation are shown side by side, with optional voice readout and transcript export. Pure static HTML, no backend, zero cost.

## Features

- Real-time speech-to-text in the browser: Russian (ru-RU), English (en-US), and auto mode (adapts per utterance)
- Free translation (no API key, no tokens burned), tried in order:
  1. Browser built-in translation model (Chrome 138+; download once from Settings, then it runs on-device with no quota)
  2. MyMemory free API (primary, direct, CORS enabled)
  3. Google free endpoint via public CORS proxy (last resort; often unreachable from mainland China)
- Display modes: dual panel / single panel / original only / translation only; adjustable font size; fullscreen (projection friendly)
- Voice readout of the Chinese translation (browser TTS)
- Glossary: literal post-translation replacement for names and terms
- Manual input for quiet environments
- Timestamped transcript export and copy-to-clipboard

## Quick Start

1. Open `index.html` with Chrome or Edge (speech recognition requires https or localhost; if the browser blocks the microphone on a local file, serve it):

   ```bash
   python3 -m http.server 8000
   # open http://localhost:8000
   ```

2. Press the microphone to start — original text on the left, Chinese translation on the right.
3. (Optional) Add glossary entries in Settings; register a free key at mymemory.translated.net to raise the daily quota from 5,000 to 50,000 words; or press "Download / Check" to install the browser's on-device translation model and stop worrying about quota.

No paid API key required — all translation goes through free public endpoints.

## Free Quota Notes

- MyMemory anonymous quota: about 5,000 words/day — enough for typical meetings; register a free key for heavy use.
- Free endpoints occasionally rate-limit; the app automatically falls back to the next free source and shows a retry notice if all fail.

## Deployment

Static files — deploy to GitHub Pages or any static host.

## Browser Support

| Capability | Chrome / Edge | Safari | Firefox |
|---|---|---|---|
| Speech recognition | ✅ | partial | ❌ |
| Manual translation | ✅ | ✅ | ✅ |

## Notes

- Speech recognition uses the browser engine; Chrome's recognizer talks to Google servers, so without access to Google it reports "recognition service unreachable" — use Manual Input in that case.
- Text is split at 500 characters per request (MyMemory's limit), then joined back.
- Concurrent requests are queued so free endpoints don't rate-limit (429).
- Translation quality is machine-translation grade; use the glossary to align proper nouns.

---

©lan, cooperated with artificial intelligence
