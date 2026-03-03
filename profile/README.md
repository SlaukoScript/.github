<div align="center">

<img src="https://raw.githubusercontent.com/SlaukoScript/.github/main/assets/logo.png" alt="SlaukoScript" width="600" />

<br />
<br />

**Cross-platform community operations for Discord and Twitch**

One dashboard. Five services. Shared engine.

[![Website](https://img.shields.io/badge/Website-slaukoscript.com-F97316?style=for-the-badge&logo=googlechrome&logoColor=white)](https://slaukoscript.com)
[![Discord](https://img.shields.io/badge/Discord-Join%20Us-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/nVGAfRg8Md)
[![Feedback](https://img.shields.io/badge/Feedback-Bug%20Reports%20%26%20Ideas-22C55E?style=for-the-badge&logo=github&logoColor=white)](https://github.com/SlaukoScript/feedback/issues)

---

### What SlaukoScript is

SlaukoScript is a modular platform for community safety and operations across **Discord** and **Twitch**.

It combines a Nuxt dashboard, Fastify API, queue-driven worker, and platform bots into one consistent system.

### Current architecture

**Monorepo runtime:** Turbo + pnpm workspaces on Node.js 22+ and TypeScript 5.9  
**Apps:** `web`, `api`, `worker`, `discord`, `twitch`  
**Shared packages:** `engine`, `contracts`, `db`, `redis`, `config`, `logger`, `bot-common`  
**Core infra:** PostgreSQL 17, Redis 7, BullMQ, Docker, GHCR-based deployment  
**Quality gates:** CI runs lint, typecheck, tests, build, and boundary validation

### Core Features

<table>
<tr>
<td width="50%" valign="top">

**Moderation**

- Trust-aware AutoMod with smart filtering
- Strike escalation with configurable thresholds
- Mod queue for content review
- Ban appeal system with SLA tracking
- Cross-platform ban sync

</td>
<td width="50%" valign="top">

**Community**

- XP & reputation system with leaderboards
- Role rewards & auto-roles
- Custom commands with permission levels
- Scheduled & timed messages

</td>
</tr>
<tr>
<td width="50%" valign="top">

**Safety**

- Raid detection with automatic response tiers
- Real-time moderation log & live feed
- Cross-platform account linking
- Configurable trust scores

</td>
<td width="50%" valign="top">

**Automation & Integration**

- Rule-based automation engine
- REST API with rate limiting & webhooks
- Queue-backed background processing
- Stripe-powered subscription billing

</td>
</tr>
</table>

### Platform Status

| Surface           |         Status          | Notes                                                                 |
| :---------------- | :---------------------: | :-------------------------------------------------------------------- |
| **Discord Bot**   | :white_check_mark: Live | Moderation, automation, reputation, and command workflows             |
| **Twitch Bot**    | :white_check_mark: Live | EventSub-driven moderation and chat operations                        |
| **Web Dashboard** | :white_check_mark: Live | Unified operations UI at [slaukoscript.com](https://slaukoscript.com) |
| **API + Worker**  | :white_check_mark: Live | Fastify endpoints + BullMQ processing for async workloads             |

### Tech Stack

`Nuxt 4` `Vue 3` `TypeScript` `Fastify` `Drizzle ORM` `PostgreSQL` `Redis` `BullMQ` `Discord.js` `Twurple` `Stripe` `Docker` `GitHub Actions`

---

_Built by [slauko](https://github.com/slauko)_

</div>
