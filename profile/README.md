<div align="center">

<img src="https://raw.githubusercontent.com/SlaukoScript/.github/main/assets/logo.png" alt="SlaukoScript" width="600" />

<br />
<br />

**A modular product suite built on Nuxt 4**

Three apps. One shared layer. Ship fast.

[![Website](https://img.shields.io/badge/Website-slaukoscript.com-F97316?style=for-the-badge&logo=googlechrome&logoColor=white)](https://slaukoscript.com)
[![Discord](https://img.shields.io/badge/Discord-Join%20Us-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/nVGAfRg8Md)
[![Feedback](https://img.shields.io/badge/Feedback-Bug%20Reports%20%26%20Ideas-22C55E?style=for-the-badge&logo=github&logoColor=white)](https://github.com/SlaukoScript/feedback/issues)

---

### What SlaukoScript is

SlaukoScript is a product suite powering community tools and personal productivity apps — all built from a single Nuxt 4 monorepo with a shared UI layer.

### Products

<table>
<tr>
<td width="33%" valign="top">

**🌐 SlaukoScript**
<br />
[slaukoscript.com](https://slaukoscript.com)

Main landing page and product hub. Entry point for the entire platform.

</td>
<td width="33%" valign="top">

**🛡️ Moderation**
<br />
[mod.slaukoscript.com](https://mod.slaukoscript.com)

Cross-platform moderation for Discord and Twitch. Dashboard with real-time feeds, analytics, AutoMod, strikes, ban appeals, and automation.

</td>
<td width="33%" valign="top">

**💪 GymTrack**
<br />
[gym.slaukoscript.com](https://gym.slaukoscript.com)

Personal gym tracking PWA. Log workouts offline, track progress with charts, and sync when connected.

</td>
</tr>
</table>

### Architecture

**Monorepo runtime:** Turbo + pnpm workspaces on Node.js 22+ and TypeScript 5.9

**Apps:**
| App | Domain | Description |
|-----|--------|-------------|
| `web` | slaukoscript.com | Product suite landing page |
| `moderation` | mod.slaukoscript.com | Moderation dashboard & bot management |
| `gymtrack` | gym.slaukoscript.com | Gym tracking PWA |

**Shared packages:**
| Package | Purpose |
|---------|---------|
| `ui` | Nuxt layer — all generic components, composables, layouts, modules, and styling |
| `core` | Shared types, validation schemas, errors, and utilities |
| `server` | Auth, middleware, Redis, logger, and API client |
| `tooling` | Test utilities and build configuration |

**Infrastructure:** PostgreSQL, Redis, Docker, VPS with Nginx Proxy Manager

### Key Design Decisions

- **`packages/ui` is the single Nuxt layer** — every generic component, composable, layout, plugin, and module lives here. Apps are thin domain-specific consumers.
- **Apps share identical wiring** — same `app.vue` structure, same layout approach, same module set. Style changes are atomic across the entire platform.
- **No re-exports, no wrappers** — apps import directly from the shared layer with zero boilerplate.
- **PWA + offline-first** — GymTrack works fully offline via service workers and IndexedDB.

### Tech Stack

`Nuxt 4` `Vue 3` `TypeScript 5.9` `Turbo` `pnpm` `Nuxt UI` `Tailwind CSS` `Pinia` `ECharts` `i18n` `Sentry` `PWA` `PostgreSQL` `Redis` `Docker`

---

_Built by [slauko](https://github.com/slauko)_

</div>
