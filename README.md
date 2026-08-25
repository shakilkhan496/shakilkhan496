<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:635BFF,100:6366F1&height=210&section=header&text=Shakil%20Khan&fontSize=58&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=Full-Stack%20JavaScript%20Engineer%20%E2%80%A2%20Stripe%20Payments%20Expert&descAlignY=56&descAlign=50" width="100%"/>

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&pause=1200&color=6366F1&center=true&width=680&lines=React+%7C+Next.js+%7C+Node.js+%7C+MERN;Stripe+Payments+%26+Stripe+Connect+Specialist;Performance+%E2%80%A2+DX+%E2%80%A2+Scalability+%E2%80%A2+Clean+Architecture" alt="Typing intro"/>

<br/>

<img src="https://komarev.com/ghpvc/?username=shakilkhan496&style=for-the-badge&color=6366F1&label=PROFILE+VIEWS" alt="Profile views"/>
<img src="https://img.shields.io/github/followers/shakilkhan496?style=for-the-badge&color=6366F1&logo=github&label=FOLLOWERS" alt="GitHub followers"/>
<img src="https://img.shields.io/badge/dynamic/json?style=for-the-badge&color=6366F1&label=PUBLIC%20REPOS&query=%24.public_repos&url=https%3A%2F%2Fapi.github.com%2Fusers%2Fshakilkhan496" alt="Public repos"/>

</div>

<br/>

## 🧭 About Me

- 🚀 I build fast, accessible web & mobile experiences with **React**, **Next.js**, and **Node.js**.
- 🧩 I care about clean architecture, great developer experience, and systems that scale.
- 🌱 Currently deepening my knowledge of the Next.js App Router, RSCs, and caching strategies.
- 🤝 Open to freelance work and collaboration on React / Next.js / Node projects.
- 💳 **Stripe integration specialist** — subscriptions, one-time payments, and **Stripe Connect** (Standard / Express / Custom) set up end‑to‑end.

<br/>

## 🛠 Tech Stack

<div align="center">

<img src="https://skillicons.dev/icons?i=js,ts,react,nextjs,nodejs,express,mongodb,html,css,tailwind,bootstrap,redux&perline=6" alt="Languages & Frameworks"/>
<br/>
<img src="https://skillicons.dev/icons?i=git,github,vscode,figma,vercel,postman,linux&perline=6" alt="Tools & Platforms"/>

</div>

<details>
<summary><b>What I use day-to-day</b></summary>
<br/>

| Layer | Tools |
|---|---|
| **Frontend** | React 18, Next.js (App Router), Tailwind CSS, Redux Toolkit |
| **Backend** | Node.js, Express, REST APIs (OpenAPI), JWT Auth |
| **Database & Infra** | MongoDB (Mongoose), Vercel, GitHub Actions CI/CD |
| **Quality** | ESLint, Prettier, Vitest / Jest, Playwright |
| **Payments** | Stripe API, Stripe Connect, Webhooks |

</details>

<br/>

## 💳 Payments & Stripe

<div align="center">

