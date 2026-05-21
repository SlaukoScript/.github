<div align="center">

<img src="https://raw.githubusercontent.com/SlaukoScript/.github/main/assets/logo.png" alt="SlaukoScript" width="600" />

<br />
<br />

**A modular product suite — multi-repo, shared TypeScript packages, central deploy**

[![Website](https://img.shields.io/badge/Website-slaukoscript.com-F97316?style=for-the-badge&logo=googlechrome&logoColor=white)](https://slaukoscript.com)
[![Discord](https://img.shields.io/badge/Discord-Join%20Us-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/nVGAfRg8Md)
[![Feedback](https://img.shields.io/badge/Feedback-Bug%20Reports%20%26%20Ideas-22C55E?style=for-the-badge&logo=github&logoColor=white)](https://github.com/SlaukoScript/feedback/issues)

---

</div>

## What SlaukoScript is

A small portfolio of self-hosted product apps (gym tracker, moderation suite, landing page, internal AI gateway) running on a single VPS. Each app is its own repository with its own CI/CD; they share a curated set of TypeScript packages and a central deploy compose file.

## Products

<div align="center">
<table>
<tr>
<td width="33%" valign="top" align="center">

**🌐 SlaukoScript**
<br />
[slaukoscript.com](https://slaukoscript.com)

Main landing page and product hub.

[Repo →](https://github.com/SlaukoScript/web)

</td>
<td width="33%" valign="top" align="center">

**🛡️ Moderation**
<br />
[mod.slaukoscript.com](https://mod.slaukoscript.com)

Cross-platform moderation for Discord and Twitch — dashboard, AutoMod, strikes, appeals.

[Repo →](https://github.com/SlaukoScript/moderation)

</td>
<td width="33%" valign="top" align="center">

**💪 GymTrack**
<br />
[gym.slaukoscript.com](https://gym.slaukoscript.com)

Personal gym tracking PWA — offline-first, charts, progressive overload.

[Repo →](https://github.com/SlaukoScript/gymtrack)

</td>
</tr>
</table>
</div>

## Architecture

After [Axis 2 decomposition](https://github.com/SlaukoScript/docs/blob/main/docs/adr/0002-monorepo-decomposition.md) (2026-05), the org runs as **10 focused repos** instead of one mega-monorepo:

```
        ┌─────────────────────┐
        │     packages        │  ← shared TypeScript libraries
        │  core platform      │     publishes 0.0.0-<sha>-snapshot
        │  server tooling ui  │     to GitHub Packages on every merge
        └──────────┬──────────┘
                   │ consumers pin to ^snapshots
       ┌───────────┼───────────────────────────────┐
       │           │                               │
   ┌───┴───┐   ┌───┴────┐  ┌──────────┐  ┌─────────┴────────┐
   │  ai   │   │gymtrack│  │moderation│  │       web        │
   └───┬───┘   └───┬────┘  └────┬─────┘  └─────────┬────────┘
       │           │            │                  │
       └───────────┴─── ghcr.io/slaukoscript/<app> ┘
                              │
                       ┌──────┴──────┐
                       │    infra    │  ← central docker-compose pulls images
                       └─────────────┘
```

A separate [`daemon`](https://github.com/SlaukoScript/daemon) sweeps every repo on a cadence to open improvement PRs. [`docs`](https://github.com/SlaukoScript/docs) holds cross-repo ADRs, ops runbooks, and the daemon's shared memory.

## Repositories

| Repo | Role | Stack |
|---|---|---|
| [`packages`](https://github.com/SlaukoScript/packages) | Shared TS libraries (`core`, `platform`, `server`, `tooling`, `ui`). Publishes snapshots to GitHub Packages. | pnpm + Turbo |
| [`ai`](https://github.com/SlaukoScript/ai) | AI-scope monorepo — 3 packages (`ai-{agent,client,providers}`) + 3 apps (`chat`, `cli`, `gateway`) | pnpm + Turbo, Nuxt 4, Nitro |
| [`gymtrack`](https://github.com/SlaukoScript/gymtrack) | Gym tracking PWA — offline-first, IndexedDB + service workers | Nuxt 4, Nitro, Postgres, sharp |
| [`moderation`](https://github.com/SlaukoScript/moderation) | Discord/Twitch moderation dashboard + bots | Nuxt 4, Nitro, Postgres, Redis |
| [`web`](https://github.com/SlaukoScript/web) | Landing page | Nuxt 4 |
| [`infra`](https://github.com/SlaukoScript/infra) | Central `docker-compose.yml` pulling GHCR images + ops scripts | Docker, NPM, Postgres, Redis |
| [`daemon`](https://github.com/SlaukoScript/daemon) | Autonomous improvement daemon — sweeps all repos | Node.js + Claude/Slauko CLI |
| [`docs`](https://github.com/SlaukoScript/docs) | Cross-repo ADRs, ops runbooks, decomposition tooling, daemon memory | Markdown |
| [`feedback`](https://github.com/SlaukoScript/feedback) | Public bug reports + feature requests | Issues only |
| [`.github`](https://github.com/SlaukoScript/.github) | Org profile + shared workflows | This file |

## Deploy flow

1. Push to a split repo's `main` → its CI builds and pushes `ghcr.io/slaukoscript/<app>:<sha>` + `:latest`
2. Operator runs `infra/compose-up.sh` on the VPS → `docker compose pull && docker compose up -d`
3. Nginx Proxy Manager terminates TLS and routes the subdomain to the container

For shared-package changes: push to `packages/main` → snapshot publish workflow ships `0.0.0-<sha7>-snapshot` to GHCR npm. Each consumer repo bumps its pin in a follow-up PR (manual today; Renovate later).

## Tech stack

`Nuxt 4` `Vue 3` `TypeScript 5.9` `pnpm` `Turbo` `Nuxt UI` `Tailwind CSS 4` `Pinia` `ECharts` `i18n` `Sentry` `PWA` `PostgreSQL 17` `Redis 7` `Docker` `Nginx Proxy Manager` `Self-hosted GitHub Actions` `GitHub Packages` `GHCR`

---

<div align="center">

_Built by [slauko](https://github.com/slauko) — autonomously improved by [`daemon`](https://github.com/SlaukoScript/daemon)_

</div>
