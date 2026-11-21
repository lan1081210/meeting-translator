# Live Meeting Translator

[中文](README.md)

A web-based real-time meeting translator: microphone capture → speech recognition (Russian / English) → streaming translation into Simplified Chinese via DeepSeek. Original and translation are shown side by side, with optional voice readout and transcript export. Pure static HTML, no backend.

## Features

- Real-time speech-to-text in the browser: Russian (ru-RU), English (en-US), and auto mode (adapts per utterance)
- Streaming translation via DeepSeek API (deepseek-chat / deepseek-reasoner) — text appears word by word
- Display modes: dual panel / single panel / original only / translation only; adjustable font size; fullscreen (projection friendly)
- Voice readout of the Chinese translation (browser TTS)
- Glossary and meeting context settings for better terminology alignment
- Manual input for quiet environments
- Timestamped transcript export and copy-to-clipboard

## Quick Start

1. Open `index.html` with Chrome or Edge (speech recognition requires https or localhost; if the browser blocks the microphone on a local file, serve it):

   ```bash
   python3 -m http.server 8000
   # open http://localhost:8000
   ```

2. Click "⚙ 设置" (Settings) in the top-right and enter your DeepSeek API key (get one at [platform.deepseek.com](https://platform.deepseek.com/)).
3. Pick a language (Russian / English / auto) and press the microphone to start.

The API key is stored only in your browser's localStorage. Translation requests go directly from the browser to the DeepSeek API — no third-party server involved.

## Deployment

Static files — deploy to GitHub Pages or any static host. On public deployments, each user enters their own API key in Settings.

## Browser Support

| Capability | Chrome / Edge | Safari | Firefox |
|---|---|---|---|
| Speech recognition | ✅ | partial | ❌ |
| Manual translation | ✅ | ✅ | ✅ |

## Notes

- Speech recognition is provided by the browser's built-in engine; quality depends on the browser and network.
- Translation quality depends on the DeepSeek model; use the glossary and meeting context settings.

---

©lan, cooperated with artificial intelligence
