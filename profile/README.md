<div align="center">

<img src="https://raw.githubusercontent.com/SlaukoScript/.github/main/assets/logo.png" alt="SlaukoScript" width="600" />

<br />
<br />

**A clean creator-moderation platform foundation**

[![Website](https://img.shields.io/badge/Website-slaukoscript.com-F97316?style=for-the-badge&logo=googlechrome&logoColor=white)](https://slaukoscript.com)
[![Dashboard](https://img.shields.io/badge/Dashboard-mod.slaukoscript.com-FF6B4A?style=for-the-badge&logo=react&logoColor=white)](https://mod.slaukoscript.com)
[![Feedback](https://img.shields.io/badge/Feedback-Bug%20Reports%20%26%20Ideas-22C55E?style=for-the-badge&logo=github&logoColor=white)](https://github.com/SlaukoScript/feedback/issues)

---

</div>

## What SlaukoScript Is

SlaukoScript is a creator-moderation platform for teams that protect communities across Discord, Twitch, and future managed-provider integrations.

The active platform now lives in one clean monorepo:

- [`slaukoscript`](https://github.com/SlaukoScript/slaukoscript): React + Vite dashboard, Astro landing site, Hono API, worker runtime, shared TypeScript packages, local Docker runtime, tests, and smoke gates.
- [`feedback`](https://github.com/SlaukoScript/feedback): public bug reports, feature requests, and community feedback.
- [`archive`](https://github.com/SlaukoScript/archive): read-only v1 snapshots of the previous multi-repo setup.

## Current Architecture

```text
apps/
  landing      Astro static site
  dashboard    React + Vite creator workspace
  api          Hono HTTP API
  worker       Background processing runtime

packages/
  contracts    Runtime schemas and shared TypeScript contracts
  core         Framework-neutral helpers and brand assets
  client       Browser API client and React domain hooks
  ui           Reusable React UI primitives and tokens
  billing      Dodo catalog, product lookup, and entitlement helpers
  platform     Organizations, modules, integrations, moderation domain logic
  db           Database client and repositories
```

## Runtime Direction

The platform is being brought up as a real local runtime first: Postgres, Redis, migrations, seeds, API health/readiness, worker queues, dashboard, landing page, billing lookup, and moderation smoke coverage.

## Tech Stack

`TypeScript` `pnpm` `Turbo` `React` `Vite` `Astro` `Hono` `PostgreSQL` `Redis` `Docker` `Drizzle` `Dodo Payments` `Discord` `Twitch` `Playwright` `Vitest`

---

<div align="center">

Built by [slauko](https://github.com/slauko)

</div>
