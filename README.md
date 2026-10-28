# Academic Writing Copilot

**Interactive MVP for an AI Builder / Product portfolio**

Academic Writing Copilot helps university students review academic paragraphs through prioritized, evidence-based writing feedback. It is inspired by research and experience in language education, academic writing support, and technology-enhanced learning.

## Live demo options

**Static prototype (no setup):** open `index.html` in a browser, or publish it with GitHub Pages. This mode uses **transparent local heuristics**, not a large language model. It works on arbitrary input but detects only a small set of patterns.

**Optional real AI backend (local):** requires Python and an API key. The frontend calls `/api/analyze`; when a configured backend responds, the app labels results **AI model analysis**. If unavailable, the interface falls back to the local heuristic prototype.

```bash
python -m venv .venv
source .venv/bin/activate       # Windows: .venv\\Scripts\\activate
pip install -r requirements.txt
export OPENAI_API_KEY="YOUR_KEY" # Windows PowerShell: $env:OPENAI_API_KEY="YOUR_KEY"
uvicorn app:app --reload
```

Visit http://127.0.0.1:8000. API usage may incur costs. **Never commit API keys or place them in browser JavaScript.**

## Core features

1. Input academic paragraphs and load a sample.
2. Analyze text and prioritize feedback by issue category and severity.
3. Review specific evidence, explanations, and revision suggestions.
4. Compare original and revised drafts and word counts.
5. Rate usefulness (session-only; not persisted or transmitted).

## Problem and target user

Students often receive generic writing feedback and struggle to decide what to revise first. The MVP emphasizes *actionable explanations* rather than automatically replacing the student's writing. Target users: university students and English language learners.

## Product decisions

- **MVP scope:** paragraph-level feedback, not full-document editing.
- **Feedback UX:** evidence + explanation + suggestion; high-priority issues first.
- **Privacy:** static mode processes text locally; AI mode sends it to a configured server/provider. Do not submit confidential or unauthorized student writing.
- **Academic integrity:** no fabricated citations or full-essay ghostwriting.
- **Limitations:** heuristic analysis is shallow; AI analysis may be wrong; no persistent accounts or telemetry; revision comparison is textual, not a quality score.

## Architecture

`Browser UI (HTML/CSS/JS) -> /api/analyze (FastAPI) -> model provider` (optional). Without a backend, local rules run in-browser.

## Evaluation plan (not completed)

- Assemble 20 consented or synthetic paragraphs with manually annotated issues.
- Measure precision of detected issues and proportion of actionable suggestions.
- Collect 1–5 helpfulness ratings from 5 pilot users with consent.
- Measure response latency and document failure modes.
- Prioritize next iterations based on results, not assumed improvements.

## Suggested roadmap

- v0.1: interactive local prototype (included).
- v0.2: model-backed structured feedback (optional backend included; requires configuration and validation).
- v0.3: real user evaluation and revised prompts.
- v0.4: better revision diff, multilingual support, and privacy controls.

## Authorship and disclosure

This portfolio prototype was developed with AI-assisted code generation and documentation. The applicant should review, run, test, and be able to explain the implementation before presenting it as their own project. No user testing or performance improvement is claimed without evidence.

## Screenshots

Add a screenshot of the interface and one of the analysis results after running the demo.
