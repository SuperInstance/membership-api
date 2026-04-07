# Membership API

A minimal API for handling tiered memberships and usage billing within the Cocapn Fleet. You run it, you control it.

---

## Why this exists
Third-party billing services add complexity, cost, and lock-in. This provides the core logic for memberships—tiers, quotas, and payments—as open-source code you deploy yourself. You keep full control over your data and revenue.

## What it is
A Cloudflare Worker that uses KV storage. It manages member tiers, tracks request usage against daily quotas, and handles subscription billing via Stripe. All configuration is in your code.

## Quick start
1.  **Fork this repository.** This is working code, not a library.
2.  **Deploy to Cloudflare Workers:**
    ```bash
    npx wrangler deploy
    ```
3.  **Edit the tier definitions** in `src/tiers.ts` to set your quotas, prices, and features.
4.  (Optional) **Add your Stripe keys** as secrets to enable live payments.

A public reference instance is available for testing: [https://the-fleet.casey-digennaro.workers.dev/membership](https://the-fleet.casey-digennaro.workers.dev/membership)

## What it does
*   **Defines membership tiers** (Free, Standard, Gold, Enterprise by default) with configurable daily request quotas and transparent, cost-plus pricing.
*   **Tracks usage** and attributes costs per request, providing itemized logs.
*   **Manages subscriptions** through integrated Stripe checkout and webhook handlers.
*   **Binds resources** like domains or fleet vessels to specific member accounts.
*   **Stores all state** in Cloudflare KV. There are zero external runtime dependencies.

## One limitation
This is built for the Cloudflare Workers ecosystem. If you're not using Workers and KV, you'll need to adapt the storage layer.

## Keep your revenue
When you add your Stripe keys, all payment processing runs in your worker. Stripe's fees apply, but no additional cut is taken.

---

MIT License  
Superinstance & Lucineer (DiGennaro et al.)

<div align="center">
  <a href="https://the-fleet.casey-digennaro.workers.dev">The Fleet</a> • <a href="https://cocapn.ai">Cocapn</a>
</div>