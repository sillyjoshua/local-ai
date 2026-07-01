# Local AI

A native desktop app for chatting, coding help, and image-prompt generation, powered by [Ollama](https://ollama.com) models running on your own machine. No data leaves your computer.

Works with **just one model installed** — you don't need all three.

| Mode | Model used | Purpose |
|---|---|---|
| Chat | `llama2` | General conversation |
| Uncensored Chat | `llama2-uncensored` | Unrestricted, direct answers |
| Code Assistant | `qwen2.5-coder:7b` | Coding help |
| Image Prompts | any installed chat model | Writes detailed prompts for image generators |

---

## 1. Install Ollama

**Windows / Mac:** [https://ollama.com/download](https://ollama.com/download)

**Linux:**
```bash
curl -fsSL https://ollama.com/install.sh | sh
```

Ollama runs in the background automatically after install. To check:
```bash
ollama serve
```

---

## 2. Install the AI models

Install whichever you want — only one is required.

```bash
ollama pull llama2
ollama pull llama2-uncensored
ollama pull qwen2.5-coder:7b
```

Check installed models:
```bash
ollama list
```

---

## 3. Install and run the app

**Requirements:** [Node.js](https://nodejs.org) (v18+) and npm.

```Setup
Extract and move the extracted folder to C:/Users/<your-user>
```

```bash
cd local-ai-chat
npm install
npm start
```

This opens **Local AI** as its own desktop window — not a browser tab. The app starts its local server in the background automatically.

---

## Building an installer (optional)

To package it into a real installable app (`.exe`, `.dmg`, `.AppImage`):

```bash
npx electron-builder
```

Output goes to the `dist/` folder. Run the installer there like any other app.

---

## Using the app

- **Sidebar** — switch between Chat, Uncensored Chat, Code Assistant, and Image Prompts. Modes without an installed model are grayed out.
- **Sessions** — each mode keeps its own history. Click "+ new chat" to start fresh.
- **Status panel** — shows whether Ollama is reachable and which models are available.

---

## Troubleshooting

**Blank window on launch**
Ollama might be slow to respond on first load — wait a few seconds, it retries automatically.

**"Ollama not running" banner**
Run `ollama serve` and relaunch the app.

**"No supported models found"**
Run `ollama pull llama2` and relaunch.

**Change the port**
Edit `.env` and set `PORT=xxxx`.

---

## Project structure

```
local-ai-chat/
├── electron.js       # Desktop app entry point
├── server.js          # Backend, talks to Ollama
├── package.json
├── .env.example
├── public/
│   ├── index.html
│   └── app.js
└── README.md
```

