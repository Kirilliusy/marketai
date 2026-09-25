# MarketAI

AI-powered SaaS that generates marketplace product listings (Wildberries / Ozon / Amazon) from a short brief. Built solo, end to end — from the LLM prompt pipeline to auth, billing, and deployment.

**Live:** https://marketplace-saas-nine.vercel.app/ · **Stack:** Next.js 16 · TypeScript · Supabase · Claude (Anthropic SDK) · Stripe · YooKassa

---

## What it does

- **AI listing generation** — turns a product brief into a ready-to-publish marketplace card (title, description, bullets) using Claude via the Anthropic SDK.
- **Try-before-signup demo** — a public demo endpoint lets visitors test generation before creating an account.
- **Accounts & auth** — Supabase authentication with OAuth callback flow; personal dashboard per user.
- **Dual billing** — subscription checkout through both **Stripe** (international) and **YooKassa** (Russian market), each with its own webhook handler.

## Tech

| Layer | Choice |
|-------|--------|
| Framework | Next.js 16 (App Router) |
| Language | TypeScript |
| AI | Claude — `@anthropic-ai/sdk` |
| Data & Auth | Supabase (Postgres, Auth) |
| Payments | Stripe + YooKassa (webhooks) |
| Styling | Tailwind CSS v4 |
| Hosting | Vercel |

## Architecture

```
app/
  api/
    generate/       # Claude generation endpoint
    demo/           # public demo generation
    stripe/         # checkout + webhook
    yookassa/       # checkout + webhook
  auth/             # login + OAuth callback
  dashboard/        # authed user area
lib/                # Supabase, Claude, billing clients
supabase/           # schema / migrations
```

## Running locally

```bash
npm install
cp .env.local.example .env.local   # fill in your keys
npm run dev
```

Requires keys for Supabase, Anthropic, and Stripe/YooKassa (see `.env.local.example`).

---

*Solo project — product, engineering, and deployment. Part of my portfolio: [more projects](https://github.com/kzhigalov-dev).*
