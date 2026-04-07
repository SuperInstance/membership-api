You don't need a complex third-party service to manage access for your agent fleet.

# Membership API

Tiered access, seat management, and transparent billing built for the Cocapn Fleet protocol.

---

## Why it Exists

When your open-source agent project gains users, you need a way to manage access and billing. This API provides that core membership logic so you don't have to rebuild it. It's designed to be forked and owned by you.

## Try it Live

Test the public instance:
https://the-fleet.casey-digennaro.workers.dev

You can call tier endpoints and inspect quota schemas.

## Quick Start

1.  **Fork this repository.** This is designed to be modified.
2.  ️ Clone your fork and deploy to Cloudflare Workers: `npx wrangler deploy`
3.  Edit tier rules, pricing, and limits directly in `src/config.ts`. It's just TypeScript.

## What It Is

A stateless API (~1200 lines of TypeScript) running on Cloudflare Workers. It manages membership tiers, request quotas, and billing associations. All state is stored in Cloudflare KV; there are no external database dependencies.

## What It Does

*   **Manages Tiers:** Provides four pre-configured tiers (Free, Standard, Gold, Enterprise) with daily and monthly quotas.
*   **Tracks Usage:** Logs requests with transparent cost attribution. You see the exact markup applied.
*   **Handles Billing:** Includes Stripe webhook handlers and subscription logic. You add your own keys.
*   **Binds Resources:** Associate domains, agent vessels, and storage with member accounts.
*   **Composes Natively:** Works with other services in the Cocapn Fleet.

## One Limitation

This API uses Cloudflare KV for storage. It's excellent for metadata and quotas but is not a relational database. Complex reporting or high-volume transaction logging would need a separate service.

## Enable Live Payments

To accept payments, set your Stripe keys as environment variables using `wrangler secret put`. All checkout and subscription logic is included. You keep 100% of your revenue.

## Philosophy

**Fork-first.** You are meant to run your own modified version. Zero lock-in, zero runtime dependencies, and no hidden platform. All pricing and business logic is in your code.

## Contributing

Fork the repository and make the changes you need. If you build something that would benefit others, consider opening a pull request.

## License

MIT License

Superinstance & Lucineer (DiGennaro et al.)

---

<div align="center">
  <a href="https://the-fleet.casey-digennaro.workers.dev">The Fleet</a> • <a href="https://cocapn.ai">Cocapn</a>
</div>