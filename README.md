# Swiggy Copilot 🚀

> **Note:** This repository contains the codebase for the **demo site** of the Swiggy Copilot project.

Swiggy Copilot is a natural language order assistant for Swiggy. A user types one messy sentence — *"20 mins, under ₹250, high protein, no paneer, something like last week"* — and the app parses every constraint, back-calculates delivery ETAs against meeting schedules, cross-references order history, and returns a ranked shortlist in under 3 seconds. It collapses the typical 5–8 minute browse-and-filter session into a single tap.

## 🌟 Key Features

- **Natural Language Parsing**: Uses Claude (`claude-sonnet`) to extract structured constraints in JSON format (deadline, budget, exclusions, macros, history flag).
- **Smart Filtering**: Back-calculates ETAs, searches price ranges, and handles macro-level dish filtering via sequential API calls.
- **Intelligent Ranking**: Ranks results using a custom scoring function based on `(ETA fit × budget headroom × protein match × history similarity)`.
- **Seamless Integrations**: 
  - Primary: **Swiggy Food**
  - Stretch Goal: **Swiggy Instamart** (for ingredient gap ordering)
- **One-Tap Ordering**: The top result is pre-loaded into the user's cart via `update_food_cart`. After user confirmation, `place_food_order` is fired.

## 🛠️ Tech Stack & Architecture

- **Frontend**: React
- **Backend / Middleware**: Node.js
- **AI/LLM**: Claude (claude-sonnet)
- **Security**: Auth tokens are stored securely server-side; authentication redirect flows are handled fully through the backend.

## 🚀 Workflow

1. **Input**: User provides natural language constraints.
2. **LLM Extraction**: Claude extracts a structured JSON constraint object.
3. **Availability Check**: Sequential calls to `search_restaurants` (filtered by ETA/price) and `search_menu` (for macro filtering).
4. **Ranking & Scoring**: AI scores the top matches.
5. **Checkout**: Top match pre-loaded -> User confirms -> Order placed.

## 📄 License

This project is intended for demonstration purposes. Provide any applicable proprietary licenses or open-source licenses as needed.
