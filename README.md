# AI Projects — Chinedum Aranotu

<!-- This app was built by CeeJay for Chinedum Aranotu – 2026 -->

> A collection of AI-powered web apps built with the Claude API. No sign-up, no API key — just open and use.

**Live:** [ai-projects-flax.vercel.app](https://ai-projects-flax.vercel.app) &nbsp;·&nbsp; **Stack:** Claude API (Sonnet 4) · Vanilla JS · HTML/CSS · Vercel Serverless

---

## Apps

| # | App | What it does |
|---|-----|-------------|
| 01 | [**CoachAI**](https://ai-projects-flax.vercel.app/chatbot) | AI fitness coach chatbot with multi-turn conversation, persona system prompt, and starter prompts |
| 02 | [**ResumeAI**](https://ai-projects-flax.vercel.app/resumeReviewer) | Resume gap analyzer — scores your resume against a job description, surfaces missing ATS keywords and quick wins |
| 03 | [**SentimentAI**](https://ai-projects-flax.vercel.app/sentiment) | Real-time sentiment analysis across 4 classes with confidence scores, animated meters, and analysis history |
| 04 | [**SummarAI**](https://ai-projects-flax.vercel.app/summarizer) | Multi-mode text summarizer — bullet points, paragraph, ELI5, and TL;DR with word count reduction stats |
| 05 | [**LabelAI**](https://ai-projects-flax.vercel.app/dataLabeler) | Batch data labeling tool with custom schemas, few-shot examples, confidence scores, and CSV export |
| 06 | [**PromptLab**](https://ai-projects-flax.vercel.app/promptComparison) | Side-by-side prompt comparison — runs two system prompts in parallel and AI-analyzes what made the difference |

---

## Architecture

API calls are routed through a Vercel serverless function (`/api/proxy.js`) that holds the Anthropic API key as a server-side environment variable. The frontend never touches the key.

```
Browser  →  /api/proxy  →  api.anthropic.com
              (Vercel)        (Claude API)
              key lives
              here only
```

This means users can open any app and start using it immediately — no sign-up, no key input required.

---

## Key AI Techniques Demonstrated

- **System prompts & personas** — CoachAI uses a structured system prompt to maintain a consistent coaching voice across multi-turn conversation
- **Structured JSON output** — ResumeAI, SentimentAI, and LabelAI instruct the model to return strict JSON, which is parsed and rendered into UI components
- **Few-shot prompting** — LabelAI lets you define labeled examples that get injected into the prompt at runtime to guide classification
- **Prompt mode switching** — SummarAI sends different instruction sets to the same model depending on the output format selected (bullets / paragraph / ELI5 / TL;DR)
- **Parallel API calls** — PromptLab fires both prompt variants simultaneously with `Promise.all`, then runs a third analysis call to compare outputs
- **Multi-turn conversation** — CoachAI maintains a full `conversationHistory` array and passes it with every request

---

## Project Structure

```
aiProjects/
├── api/
│   └── proxy.js              # Vercel serverless proxy — holds API key
├── index.html                # Portfolio landing page
├── chatbot.html              # CoachAI — fitness coach chatbot
├── resumeReviewer.html       # ResumeAI — resume gap analyzer
├── sentiment.html            # SentimentAI — sentiment analysis
├── summarizer.html           # SummarAI — multi-mode summarizer
├── dataLabeler.html          # LabelAI — batch data labeling tool
├── promptComparison.html     # PromptLab — prompt A/B comparison
├── vercel.json               # Serverless function config + clean URLs
└── README.md
```

---

## Running Locally

```bash
git clone https://github.com/aranotuchinedum2/aiProjects.git
cd aiProjects
```

Create a `.env.local` file:

```
ANTHROPIC_API_KEY=sk-ant-...
```

Then run with the Vercel CLI so the proxy function works:

```bash
npm i -g vercel
vercel dev
```

Open `http://localhost:3000`. The proxy reads your local env var and all 6 apps work without any key input.

---

## Deploying Your Own Fork

1. Fork this repo and push to your GitHub
2. Import the project at [vercel.com](https://vercel.com)
3. In **Settings → Environment Variables**, add `ANTHROPIC_API_KEY` with your key
4. Redeploy — done

---

## Model

All apps use **Claude Sonnet 4** (`claude-sonnet-4-20250514`). The proxy forwards the request body from the frontend directly to Anthropic, so switching models is a one-line change per app.

---

## License

MIT — use freely, build on top, credit appreciated.

---

*Built by Chinedum Aranotu · 2026*
