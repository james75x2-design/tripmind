[VoyageFlow_README.md](https://github.com/user-attachments/files/28512622/VoyageFlow_README.md)
# VoyageFlow — AI Travel Agent ✈️
**A free, zero-friction AI travel agent — no sign-up, no API key, instant trip planning.**

![Status](https://img.shields.io/badge/status-active-brightgreen) ![Version](https://img.shields.io/badge/version-1.0-blue) ![License](https://img.shields.io/badge/license-MIT-green) ![Powered by Groq](https://img.shields.io/badge/powered%20by-Groq-orange)

---

## What Is VoyageFlow?

VoyageFlow is an AI-powered travel planning assistant that helps users plan complete trips instantly — flights, hotels, itineraries, visa requirements, packing lists, and budget breakdowns — all in one conversation.

No sign-up. No API key. No friction. Just start planning.

---

## 🚀 Live Demo

👉 **[Try VoyageFlow Live](https://your-live-link-here)**

---

## ✨ Features

- **Complete trip planning** — flights, hotels, itineraries, budgets, visa requirements
- **Day-by-day itineraries** — real, specific suggestions for any destination
- **Side-by-side pricing** — compare budget vs luxury options for flights and hotels
- **Smart model routing** — automatically falls back to secondary Groq models if rate limited
- **Cookie-based memory** — remembers your last destination across sessions
- **Secure backend** — API key never exposed to the client
- **Affiliate integration** — flight and hotel booking links via Kiwi.com, Booking.com, Viator
- **Zero configuration** — works immediately on load, no setup required

---

## 🏗️ Repository Structure

```
voyageflow/
├── index.html      # Frontend — single-file static web client
├── worker.js       # Cloudflare Worker — Groq API gateway with fallback router
├── README.md       # This file
└── .gitignore      # Prevents tracking local dependencies and secrets
```

---

## 🤖 AI Backend — Groq Multi-Model Fallback

VoyageFlow uses a Cloudflare Worker as a secure proxy to Groq's API. If a model hits a rate limit, it automatically falls back through this priority chain:

1. `openai/gpt-oss-120b` — highest quality, try first
2. `llama-3.3-70b-versatile` — strong general model
3. `qwen/qwen3-32b` — fast and capable
4. `meta-llama/llama-4-scout-17b-16e-instruct` — efficient fallback
5. `llama-3.1-8b-instant` — ultra-fast final fallback

If all models are rate limited, the user sees a friendly retry message.

---

## ⚡ Deployment Guide

### Step 1 — Deploy the Cloudflare Worker Backend

1. Sign up free at [cloudflare.com](https://workers.cloudflare.com)
2. Create a new Worker (e.g. `voyageflow-api`)
3. Paste the contents of `worker.js` into the Worker editor
4. Go to **Settings → Variables → Add Variable:**
   - Name: `GROQ_API_KEY`
   - Type: **Secret**
   - Value: Your Groq API key from [console.groq.com](https://console.groq.com)
5. Save and Deploy
6. Copy your `.workers.dev` URL

### Step 2 — Configure the Frontend

1. Open `index.html`
2. Find `const WORKER_URL = 'https://your-worker-subdomain.workers.dev'`
3. Replace with your actual Cloudflare Worker URL

### Step 3 — Deploy the Frontend

Drag and drop `index.html` onto [Netlify](https://netlify.com) or connect to [Vercel](https://vercel.com) for free static hosting.

### Step 4 — Configure Affiliate Links *(Optional)*

To earn commissions from bookings:

1. Register with your chosen travel affiliate networks:
   - [Travelpayouts](https://partners.travelpayouts.com) — Kiwi.com flights
   - [Booking.com Affiliate](https://partners.booking.com) — hotels
   - [Viator Partners](https://partners.viator.com) — tours and activities
   - [World Nomads](https://worldnomads.com/affiliate) — travel insurance
2. Open `index.html` and find the `createAffiliateCard()` function
3. Replace placeholder IDs with your actual affiliate IDs

---

## 🔒 Security

- Groq API key is stored as an encrypted Cloudflare environment variable
- Key is never exposed to the frontend or visible in browser source
- All API calls are proxied through the Cloudflare Worker
- No user data is stored or logged

---

## 🛠️ How It's Built

- **Frontend** — Single-file HTML with vanilla JavaScript, no framework dependencies
- **Backend** — Cloudflare Worker (serverless, free tier: 100,000 req/day)
- **AI** — Groq API with multi-model fallback routing and automatic retry logic
- **Memory** — Cookie-based client memory for returning users
- **Affiliate** — Dynamic pricing cards with Kiwi.com, Booking.com, Viator integration

---

## 🗺️ Roadmap

- [ ] Mobile-responsive layout improvements
- [ ] Multi-city trip planning support
- [ ] Saved itineraries and trip history
- [ ] Currency conversion integration
- [ ] Real-time flight availability via API

---

## 👤 About

**James Earl C. Felipe**
AI Solutions Designer | Enterprise IT Professional
Building AI tools that solve real human problems.

🔗 [LinkedIn](https://linkedin.com/in/james-earl-felipe-13359665) · 📧 james75x2@gmail.com

---

## 📄 License

MIT License — Copyright (c) 2026 James Earl C. Felipe

Free to use, modify, and share with attribution.

---

*© 2026 James Earl C. Felipe. Built with Claude and Gemini. Designed for travellers.*
