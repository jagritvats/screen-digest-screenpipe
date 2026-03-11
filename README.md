# 📋 Daily Screen Digest

A [screenpipe](https://github.com/mediar-ai/screenpipe) pipe that summarizes your workday by analyzing your screen activity. Get a structured breakdown of what you did, which apps you used, and key activities — all from your local screen recordings.

<img width="1256" height="689" alt="image" src="https://github.com/user-attachments/assets/5b06aaef-0c18-425f-a102-52aca630c430" />


## What it does

- **Select a time range** (last 2h, 4h, 8h, or full day)
- **Generates a digest** of your screen activity grouped by application
- **AI-powered summaries** via OpenAI (optional — works without it too)
- **Raw grouped view** when no API key is provided — still useful for seeing what you did
- **100% local** — your data never leaves your machine unless you choose to use OpenAI

## How it works

1. Queries screenpipe's local API (`localhost:3030`) for OCR text captured from your screen
2. Groups the captured text by application (VS Code, Chrome, Slack, Terminal, etc.)
3. Optionally sends the grouped data to OpenAI for a clean, structured summary
4. Displays the result as formatted markdown with key activities, timeline, and highlights

## Installation

### As a screenpipe pipe

```bash
# Clone the repo
git clone https://github.com/jagritvats/screen-digest-screenpipe.git
cd screen-digest-screenpipe

# Install dependencies
bun install

# Run
bun run dev
```

Make sure [screenpipe](https://github.com/mediar-ai/screenpipe) is running on your machine (default port 3030).

### Standalone development

The pipe works without screenpipe running — it shows a connection message and you can use the mock server for testing:

```bash
# Start the mock server (simulates screenpipe API)
node mock-server.js

# In another terminal
bun run dev
```

## Configuration

| Setting | Required | Description |
|---------|----------|-------------|
| OpenAI API Key | No | Enables AI-powered summaries. Without it, you get raw grouped data. |
| Time Range | Yes | Select last 2h, 4h, 8h, or full day |

## Tech Stack

- **Next.js** with TypeScript
- **screenpipe REST API** for screen data
- **OpenAI API** (optional) for summarization
- **Tailwind CSS** for styling

## Roadmap

- [ ] Screen time analytics with charts (time per app, productivity score)
- [ ] Automatic scheduled digests (e.g. every day at 6 PM)
- [ ] Export digest as markdown file
- [ ] Support for Ollama / local LLMs instead of OpenAI
- [ ] App categorization (productive vs distraction)

## License

MIT

---

Built as a [screenpipe pipe](https://docs.screenpi.pe/plugins) — give your AI memory of your screen.
