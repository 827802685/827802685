<div align="center">

<img src="assets/banner.svg" width="100%" alt="zjkl" />

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=19&pause=1000&color=F6821F&center=true&vCenter=true&width=620&lines=Cloudflare+Workers;AI+Agent+Orchestration;Self-hosted+Services" alt="typing" />

<br/>

**高中生 · 自学 · 主力写两类东西：跑在 Cloudflare 边缘的服务，和调度 AI 干活的本地编排系统**

[![Blog](https://img.shields.io/badge/Blog-blog.zjkl.qzz.io-F38020?style=flat-square&logo=cloudflare&logoColor=white)](https://blog.zjkl.qzz.io)
[![GitHub](https://img.shields.io/badge/GitHub-827802685-181717?style=flat-square&logo=github)](https://github.com/827802685)
[![Mail](https://img.shields.io/badge/Mail-zjkl%40zjkl0426.dpdns.org-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:zjkl@zjkl0426.dpdns.org)

<img src="assets/divider.svg" width="100%" height="40" alt="" />

</div>

## 🔨 在做

<table>
  <tr>
    <td width="33%" align="center">
      <b>🧠 牛马工作室</b><br/>
      <sub>一个进程里的 AI 编排层 + Job 状态层</sub>
    </td>
    <td width="33%" align="center">
      <b>☁️ clist</b><br/>
      <sub>网盘 / 图床 / 存储聚合，前后端分离</sub>
    </td>
    <td width="33%" align="center">
      <b>⚡ mini-flow</b><br/>
      <sub>n8n 工作流引擎搬到 Cloudflare Workers</sub>
    </td>
  </tr>
</table>

<br/>

## 🚀 主力项目

> 持续投入、有自己架构的那几个。

### [job](https://github.com/827802685/job) — 牛马工作室 &nbsp;<img src="https://img.shields.io/badge/全部自研-22C55E?style=flat-square" alt="self"/>

一个进程、一个端口、一套网页，把两件事合在一起：

- **工作室**：项目组 × 员工两层模型。项目组 = 一个模型后端（Claude Code / Codex / OpenCode / Qoder / Trae / DeepSeek CLI / 任意 OpenAI 兼容 API），员工 = 某个技能（架构 / 前端 / 后端 / 测试 / 审查 / 排障 / 文案）在某个项目组里上班。会拆任务、派活、盯进度、验收、返工、存档。
- **Job 状态层**：意图路由 → 权限裁定（L1–L6，**Fail Closed**）→ 租约 → 十二道执行门禁 → 调度 → 审计 → 工单。挂在 `/job/*`，控制台是首页右上角「管家」面板，13 个页签。

带彩排模式：`npm run rehearsal` —— 假员工演一遍，不花钱、不改文件。

### [mini-flow](https://github.com/827802685/mini-flow) — n8n 的边缘版 &nbsp;<img src="https://img.shields.io/badge/后端自研-22C55E?style=flat-square" alt="self"/>

把 n8n 的可视化编排 + 节点执行原生化搬到 Cloudflare Workers，内置防丢失与中断恢复：**检查点、幂等重试、死信队列、防重叠锁**。

- 后端在 Workers 上**自己复刻** n8n 的 REST 契约 + Push(SSE) 协议：Hono 组装，D1 存状态、KV 存凭据、Durable Object 转 SSE、Workflows 断点续跑
- 前端复用 n8n 官方 editor-ui（不改源码）
- 决策写在 [`DECISIONS.md`](https://github.com/827802685/mini-flow/blob/main/DECISIONS.md)，带 tests 与 migrations

### [cloud-api](https://github.com/827802685/cloud-api) — AI 网关 &nbsp;<img src="https://img.shields.io/badge/基于开源网关改造-3B82F6?style=flat-square" alt="based"/>

可自托管的 AI 网关：多供应商（OpenAI / Anthropic / Gemini）+ 多协议（Chat / Images / Audio）+ 四种路由策略（缓存亲和 / 加权随机 / 优先级主备 / 加权轮转）+ 三账本计费。Workers + D1 零成本部署，也可 Docker 自托管。

### [Rin](https://github.com/827802685/Rin) — 个人博客 &nbsp;<img src="https://img.shields.io/badge/fork_自_openRin/Rin-3B82F6?style=flat-square" alt="fork"/>

Fork 自 [openRin/Rin](https://github.com/openRin/Rin) 的边缘博客，之后 40+ 次提交按自己的需求改。线上跑在 **[blog.zjkl.qzz.io](https://blog.zjkl.qzz.io)**（Workers + D1 + R2）。

### [Hot-News](https://github.com/827802685/Hot-News) — 新闻聚合 &nbsp;<img src="https://img.shields.io/badge/整合_newsnow-3B82F6?style=flat-square" alt="based"/>

一个 Worker 同时承载 newsnow 卡片新闻墙 + 自建后台（订阅抓取 / 多源 / AI 翻译 / 企业微信推送 / 四时段定时）。线上 **[news.zjkl.qzz.io](https://news.zjkl.qzz.io)**，15 分钟一轮采集。

### ☁️ clist — 网盘聚合 <img src="https://img.shields.io/badge/私有仓库-F6821F?style=flat-square" alt="private"/>

前后端分离的云盘 / 图床 / 存储聚合系统，跑在 **[clist.zjkl.dpdns.org](https://clist.zjkl.dpdns.org)**。仓库私有，代码不公开。

---

## 🧩 小工具

| 项目 | 说明 |
| :--- | :--- |
| 🔑 **[Password-UUID-Generator](https://github.com/827802685/Password-UUID-Generator)** | 密码 & UUID 生成器，纯前端，线上 [uuid.zjkl0426.dpdns.org](https://uuid.zjkl0426.dpdns.org) |
| 📡 **[ModelRadar](https://github.com/827802685/ModelRadar)** | 免费 AI 模型雷达：收录可用模型、额度与限速信息 |
| 📮 **[personal-ai-mail](https://github.com/827802685/personal-ai-mail)** | 单用户 AI 邮件系统：AI 分类摘要、验证码提取、FTS5 中文全文搜索、11 个 MCP 工具 |
| 🔀 **[freellmapi-cf](https://github.com/827802685/freellmapi-cf)** | 统一大模型 API 路由，聚合 19+ 家提供商，一个 endpoint 全搞定 |
| 🐒 **[tampermonkey](https://github.com/827802685/tampermonkey)** | 个人油猴脚本集合 |

---

## 🔧 基于上游部署

> 这些是拿来自己跑、顺手改了点儿的，**不算作品**，列出来只是说明我在用什么。

| 项目 | 上游 |
| :--- | :--- |
| 📦 [cloud-drive](https://github.com/827802685/cloud-drive) | CloudPaste（云盘聚合，我只补了审计日志） |
| 🎭 [Live2D](https://github.com/827802685/Live2D) | live2d-widget（网页看板娘） |
| 📈 [UptimeFlare](https://github.com/827802685/UptimeFlare) | uptime-flare（服务状态页） |
| 🖼 [tg-img](https://github.com/827802685/tg-img) | x-dr/telegraph-Image（图床） |
| 📋 [web-clipboard](https://github.com/827802685/web-clipboard) | yun8862779/web-clipboard |

<sub>其余为纯 fork 自部署，如 newsnow、cloud-mail、Sink、LibreTV、MoonTV、SPlayer、TrendRadar、galaxy 等，不再逐一列出。</sub>

<br/>

## 🌐 在跑的服务

<table>
  <tr>
    <td width="33%" align="center">📝<br/><a href="https://blog.zjkl.qzz.io"><b>博客</b></a><br/><sub>Rin · Workers + D1 + R2</sub></td>
    <td width="33%" align="center">🏠<br/><a href="https://zjkl.qzz.io"><b>主页</b></a><br/><sub>zjkl.qzz.io</sub></td>
    <td width="33%" align="center">🔥<br/><a href="https://news.zjkl.qzz.io"><b>新闻墙</b></a><br/><sub>Hot-News · 15 分钟一轮</sub></td>
  </tr>
  <tr>
    <td width="33%" align="center">☁️<br/><a href="https://clist.zjkl.dpdns.org"><b>云盘列表</b></a><br/><sub>clist 网盘聚合</sub></td>
    <td width="33%" align="center">🚀<br/><a href="https://gh.zjkl0330.dpdns.org"><b>GitHub 加速</b></a><br/><sub>Release 下载镜像</sub></td>
    <td width="33%" align="center">🔑<br/><a href="https://uuid.zjkl0426.dpdns.org"><b>密码生成器</b></a><br/><sub>密码 &amp; UUID</sub></td>
  </tr>
</table>

<br/>

## 🛠 技术栈

**语言**

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)

**Cloudflare 全家桶**

![Workers](https://img.shields.io/badge/Workers-F38020?style=for-the-badge&logo=cloudflare&logoColor=white)
![D1](https://img.shields.io/badge/D1-0B1020?style=for-the-badge&logo=cloudflare&logoColor=F38020)
![KV](https://img.shields.io/badge/KV-0B1020?style=for-the-badge&logo=cloudflare&logoColor=F38020)
![Durable Objects](https://img.shields.io/badge/Durable_Objects-0B1020?style=for-the-badge&logo=cloudflare&logoColor=F38020)
![Hono](https://img.shields.io/badge/Hono-E36002?style=for-the-badge&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)

**前端**

![Vue](https://img.shields.io/badge/Vue.js-4FC08D?style=for-the-badge&logo=vuedotjs&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)

**工具**

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![Pages](https://img.shields.io/badge/Pages-F38020?style=for-the-badge&logo=cloudflare&logoColor=white)
![Tampermonkey](https://img.shields.io/badge/Tampermonkey-800000?style=for-the-badge&logo=tampermonkey&logoColor=white)

<br/>

## 📊 Activity

<div align="center">

<table>
  <tr>
    <td align="center" width="50%">
      <img src="https://img.shields.io/github/followers/827802685?style=for-the-badge&label=Followers&color=F6821F&logo=github&logoColor=white" alt="followers" />
    </td>
    <td align="center" width="50%">
      <img src="https://img.shields.io/badge/dynamic/json?style=for-the-badge&label=Repos&color=3178C6&query=%24.public_repos&url=https%3A%2F%2Fapi.github.com%2Fusers%2F827802685" alt="repos" />
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <img src="https://img.shields.io/github/stars/827802685?style=for-the-badge&label=Stars&color=F7DF1E" alt="stars" />
    </td>
    <td align="center" width="50%">
      <img src="https://img.shields.io/badge/On_GitHub-since_2024--02--08-22C55E?style=for-the-badge&logo=github&logoColor=white" alt="since" />
    </td>
  </tr>
</table>

<br/>

<img src="assets/langs.svg" width="100%" alt="language breakdown" />

<br/>

<img src="https://streak-stats.demolab.com?user=827802685&hide_border=true&border_radius=10&locale=zh_Hans&theme=dark" alt="streak" />

</div>

<br/>

## 🤝 合作

- 对 **Cloudflare Workers / 边缘计算 / AI Agent 编排**相关话题感兴趣，开 issue 直接聊
- 接小的自建工具、脚本需求，先说清楚要什么
- 不接：代写、刷量、任何要我造假数据的活

<div align="center">

<img src="assets/divider.svg" width="100%" height="40" alt="" />

<sub>加入 GitHub：2024-02-08 · 坐标：中国 江西 吉安</sub>

**能跑起来的才算数。**

</div>
