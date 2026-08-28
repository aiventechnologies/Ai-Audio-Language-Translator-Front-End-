# Voxbridge — AI Audio Language Translator (Frontend)

A React + Vite frontend for an AI-powered audio language translator. Record or upload
speech, pick a source and target language, and get a live transcript + translation with
an animated waveform display. This repo is **frontend only** — wire up your own backend
or AI API (e.g. Whisper for transcription + an LLM/translation API) in `src/lib/api.js`.

## Features

- 🎙️ In-browser audio recording (MediaRecorder API) with a live animated waveform
- 📁 Drag-and-drop audio file upload as an alternative to recording
- 🌐 Source/target language selection with quick-swap
- 📝 Transcript + translation panel with copy-to-clipboard
- 🕘 Local session history of past translations
- 🎨 Distinctive, fully responsive UI (see Design section)

## Technology stack

- React 18 + Vite
- Plain CSS (no framework) using CSS custom properties for theming
- Web Audio API for the waveform visualizer

## Getting started

```bash
npm install
npm run dev
```

Open the printed local URL in your browser. Grant microphone permission to record.

To build for production:

```bash
npm run build
npm run preview
```

## Connecting a real backend

All network calls are isolated in `src/lib/api.js`. Two functions are stubbed and ready
to be pointed at a real service:

- `transcribeAudio(blob, sourceLang)` — send the recorded/uploaded audio to your speech-to-text
  endpoint (e.g. Whisper API) and return `{ text }`.
- `translateText(text, sourceLang, targetLang)` — send transcribed text to your
  [translation](https://unicodeinpage.com/roman-urdu-to-english-and-english-to-roman-urdu-converter/) /LLM endpoint and return `{ translatedText }`.

Both currently return mocked data after a short delay so the UI is fully demoable without
a backend.

## Project structure

```
src/
  components/
    Header.jsx
    Recorder.jsx
    WaveformVisualizer.jsx
    LanguageSelector.jsx
    TranscriptPanel.jsx
    HistoryList.jsx
    Footer.jsx
  lib/
    api.js
    languages.js
  App.jsx
  main.jsx
  index.css
```

## Deploying

This is a static Vite app — deploy the `dist/` output to Vercel, Netlify, GitHub Pages,
or Cloudflare Pages.

## License

MIT — do whatever you like with this.
