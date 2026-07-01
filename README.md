# Local AI Chat

A local web app for chatting, coding help, and image-prompt generation, powered by [Ollama](https://ollama.com) models running on your own machine. No data leaves your computer.

Works with **just one model installed** — you don't need all three.

| Mode | Model used | Purpose |
|---|---|---|
| Chat | `llama2` | General conversation |
| Uncensored Chat | `llama2-uncensored` | Unrestricted, direct answers |
| Code Assistant | `qwen2.5-coder:7b` | Coding help |
| Image Prompts | any installed chat model | Writes detailed prompts for image generators |

---

## 1. Install Ollama

Ollama runs the AI models locally on your machine.

**Windows / Mac:**
Download and install from [https://ollama.com/download](https://ollama.com/download)

**Linux:**
```bash
curl -fsSL https://ollama.com/install.sh | sh
```

After installing, make sure Ollama is running:
```bash
ollama serve
```
(On Windows/Mac the desktop app usually starts this automatically in the background.)

---

## 2. Install the AI models

You only need **one** of these — install whichever you want to use.

```bash
# General chat
ollama pull llama2

# Uncensored / unrestricted chat
ollama pull llama2-uncensored

# Coding assistant
ollama pull qwen2.5-coder:7b
```

Each model is several GB, so this may take a while depending on your connection.

To check what's installed at any time:
```bash
ollama list
```

---

## 3. Install and run the app

**Requirements:** [Node.js](https://nodejs.org) (v18 or newer) and npm.

```bash
# 1. Go into the project folder
cd local-ai-chat

# 2. Install dependencies
npm install

# 3. (Optional) copy the example env file
cp .env.example .env

# 4. Start the app
npm start
```

Then open your browser to:
```
http://localhost:3000
```

The app automatically detects which models you have installed and only enables the matching chat modes. If Ollama isn't running, you'll see a banner telling you to start it.

---

## Using the app

- **Sidebar** — switch between Chat, Uncensored Chat, Code Assistant, and Image Prompts. Modes without an installed model are grayed out.
- **Sessions** — each mode keeps its own list of past chats. Click "+ new chat" to start fresh.
- **Status panel** (bottom of sidebar) — shows whether Ollama is reachable and which model roles are available.
- Responses stream in real time as the model generates them.

---

## Troubleshooting

**"Ollama not running" banner**
Run `ollama serve` in a terminal and refresh the page.

**"No supported models found"**
Run `ollama pull llama2` (or any of the models above) and refresh.

**Slow responses**
Larger models need more RAM/VRAM. If responses are too slow, try a smaller model or close other heavy applications.

**Change the port**
Edit `.env` and set `PORT=xxxx`, then restart with `npm start`.

**Ollama running on a different machine/port**
Edit `.env` and set `OLLAMA_URL=http://<host>:<port>`.

---

## Project structure

```
local-ai-chat/
├── server.js          # Express backend, talks to Ollama
├── package.json
├── .env.example
├── public/
│   ├── index.html      # UI layout
│   └── app.js           # Frontend logic, streaming chat
└── README.md
```
