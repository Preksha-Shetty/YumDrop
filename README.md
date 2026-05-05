# YumDrop 🍜

**AI-Powered Social Recipe Platform**

## 🌟 Overview
YumDrop is a mobile-first, AI-powered platform designed to close the **"Ingredient-Recipe Gap."** Instead of asking "What do I want to cook?", YumDrop asks **"What can I cook right now with what I have?"** It targets university students and young professionals who face limited pantries, limited cooking skills, and a desire to stay connected to their cultural food heritage.

## 🚀 Key Features
- **Pantry Magic:** Tap the ingredients you have (e.g., eggs, rice, soy sauce), and the AI reasons across your stash to find perfect or close matches.
- **Yum AI Chat:** A real-time cooking assistant that answers "mid-cook" questions (e.g., "Why is my rice soggy?" or "What can I use instead of soy sauce?").
- **Drop & Cook:** A beginner-friendly, step-by-step adaptive cooking mode that breaks down complex techniques into manageable actions.
- **Kitchen Stories:** A community-driven space to document and share family recipes, preserving oral culinary traditions and cultural heritage.

## 🛠️ Technical Stack & AI Implementation
This project transitions LLM theory into a grounded, functional business application using:
- **Claude API:** Powers the core reasoning engine for "Pantry Magic" and the conversational assistant.
- **RAG (Retrieval-Augmented Generation):** A local recipe knowledge base grounds AI outputs to ensure accuracy and prevent "hallucinated" recipes.
- **Live Web Search:** Enables discovery of regional, cultural, and niche recipes beyond the static database.
- **Prompt Engineering:** Strict JSON formatting ensures AI outputs are parseable by the front-end interface.
- **Fallback Logic:** A local scoring algorithm maintains usability even during API latency or failures.

## 🎯 Problem Space
- **The Ingredient Gap:** Traditional apps assume a full pantry (10-15 ingredients), whereas students typically have 4-8 items.
- **The Confidence Deficit:** 61% of beginner cooks feel overwhelmed by static recipe cards that offer no feedback.
- **Cultural Erasure:** Mainstream platforms underrepresent non-Western cuisines; YumDrop provides a digital home for family recipes and oral traditions.