![Stripe API](https://img.shields.io/badge/Stripe-API-635bff?style=for-the-badge&logo=stripe&logoColor=white)
![Subscriptions](https://img.shields.io/badge/Checkout-Subscriptions-635bff?style=for-the-badge)
![Connect](https://img.shields.io/badge/Connect-Platforms-635bff?style=for-the-badge)

</div>

- **Subscriptions** — products/prices, free trials, proration, metered billing, customer portal.
- **One-time payments** — Checkout, Payment Element, promo codes, taxes, invoices.
- **Stripe Connect** — Standard / Express / Custom, onboarding, payouts, destination & transfer charges.
- **Webhooks & reliability** — signature verification, idempotency keys, retry-safe flows.
- **Compliance** — SCA-ready, PCI-compliant flows via Elements / Checkout.

<details>
<summary><b>Quick demo code (Node/Next.js)</b></summary>

```ts
// /app/api/checkout/route.ts – one-time payment
import Stripe from 'stripe';
const stripe = new Stripe(process.env.STRIPE_SECRET_KEY!, { apiVersion: '2024-06-20' });

export async function POST() {
  const session = await stripe.checkout.sessions.create({
    mode: 'payment',
    line_items: [{ price: process.env.STRIPE_PRICE_ONE_TIME!, quantity: 1 }],
    success_url: `${process.env.NEXT_PUBLIC_URL}/success?session_id={CHECKOUT_SESSION_ID}`,
    cancel_url: `${process.env.NEXT_PUBLIC_URL}/cancel`,
  });
  return Response.json({ url: session.url });
}
```

```ts
// /app/api/subscribe/route.ts – subscription
export async function POST() {
  const session = await stripe.checkout.sessions.create({
    mode: 'subscription',
    line_items: [{ price: process.env.STRIPE_PRICE_SUBSCRIPTION!, quantity: 1 }],
    allow_promotion_codes: true,
    success_url: `${process.env.NEXT_PUBLIC_URL}/dashboard`,
    cancel_url: `${process.env.NEXT_PUBLIC_URL}/pricing`,
  });
  return Response.json({ url: session.url });
}
```

```ts
// /app/api/connect/onboard/route.ts – Connect Express onboarding link
export async function GET() {
  const account = await stripe.accounts.create({ type: 'express' });
  const link = await stripe.accountLinks.create({
    account: account.id,
    refresh_url: `${process.env.NEXT_PUBLIC_URL}/onboarding/refresh`,
    return_url: `${process.env.NEXT_PUBLIC_URL}/onboarding/return`,
    type: 'account_onboarding',
  });
  return Response.json({ url: link.url });
}
```

```ts
// /app/api/webhooks/stripe/route.ts – webhook
import { headers } from 'next/headers';

export async function POST(req: Request) {
  const sig = headers().get('stripe-signature')!;
  const raw = await req.text();
  let event;
  try {
    event = stripe.webhooks.constructEvent(raw, sig, process.env.STRIPE_WEBHOOK_SECRET!);
  } catch (err) {
    return new Response('Invalid signature', { status: 400 });
  }
  // handle event.type ...
  return new Response('ok');
}
```

</details>

<br/>

## 📈 GitHub Activity

> Generated automatically every 6 hours by the `metrics.yml` workflow in this repo — a static SVG committed to the repository, so it always renders (no shared third-party rate limits).

<div align="center">
  <img src="./github-metrics.svg" alt="GitHub metrics overview" width="100%"/>
</div>

<br/>

## 🏆 Trophies

<div align="center">
  <img src="https://github-profile-trophy.vercel.app/?username=shakilkhan496&theme=algolia&no-bg=true&no-frame=true&margin-w=10&row=1" alt="GitHub trophies"/>
</div>

<br/>

## 🐍 Contribution Snake

> Generated automatically every day by the `snake.yml` workflow, which commits the SVG to an `output` branch.

<div align="center">
  <img src="https://raw.githubusercontent.com/shakilkhan496/shakilkhan496/output/github-contribution-grid-snake-dark.svg#gh-dark-mode-only" alt="Contribution snake (dark)"/>
  <img src="https://raw.githubusercontent.com/shakilkhan496/shakilkhan496/output/github-contribution-grid-snake.svg#gh-light-mode-only" alt="Contribution snake (light)"/>
</div>

<br/>

## 📫 Connect

<div align="center">

[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:shakilkhan496@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/shakilkhan496)
[![Portfolio](https://img.shields.io/badge/Portfolio-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://shakil-khan-portfolio.vercel.app/)

</div>

<br/>

<div align="center">
<i>🚀 Let's build, monetize, and scale with Stripe & Next.js!</i>
</div>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:6366F1,100:635BFF&height=100&section=footer" width="100%"/>
