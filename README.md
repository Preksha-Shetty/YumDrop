# YumDrop 🍜 — AI-Powered Social Recipe Platform

## MBA Applied AI Capstone Project — MGS636

### Team
- Preksha Shetty
- Rakib Rahman  
- Satya Jeetu Ganguri

---

## What is YumDrop?

YumDrop is a mobile-first AI-powered social recipe sharing platform for university students and beginner cooks. It matches available ingredients to recipes using RAG (Retrieval-Augmented Generation) and live web search, and guides users through cooking with step-by-step AI assistance.

---

## How to Run

This is a single-file web app. No installation, no build step, no server required.

1. Open `index.html` in any modern browser (Chrome, Firefox, Safari, Edge)
2. That's it.

> **Note:** The AI features (Pantry Magic matching, Yum AI Chat) require an Anthropic API key. The app calls the API directly from the browser. For production use, route calls through a secure backend proxy.

---

## Adding Your Anthropic API Key

The app calls `https://api.anthropic.com/v1/messages` directly. To enable AI features:

1. Open `index.html` in a text editor
2. The fetch call is in the `runMatch()` and `doSend()` functions in the `<script>` section
3. Add a header: `"x-api-key": "YOUR_KEY_HERE"` to the fetch headers object

Without a key, the app falls back to a local ingredient-overlap scoring algorithm automatically — so the demo still works.

---

## AI Architecture

| Component | Technology |
|---|---|
| LLM | Anthropic Claude (claude-sonnet-4-20250514) |
| RAG Layer | Full-context KB injection on every API call |
| Web Search | web_search_20250305 tool |
| Fallback | Local ingredient overlap scoring |
| Source Attribution | SOURCES: tag parsed from every response |

### RAG Knowledge Base
6 seed recipes, each with: title, emoji, cultural origin, ingredients, step-by-step instructions (with timers and AI tips), personal story narrative, creator attribution, and engagement stats.

### Key Prompts

**Pantry Magic (AI Matcher):**
```
You are YumDrop's AI Recipe Matcher. Use this knowledge base:
[KB INJECTED]
Return ONLY a JSON array (no markdown). Each object:
{"title":str, "emoji":str, "matchPct":num, "matchType":"perfect"|"close"|"stretch",
 "missingIngredients":str[], "aiSwap":str, "origin":str, "time":str, "reason":str}
Return 4-6 matches sorted by matchPct. Include 1 creative web-inspired recipe.
```

**Yum AI Chat:**
```
You are Yum AI — a fun, energetic cooking assistant for students.
[KB INJECTED]
Context: User is cooking "[RECIPE]" step [N].
Keep replies 2-3 sentences. End with: SOURCES: [KB / Web / both]
```

---

## Features

### 🏠 Home — Reel Feed
- TikTok-style vertical video cards with recipe content
- Instagram Stories ring row of creator profiles
- Filter tabs: For You, Campus, Stories, Quick
- Like, share, save, duet actions on each reel

### ✨ Pantry Magic — AI Ingredient Matcher
- Tap-to-select ingredient chips
- AI matches ingredients against KB + web search
- Ranked results: perfect / close / stretch
- AI swap suggestions for missing ingredients
- Animated loading states with step-by-step progress

### 🍳 Drop & Cook — Guided Cooking Mode
- Step-by-step recipe walkthrough
- Live countdown timer per step
- Per-step AI tips (purple callout card)
- Dot navigation — jump to any step
- Rotating step badge colors

### 🤖 Yum AI Chat — Conversational AI
- Full RAG + web search on every message
- Source attribution tags on every response (KB / Web)
- Quick-reply chips for common questions
- Context-aware (knows current recipe and step)
- Typing indicator with animated dots

### 🎬 Camera / Record Screen
- Simulated viewfinder with grain and grid overlay
- Record button with live timer and blinking REC indicator
- Speed controls (0.3x — 3x)
- Camera effects, flip, flash controls
- Mode switcher: Photo / Video / Reel / LIVE / Duet / Collab
- Auto-returns to feed after recording

### 👤 Creator Profile
- Stats: drops, followers, likes, views
- Monetization milestone progress bar (5k likes)
- 3x3 video grid (like TikTok/Instagram profile)
- Book a cook session → connects to Yum AI Chat

---

## File Structure

```
yumdrop_source/
├── index.html      ← Entire app (HTML + CSS + JS, single file)
└── README.md       ← This file
```

---

## Tech Stack

- **Frontend:** Vanilla HTML, CSS, JavaScript (no framework)
- **Fonts:** Clash Display, Bricolage Grotesque, DM Mono (Google Fonts)
- **AI:** Anthropic Messages API (claude-sonnet-4)
- **No build tools, no npm, no dependencies**

---

## Known Limitations (PoC)

- API key is client-side — use a backend proxy for production
- RAG uses full-context injection — scale to vector embeddings for >100 recipes
- No persistent storage — pantry and chat reset on refresh
- Camera recording is simulated (no actual MediaStream API)
- 6 seed recipes — production would need a real database

---

*MGS636 Applied AI for Managers · Spring 2025*
