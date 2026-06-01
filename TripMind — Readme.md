TripMind — AI-Powered Travel Agent ✈️🌴

TripMind is a high-performance, zero-friction AI travel agent application designed for seamless travel planning and side-by-side deal comparisons. Users can search flights, discover hotels, build full day-by-day itineraries, and check visa advisories instantly without any sign-up flows or complex configurations.

This repository organizes the TripMind codebase into a production-ready, easily deployable structure.

🏗️ Repository Architecture

Your project folder should be structured as follows:

tripmind/
├── .gitignore          # Prevents tracking temporary local files/dependencies
├── LICENSE.md          # Open-source MIT License
├── README.md           # Repository documentation and deployment guide (This file)
├── index.html          # Single-file static web client (Frontend with Kiwi.com integration)
└── worker.js           # Cloudflare Serverless Worker (Groq API Gateway with Failover Router)


🚀 Features

Groq-Powered Multi-Model Routing: A backend worker that communicates with Groq's high-speed API and automatically falls back to secondary models (llama-3.3-70b-versatile, qwen/qwen3-32b, etc.) if a rate limit (429) or server error is hit.

Forgiving Kiwi.com Integration: Dynamic flight search redirection to Kiwi.com that accepts loose free-text names (like "Southeast Asia" or "anywhere") without throwing 404 errors.

Side-by-Side Competitor Pricing Hub: Elegant pricing cards embedded dynamically within chat bubbles to compare budget and luxury options for flights and accommodation.

Cookie-Based Client Memory: Remembers the user's last searched destination across sessions and automatically updates suggested start prompts.

Secure Key Masking: No API keys are exposed to the client side.

⚡ Quick Start & Deployment Guide

Follow these steps to deploy TripMind to production in less than 5 minutes.

Step 1: Deploy the Serverless Backend (Cloudflare)

Sign up for a free account at Cloudflare Workers.

Create a new Worker (e.g., named tripmind-api).

Copy the contents of your worker.js file and paste it into the Cloudflare Worker script editor.

Go to Settings > Variables inside your Worker's panel.

Click Add Variable:

Type: Secret

Name: GROQ_API_KEY

Value: Your Groq API Key (obtain a key from the Groq Console)

Save and Deploy. Copy your public worker .workers.dev URL (e.g., https://tripmind-api.yourname.workers.dev).

Step 2: Configure the Frontend

Open index.html.

Locate the WORKER_URL configuration constant near the top of the <script> section:

const WORKER_URL = 'https://your-worker-subdomain.workers.dev';


Replace the placeholder with your actual Cloudflare Worker URL.

Step 3: Configure Affiliate Tracking (How to Monetise)

To earn commissions from bookings made on your platform:

Register for your chosen travel partner networks:

Booking.com Affiliate Program

Viator Partner Program

World Nomads Partners

Travelpayouts (for Kiwi.com integration)

Open index.html and scroll to the createAffiliateCard() function.

Replace the placeholder ID variables with your actual affiliate campaign, partner, or marker IDs.

Step 4: Host Your Site

Drag and drop your updated index.html file onto Netlify or connect the repository to Vercel for instant, free static hosting.

Launch, run campaigns, and share!

📄 License

This project is open source and available under the MIT License.