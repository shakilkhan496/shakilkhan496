<!-- Views -->

<p align="right">
  <img src="https://komarev.com/ghpvc/?username=shakilkhan496&style=flat-square&color=blue" alt="Profile views"/>
</p>

<h1 align="center">Hi there 👋, I’m <b>Shakil Khan</b></h1>

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&pause=1200&width=680&lines=Full-Stack+JavaScript+Engineer;React+%7C+Next.js+%7C+Node.js+%7C+MERN;Performance+%E2%80%A2+DX+%E2%80%A2+Scalability+%E2%80%A2+Clean+Architecture" alt="Typing intro"/>
</p>

<p align="center">
  <a href="https://github.com/shakilkhan496">
    <img src="https://img.shields.io/github/followers/shakilkhan496?style=social" alt="GitHub followers"/>
  </a>
  <a href="https://github.com/shakilkhan496?tab=repositories">
    <img src="https://img.shields.io/badge/Public%20Repos-dynamic?logo=github&label=Public%20Repos&query=%24.public_repos&url=https%3A%2F%2Fapi.github.com%2Fusers%2Fshakilkhan496" alt="Public repos"/>
  </a>
  <a href="https://github.com/shakilkhan496">
    <img src="https://img.shields.io/badge/Following-dynamic?logo=github&label=Following&query=%24.following&url=https%3A%2F%2Fapi.github.com%2Fusers%2Fshakilkhan496" alt="Following"/>
  </a>
  <a href="https://stripe.com">
    <img src="https://img.shields.io/badge/Payments-Stripe-635bff?logo=stripe&logoColor=white" alt="Stripe"/>
  </a>
</p>

---

## 🧭 About Me

* 🚀 I build fast, accessible web & mobile experiences.
* 🧩 I focus on clean architecture, great DX, and scalable systems.
* 🌱 Exploring advanced Next.js (App Router, RSC, caching) + testing.
* 🤝 Open to freelance & collaboration on React / Next.js / Node projects.
* 💳 **Stripe integration expert** — subscriptions, one‑time payments, and **Stripe Connect** (Standard/Express/Custom) set up seamlessly.

---

## 🛠 Tech Stack

<p align="center">
  <img src="https://skillicons.dev/icons?i=js,ts,react,nextjs,nodejs,express,mongodb,html,css,tailwind,bootstrap,redux" alt="Languages & Frameworks"/>
</p>
<p align="center">
  <img src="https://skillicons.dev/icons?i=git,github,vscode,figma,vercel,postman,linux" alt="Tools & Platforms"/>
</p>

<details>
  <summary><b>What I use day-to-day</b></summary>
  <br/>
  <ul>
    <li>Frontend: React 18, Next.js (App Router), Tailwind, Redux Toolkit</li>
    <li>Backend: Node.js, Express, REST (with OpenAPI), JWT</li>
    <li>DB & Infra: MongoDB (Mongoose), Vercel, CI/CD (GitHub Actions)</li>
    <li>Quality: ESLint, Prettier, Vitest/Jest, Playwright</li>
  </ul>
</details>

---

## 💳 Payments & Stripe

<p align="center">
  <img src="https://img.shields.io/badge/Stripe-API-635bff?logo=stripe&logoColor=white" alt="Stripe API"/>
  <img src="https://img.shields.io/badge/Checkout-%20Subscriptions-%23635bff" alt="Stripe Checkout Subscriptions"/>
  <img src="https://img.shields.io/badge/Connect-Platforms-%23635bff" alt="Stripe Connect"/>
</p>

* **Subscriptions**: products/prices, free trials, proration, metered billing, customer portal.
* **One‑time payments**: Checkout, Payment Element, promo codes, taxes, invoices.
* **Stripe Connect**: Standard/Express/Custom, onboarding, payouts, destination/transfer charges.
* **Webhooks & Reliability**: signature verification, idempotency keys, retry‑safe flows.
* **Compliance**: SCA-ready, PCI‑compliant flows via Elements/Checkout.

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
// /app/api/webhooks/stripe/route.ts – webhook (Edge-disabled for crypto libs)
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

---

## 📈 Live Stats & Charts

<!-- Main stat cards -->

<p align="center">
  <img height="175"
       src="https://github-readme-stats.vercel.app/api?username=shakilkhan496&show_icons=true&theme=radical&include_all_commits=true&count_private=true&rank_icon=github&hide_border=true&cache_seconds=7200"
       alt="GitHub stats"/>
  <img height="175"
       src="https://streak-stats.demolab.com?user=shakilkhan496&theme=radical&hide_border=true"
       alt="Contribution streak"/>
</p>

<!-- Current year badges (powered by your workflow + public gist) -->

<p align="center">
  <img src="https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/shakilkhan496/8837a29fd66377432653da3be25c98d4/raw/commits.json" alt="Commits (YTD)"/>
  <img src="https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/shakilkhan496/8837a29fd66377432653da3be25c98d4/raw/contributions.json" alt="Contributions (YTD, incl. private)"/>
</p>

<!-- Top languages -->

<p align="center">
  <img height="175"
       src="https://github-readme-stats.vercel.app/api/top-langs/?username=shakilkhan496&layout=compact&theme=radical&langs_count=8&hide_border=true&cache_seconds=7200"
       alt="Top languages"/>
</p>

<!-- Activity graph (chart) -->

<p align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=shakilkhan496&theme=react-dark&area=true&hide_border=true"
       alt="Activity Graph"/>
</p>

<!-- Summary cards grid -->

<p align="center">
  <img src="https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username=shakilkhan496&theme=radical" alt="Profile details"/>
</p>
<p align="center">
  <img src="https://github-profile-summary-cards.vercel.app/api/cards/repos-per-language?username=shakilkhan496&theme=radical" alt="Repos per language"/>
  <img src="https://github-profile-summary-cards.vercel.app/api/cards/most-commit-language?username=shakilkhan496&theme=radical" alt="Most commit language"/>
</p>
<p align="center">
  <img src="https://github-profile-summary-cards.vercel.app/api/cards/stats?username=shakilkhan496&theme=radical" alt="Stats card"/>
  <img src="https://github-profile-summary-cards.vercel.app/api/cards/productive-time?username=shakilkhan496&theme=radical&utcOffset=6" alt="Productive time (UTC+6)"/>
</p>

<!-- Lowlighter Metrics (generated by your metrics.yml) -->

<p align="center">
  <img src="/github-metrics.svg" alt="Metrics overview"/>
</p>

---

## 🏆 Achievements & Fun

<p align="center">
  <img src="https://github-profile-trophy.vercel.app/?username=shakilkhan496&theme=algolia&no-bg=true&no-frame=true&margin-w=10" alt="GitHub trophies"/>
</p>

<p align="center">
  <img src="https://github.com/1999AZZAR/1999AZZAR/blob/readme/resources/grid-snake.svg" alt="Snake animation"/>
</p>

---

## 📝 Quote of the Day

<p align="center">
  <img src="https://quotes-github-readme.vercel.app/api?type=horizontal&theme=radical" alt="Quote"/>
</p>

---

## 📫 Connect

* Email: <a href="mailto:shakilkhan496@gmail.com">[shakilkhan496@gmail.com](mailto:shakilkhan496@gmail.com)</a>
* LinkedIn: <a href="https://linkedin.com/in/shakilkhan496">linkedin.com/in/shakilkhan496</a>
* Portfolio: <a href="https://shakil-khan-portfolio.vercel.app/">shakil-khan-portfolio.vercel.app</a>

---

<p align="center"><i>🚀 Let’s build, monetize, and scale with Stripe & Next.js!</i></p>
