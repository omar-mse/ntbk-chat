# ntbk · PDF Chat

A single-file web app for reading PDFs, chatting with them, and visualizing their ideas as a knowledge graph — powered by Google's Gemini 2.5 Flash. Everything runs in the browser; there is no backend.

## Features

- **Chat with your PDFs** — Ask questions and get answers grounded strictly in the document. Every factual claim is cited with the source page (`[p.N]` or `[p.N-M]`), and clicking a citation jumps the viewer to that page.
- **Built-in PDF viewer** — Upload one or more PDFs and read them side-by-side with the chat using the browser's native PDF renderer.
- **Knowledge graph** — Generate an interactive graph (15–40 nodes) of a document's key entities, concepts, and relationships, with per-node summaries and real page references. Built with [vis-network](https://github.com/visjs/vis-network).
- **Light & dark themes** — A reading-room aesthetic that follows your preference and persists across sessions.
- **Local-first & private** — Your API key, documents, and chat history live only in your browser. Nothing is sent anywhere except directly to the Google Generative Language API.

## Getting started

1. Get a Gemini API key from [Google AI Studio](https://aistudio.google.com/app/apikey).
2. Open `index.html` in a modern browser (double-click it, or serve the folder with any static file server).
3. Paste your API key into the **Gemini key** field in the top bar. The status indicator turns green when the key is valid.
4. Click **＋ Upload PDF** and select one or more PDF files.
5. Select a document, then start asking questions in the chat panel. Switch the center pane to **Knowledge Graph** to generate and explore its concept map.

> **Tip:** Run from a local server (e.g. `python -m http.server`) rather than `file://` if your browser restricts the embedded PDF viewer.

## How it works

The app is a single `index.html` (HTML, CSS, and vanilla JavaScript — no build step). PDFs are read into the browser, base64-encoded, and sent inline to the Gemini API alongside a system prompt that enforces page-cited, document-grounded answers.

| | |
|---|---|
| **Model** | `gemini-2.5-flash` |
| **API** | `https://generativelanguage.googleapis.com/v1beta` |
| **Dependencies** | vis-network (CDN), Google Fonts |
| **Storage** | `localStorage` (API key + theme); documents and chat live in memory for the session |

## Privacy

Your API key is stored in your browser's `localStorage` and is sent only to Google's API endpoints. PDF contents are transmitted to the Gemini API to answer your questions and build graphs. No other servers are involved.

## License

No license specified. Add one if you intend to distribute.
