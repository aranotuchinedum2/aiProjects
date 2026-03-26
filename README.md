# AI Projects — Chinedum Aranotu

<!-- This app was built by CeeJay for Chinedum Aranotu – 2026 -->

> A collection of AI-powered web apps built with the Claude API. Each app is a self-contained HTML file — no build step, no framework, just clean vanilla JS hitting a real AI model.

**Live:** [ai-projects-flax.vercel.app](https://ai-projects-flax.vercel.app) &nbsp;·&nbsp; **Stack:** Claude API (Sonnet 4) · Vanilla JS · HTML/CSS · Vercel

---

## Apps

| # | App | What it does |
|---|-----|-------------|
| 01 | [**CoachAI**](https://ai-projects-flax.vercel.app/chatbot) | AI fitness coach chatbot with multi-turn conversation, persona system prompt, and starter prompts |
| 02 | [**ResumeAI**](https://ai-projects-flax.vercel.app/resumeReviewer) | Resume gap analyzer — scores your resume against a job description, surfaces missing ATS keywords and quick wins |
| 03 | [**SentimentAI**](https://ai-projects-flax.vercel.app/sentiment) | Real-time sentiment analysis across 4 classes with confidence scores, animated meters, and analysis history |
| 04 | [**SummarAI**](https://ai-projects-flax.vercel.app/summarizer) | Multi-mode text summarizer — bullet points, paragraph, ELI5, and TL;DR, with word count reduction stats |
| 05 | [**LabelAI**](https://ai-projects-flax.vercel.app/dataLabeler) | Batch data labeling tool with custom schemas, few-shot examples, confidence scores, and CSV export |
| 06 | [**PromptLab**](https://ai-projects-flax.vercel.app/promptComparison) | Side-by-side prompt comparison — runs two system prompts in parallel and AI-analyzes what made the difference |

---

## Key AI Techniques Demonstrated

- **System prompts & personas** — CoachAI uses a structured system prompt to maintain a consistent coaching voice across multi-turn conversation
- **Structured JSON output** — ResumeAI, SentimentAI, and LabelAI all instruct the model to return strict JSON, which is then parsed and rendered into UI components
- **Few-shot prompting** — LabelAI lets you define labeled examples that get injected into the prompt at runtime to guide classification
- **Prompt mode switching** — SummarAI sends different instruction sets to the same model depending on the output format selected (bullets / paragraph / ELI5 / TL;DR)
- **Parallel API calls** — PromptLab fires both prompt variants simultaneously with `Promise.all` and then runs a third analysis call to compare the outputs
- **Multi-turn conversation** — CoachAI maintains a full `conversationHistory` array and passes it with every request

---

## Running Locally

Each app is a single HTML file. No install, no build step.

```bash
git clone https://github.com/aranotuchinedum2/aiProjects.git
cd aiProjects

# Open any file directly in your browser
open chatbot.html

# Or serve locally (avoids any CORS edge cases)
npx serve .
```

Then enter your [Anthropic API key](https://console.anthropic.com/) in the input at the top of each app. Keys are never stored — they live in memory only for the duration of your session.

---

## Project Structure

```
aiProjects/
├── index.html              # Portfolio landing page
├── chatbot.html            # CoachAI — fitness coach chatbot
├── resumeReviewer.html     # ResumeAI — resume gap analyzer
├── sentiment.html          # SentimentAI — sentiment analysis
├── summarizer.html         # SummarAI — multi-mode summarizer
├── dataLabeler.html        # LabelAI — batch data labeling tool
├── promptComparison.html   # PromptLab — prompt A/B comparison
├── vercel.json             # Clean URL config
└── README.md
```

---

## API & Model

All apps use the **Claude Sonnet 4** model (`claude-sonnet-4-20250514`) via direct browser calls to `api.anthropic.com/v1/messages` with the `anthropic-dangerous-direct-browser-access` header. This is intentional for portfolio/demo purposes — in production, API calls would route through a backend to keep keys private.

---

## License

MIT — use freely, build on top, credit appreciated.

---

*Built by Chinedum Aranotu · 2026*
