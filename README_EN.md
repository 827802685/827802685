<div align="center">

<img src="assets/banner.svg" width="100%" alt="zjkl" />

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=19&pause=1000&color=F6821F&center=true&vCenter=true&width=620&lines=Cloudflare+Workers;AI+Agent+Orchestration;Self-hosted+Services" alt="typing" />

<br/>

**High-school student, self-taught. Two tracks: services running on the Cloudflare edge, and a local system that orchestrates AI coding agents.**

Every project below is reachable online. Label conventions: **Original** = I wrote the code; **Adapted** = built on an upstream project, which I name; **Deployed** = someone else's project that I run, no originality claimed; **Archived** = I no longer maintain the repo or its service.

[![Blog](https://img.shields.io/badge/Blog-blog.zjkl.qzz.io-F38020?style=flat-square&logo=cloudflare&logoColor=white)](https://blog.zjkl.qzz.io)
[![GitHub](https://img.shields.io/badge/GitHub-827802685-181717?style=flat-square&logo=github)](https://github.com/827802685)
[![Mail](https://img.shields.io/badge/Mail-zjkl%40zjkl0426.dpdns.org-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:zjkl@zjkl0426.dpdns.org)
[![中文](https://img.shields.io/badge/README-中文-8B5CF6?style=flat-square)](./README.md)

<img src="assets/divider.svg" width="100%" height="40" alt="" />

</div>

## 🚀 Featured projects

**🧠 [job](https://github.com/827802685/job) — Studio + Job state layer, merged into one process** &nbsp;`Studio subsystem adapted from Leeeger1/niuma-studio (MIT); Job state layer original`

The studio half follows the upstream orchestration model: you talk to a single coordinator, she decomposes the task into a "project group × worker" grid — a project group is one model backend (Claude Code / Codex / OpenCode / Qoder / Trae / DeepSeek CLI, or any OpenAI-compatible endpoint), a worker is one skill file — and a rehearsal mode runs the whole flow with mock agents, spending no API quota and touching no files. What I did was merge and rework it: the original two-process, two-console layout became a single process on a single port, with the `bin/niuma.js` entry point, the config format and the console page all rewritten. The original part is the Job state layer mounted on the `/job/*` routes of that same process: intent routing → tiered permission decisions (deny unless granted) → execution leases → multiple validation gates → audit records → work orders, driven from the "butler" panel on the home page.

**⚡ [mini-flow](https://github.com/827802685/mini-flow) — A lightweight workflow engine on Workers** &nbsp;`Backend original, frontend reuses n8n editor-ui`

I implemented the REST API and the Push (SSE) protocol against n8n's node model myself, so the official editor-ui works as the canvas without modification. Storage is layered: D1 holds run state, KV holds credentials, a Durable Object relays SSE, and Workflows provides resumable execution; the runtime ships with checkpoints, idempotent retries, a dead-letter queue and overlap locks. Rationale lives in [`DECISIONS.md`](https://github.com/827802685/mini-flow/blob/main/DECISIONS.md).

**☁️ [clist](https://clist.zjkl.dpdns.org) — Drive listing / image bed / object-storage aggregation** &nbsp;`Adapted, built on CloudPaste`

CloudPaste as the base, merging CloudFlare-ImgBed's image-hosting capability with Cloudflare-Clist's multi-drive aggregation, so one Worker serves all three, up long-term. Development happens in the private `clist-cf` repo; the public mirror [cloud-drive](https://github.com/827802685/cloud-drive) is the same codebase (`package.json` identical, only deployment parameters differ).

**🔀 [freellmapi-cf](https://github.com/827802685/freellmapi-cf) — Free-model router** &nbsp;`Archived`

Used to pool the free tiers of roughly 20 providers behind a single OpenAI-compatible endpoint, dispatching by availability with failover, up to v3.6.0. I no longer maintain this repo; the historical address **[api.zjkl0330.dpdns.org](https://api.zjkl0330.dpdns.org)** stays listed as an archive with no availability guarantee.

**📮 [personal-ai-mail](https://github.com/827802685/personal-ai-mail) — Single-user AI mail system** &nbsp;`Adapted, core framework from maillab/cloud-mail`

On top of cloud-mail's receiving and storage skeleton I wrote verification-code extraction, FTS5 full-text search for Chinese, and 11 MCP tools for agents to call. Live at **[mail.zjkl.qzz.io](https://mail.zjkl.qzz.io)**.

<sub>
**Also written by me**: **hot-news** (trending-news aggregation + RSS + multi-channel push Worker — the news wall below), **extraction** (watermark-free short-video and image parsing for 7 platforms), **Password-UUID-Generator**, **web-clipboard**, the **tampermonkey** script collection, **domain-alert** (the uptime config kept in this repo).<br/>
**Adapted and running** (upstream named): **Rin** (openRin/Rin), **UptimeFlare** (lyc8503/UptimeFlare), **MoonTV** (samqin123/MoonTV), **SPlayer** (kingfly0927/SPlayer), **TrendRadar** (sansan0/TrendRadar), **music** (meting-backend-js), **personal-ai-mail** (maillab/cloud-mail, see above).<br/>
**Deployed from upstream, no originality claimed**: **RSSWorker**, **tg-img**, **ra2web**, the **Live2D mascot site**, **NextChat**, **Sink**; **cloud-api** (AI gateway, Workers + D1 and Docker deployments) varies in how far I took it — its README and LICENSE are the authority on upstream and terms.
</sub>

<br/>

## 🌐 Services running now

> All self-hosted on Cloudflare. The list follows the config of my own uptime page [uptime.zjkl.dpdns.org](https://uptime.zjkl.dpdns.org), individually re-checked on 2026-10-07 for HTTP 200. Rows marked *Archived* stay listed for reference: the address may still answer, but I no longer maintain the code behind it.

| Service | URL | Notes |
| :--- | :--- | :--- |
| 🏠 **Home** | [zjkl.qzz.io](https://zjkl.qzz.io) | Personal portal |
| 📝 **Blog** | [blog.zjkl.qzz.io](https://blog.zjkl.qzz.io) | Adapted from Rin · Workers + D1 + R2 |
| 🔥 **News wall** | [news.zjkl.qzz.io](https://news.zjkl.qzz.io) | My own crawler, one pass every 15 min |
| ☁️ **Drive / image bed** | [clist.zjkl.dpdns.org](https://clist.zjkl.dpdns.org) | Three-in-one aggregate on CloudPaste |
| 📮 **Mail** | [mail.zjkl.qzz.io](https://mail.zjkl.qzz.io) | cloud-mail based: AI triage, code extraction, full-text search |
| 🔀 **Free models** (archived) | [api.zjkl0330.dpdns.org](https://api.zjkl0330.dpdns.org) | freellmapi-cf archive address, unmaintained |
| 🛰 **AI gateway** | [api.zjkl.dpdns.org](https://api.zjkl.dpdns.org) | cloud-api admin console |
| 💬 **Chat** | [chat.zjkl.dpdns.org](https://chat.zjkl.dpdns.org) | NextChat deployment |
| 📊 **Uptime / status** | [uptime](https://uptime.zjkl.dpdns.org) · [status](https://status.zjkl.dpdns.org) | Two UptimeFlare instances |
| 🔗 **Short links** | [zjkl0330.dpdns.org](https://zjkl0330.dpdns.org) | Sink deployment |

<sub>Plus RSS feeds, a model radar, video parsing, an online clipboard, password and address generators, a GitHub acceleration mirror, and personal sites such as TV and small games — all under <code>*.zjkl.qzz.io</code> · <code>*.zjkl.dpdns.org</code> · <code>*.zjkl0330.dpdns.org</code> · <code>*.zjkl0426.dpdns.org</code> · <code>*.zjkl0716.dpdns.org</code>; the uptime page is authoritative for status.</sub>

<br/>

## 🛠 Tech stack

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
<br/>
![Workers](https://img.shields.io/badge/Workers-F38020?style=flat-square&logo=cloudflare&logoColor=white)
![D1](https://img.shields.io/badge/D1-0B1020?style=flat-square&logo=cloudflare&logoColor=F38020)
![KV](https://img.shields.io/badge/KV-0B1020?style=flat-square&logo=cloudflare&logoColor=F38020)
![Durable Objects](https://img.shields.io/badge/Durable_Objects-0B1020?style=flat-square&logo=cloudflare&logoColor=F38020)
![R2](https://img.shields.io/badge/R2-0B1020?style=flat-square&logo=cloudflare&logoColor=F38020)
![Hono](https://img.shields.io/badge/Hono-E36002?style=flat-square&logoColor=white)
<br/>
![Vue](https://img.shields.io/badge/Vue.js-4FC08D?style=flat-square&logo=vuedotjs&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![Nuxt](https://img.shields.io/badge/Nuxt-00DC82?style=flat-square&logo=nuxtdotjs&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)

<br/>

## 📊 Activity

<div align="center">

![followers](https://img.shields.io/github/followers/827802685?style=flat-square&label=Followers&color=F6821F&logo=github&logoColor=white)
![repos](https://img.shields.io/badge/dynamic/json?style=flat-square&label=Repos&color=3178C6&query=%24.public_repos&url=https%3A%2F%2Fapi.github.com%2Fusers%2F827802685)
![stars](https://img.shields.io/github/stars/827802685?style=flat-square&label=Stars&color=F7DF1E)
![since](https://img.shields.io/badge/On_GitHub-since_2024--02--08-22C55E?style=flat-square&logo=github&logoColor=white)

<br/><br/>

<img src="assets/langs.svg" width="100%" alt="language breakdown" />

<br/>

<img src="https://streak-stats.demolab.com?user=827802685&hide_border=true&border_radius=10&theme=dark" alt="streak" />

</div>

<br/>

## 🤝 Contact

Open an issue if you work on **Cloudflare Workers / edge computing / AI agent orchestration** — happy to talk. I take small self-hosted tool and script requests. I don't take ghost-writing gigs, traffic inflation, or anything that asks me to fabricate data.

<div align="center">

<img src="assets/divider.svg" width="100%" height="40" alt="" />

<sub>Joined GitHub: 2024-02-08 · Based in: Ji'an, Jiangxi, China</sub>

**If it doesn't run, it doesn't count.**

</div>
