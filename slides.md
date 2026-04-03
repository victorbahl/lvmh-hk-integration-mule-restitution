---
theme: default
title: LVMH Tech Hackathon — Integration / MuleSoft
transition: fade
fonts:
  sans: DM Sans
  serif: Playfair Display
  mono: JetBrains Mono
layout: cover
background: /bg-cover.svg
class: text-white
---

<span class="section-tag">LVMH Tech Hackathon</span>
<span style="color: #B8B2AA; font-size: 0.55em; font-weight: 300; letter-spacing: 0.15em; display: block; margin-top: -20px;"><span style="font-weight: 1000;">Theme</span>: Integration / MuleSoft</span>

# Agent-Ready Order Management with MCPs

<p style="color: #B8B2AA; font-weight: 300; max-width: 500px; line-height: 1.7; margin-bottom: 46px;">
Your mission: make Order Management <strong style="color: #C4A265;">agent-ready</strong> — exposing APIs and data as MCPs that an AI agent can orchestrate in natural language.
</p>

<div style="display: flex; gap: 32px; font-size: 0.72em; color: #6B6560;">
  <div><span style="color: #B8B2AA; font-weight: 500;">Format</span><br>4-hour hackathon</div>
  <div><span style="color: #B8B2AA; font-weight: 500;">Tools</span><br>Anypoint Platform · MuleSoft Vibes · Claude Code</div>
  <div><span style="color: #B8B2AA; font-weight: 500;">Outcome</span><br>Live demo via Claude Desktop</div>
</div>

<div class="absolute top-8 right-10 flex items-center gap-4">
  <img src="/logo-lvmh.svg" style="height: 14px; opacity: 0.6;" />
  <img src="/logo-mulesoft.svg" style="height: 30px; opacity: 0.5; filter: brightness(0) invert(1);" />
</div>

<style>
h1 { color: #FAF8F5 !important; font-size: 2.4em !important; line-height: 1.2 !important; max-width: 520px; }
.section-tag { color: #C4A265; font-size: 0.7em; font-weight: 600; letter-spacing: 0.3em; text-transform: uppercase; margin-bottom: 16px; display: block; }
</style>

---

# The Challenge

## Two APIs. One Database. Agent-Ready via MCPs.

You will be provided with backend systems representing a simplified e-commerce backend typical of LVMH Maisons. Your job is to make them **agent-ready** by exposing them as MCPs that an AI agent can query in natural language.

You are split into two teams. Use `team-1` or `team-2` as a prefix in all your naming (bridges, apps, etc.).

| System | Type | What it exposes |
|---|---|---|
| **🛒 Order API** | 🌐 REST API | Orders placed by customers — order ID, customer info, items, timestamps |
| **📦 Fulfillment API** | 🌐 REST API | Shipment and delivery status — tracking number, carrier, estimated delivery |
| **🗄️ Product Catalog** | 🛢 DB | Product details — name, description, category, price, images |

---

# Prerequisites

| Requirement | Details |
|---|---|
| **Anypoint Org access** | Credentials will be provided — make sure you can log in |
| **VS Code** | Installed and up to date |
| **Anypoint Code Builder Extension Pack** | Installed in VS Code |
| **Claude account** | Required for Claude Code |
| **Claude Code Extension** | Installed in VS Code |
| **Claude Desktop** (or similar MCP client) | To test and demo your deployed MCPs |

---

# Suggested Build Plan

<v-clicks>

| | Step | What | Tool suggested |
|---|---|---|---|
| 🌉 | **1** | Create an MCP Bridge on top of the REST APIs | MuleSoft MCP Bridge |
| 🛠️ | **2** | Vibe-code a MuleSoft MCP Server on top of the Database | Claude Code |
| 🚀 | **3** | Deploy to Anypoint Platform | MuleSoft Vibes |
| 🧪 | **4** | Test — the agent queries all three systems in one interaction | Claude Desktop |
| 🔒 | **Bonus A** | Apply data masking policies on the Order API | Anypoint Platform + MuleSoft Vibes |
| 📏 | **Bonus B** | Add the LVMH Best Practices MCP and refine your code to follow standards | MuleSoft Vibes / Claude Code |

</v-clicks>

---

# Architecture — The Backend Systems

<span class="section-tag">Starting Point</span>

```mermaid {theme: 'base', themeVariables: {primaryColor: '#F5F0EB', primaryTextColor: '#1A1A1A', lineColor: '#B8B2AA', primaryBorderColor: '#B8B2AA'}, scale: 0.85}
graph LR
  OA["🛒&nbsp;Order API"] ~~~ PH1[ ] ~~~ BR[ ]
  FA["📦&nbsp;Fulfillment API"] ~~~ PH2[ ] ~~~ BR
  DB[("🗄️&nbsp;Products DB")] ~~~ PH3[ ] ~~~ MS[ ]
  BR ~~~ AG[ ]
  MS ~~~ AG

  style OA fill:#F5F0EB,color:#1A1A1A,stroke:#B8B2AA,stroke-width:2px
  style FA fill:#F5F0EB,color:#1A1A1A,stroke:#B8B2AA,stroke-width:2px
  style DB fill:#F5F0EB,color:#1A1A1A,stroke:#B8B2AA,stroke-width:2px
  style PH1 fill:none,stroke:none,color:transparent
  style PH2 fill:none,stroke:none,color:transparent
  style PH3 fill:none,stroke:none,color:transparent
  style BR fill:none,stroke:none,color:transparent
  style MS fill:none,stroke:none,color:transparent
  style AG fill:none,stroke:none,color:transparent
```

---
transition: none
---

# Architecture — Step 1: MCP Bridge

<span class="section-tag">Connect the APIs</span>

```mermaid {theme: 'base', themeVariables: {primaryColor: '#F5F0EB', primaryTextColor: '#1A1A1A', lineColor: '#B8B2AA'}, scale: 0.85}
graph LR
  OA["🛒&nbsp;Order API"] ~~~ PH1[ ] ~~~ BR["🌉&nbsp;MCP Bridge"]
  OA --> BR
  FA["📦&nbsp;Fulfillment API"] ~~~ PH2[ ] ~~~ BR
  FA --> BR
  DB[("🗄️&nbsp;Products DB")] ~~~ PH3[ ] ~~~ MS[ ]
  BR ~~~ AG[ ]
  MS ~~~ AG

  style OA fill:#F5F0EB,color:#1A1A1A,stroke:#B8B2AA,stroke-width:2px
  style FA fill:#F5F0EB,color:#1A1A1A,stroke:#B8B2AA,stroke-width:2px
  style DB fill:#F5F0EB,color:#1A1A1A,stroke:#B8B2AA,stroke-width:2px
  style BR fill:#00A1DF,color:#fff,stroke:none
  style PH1 fill:none,stroke:none,color:transparent
  style PH2 fill:none,stroke:none,color:transparent
  style PH3 fill:none,stroke:none,color:transparent
  style MS fill:none,stroke:none,color:transparent
  style AG fill:none,stroke:none,color:transparent
```

---

# Architecture — Step 2: MCP Server

<span class="section-tag">Connect the Database</span>

```mermaid {theme: 'base', themeVariables: {primaryColor: '#F5F0EB', primaryTextColor: '#1A1A1A', lineColor: '#B8B2AA'}, scale: 0.85}
graph LR
  OA["🛒&nbsp;Order API"] ~~~ PH1[ ] ~~~ BR["🌉&nbsp;MCP Bridge"]
  OA --> BR
  FA["📦&nbsp;Fulfillment API"] ~~~ PH2[ ] ~~~ BR
  FA --> BR
  DB[("🗄️&nbsp;Products DB")] ~~~ PH3[ ] ~~~ MS["🛠️&nbsp;MCP Server"]
  DB --> MS
  BR ~~~ AG[ ]
  MS ~~~ AG

  style OA fill:#F5F0EB,color:#1A1A1A,stroke:#B8B2AA,stroke-width:2px
  style FA fill:#F5F0EB,color:#1A1A1A,stroke:#B8B2AA,stroke-width:2px
  style DB fill:#F5F0EB,color:#1A1A1A,stroke:#B8B2AA,stroke-width:2px
  style BR fill:#00A1DF,color:#fff,stroke:none
  style MS fill:#D97757,color:#fff,stroke:none
  style PH1 fill:none,stroke:none,color:transparent
  style PH2 fill:none,stroke:none,color:transparent
  style PH3 fill:none,stroke:none,color:transparent
  style AG fill:none,stroke:none,color:transparent
```

---

# Architecture — Steps 3 & 4: Deploy & Test

<span class="section-tag">The Agent orchestrates everything</span>

```mermaid {theme: 'base', themeVariables: {primaryColor: '#F5F0EB', primaryTextColor: '#1A1A1A', lineColor: '#B8B2AA'}, scale: 0.85}
graph LR
  OA["🛒&nbsp;Order API"] ~~~ PH1[ ] ~~~ BR["🌉&nbsp;MCP Bridge"]
  OA --> BR
  FA["📦&nbsp;Fulfillment API"] ~~~ PH2[ ] ~~~ BR
  FA --> BR
  DB[("🗄️&nbsp;Products DB")] ~~~ PH3[ ] ~~~ MS["🛠️&nbsp;MCP Server"]
  DB --> MS
  BR --> AG["🤖&nbsp;AI Agent<br/><i style='font-size:0.8em'>(e.g. Claude Desktop)</i>"]
  MS --> AG

  style OA fill:#F5F0EB,color:#1A1A1A,stroke:#B8B2AA,stroke-width:2px
  style FA fill:#F5F0EB,color:#1A1A1A,stroke:#B8B2AA,stroke-width:2px
  style DB fill:#F5F0EB,color:#1A1A1A,stroke:#B8B2AA,stroke-width:2px
  style BR fill:#00A1DF,color:#fff,stroke:none
  style MS fill:#D97757,color:#fff,stroke:none
  style AG fill:#0A0A0A,color:#FAF8F5,stroke:#C4A265,stroke-width:2px
  style PH1 fill:none,stroke:none,color:transparent
  style PH2 fill:none,stroke:none,color:transparent
  style PH3 fill:none,stroke:none,color:transparent
```

---

# Architecture — Bonus A: API Proxy + Policy

<span class="section-tag">Data masking</span>

```mermaid {theme: 'base', themeVariables: {primaryColor: '#F5F0EB', primaryTextColor: '#1A1A1A', lineColor: '#B8B2AA'}, scale: 0.85}
graph LR
  OA["🛒&nbsp;Order API"] -.-> PX["🔒&nbsp;API Proxy<br/><i style='font-size:0.8em'>(with Policy)</i>"]
  PX --> BR["🌉&nbsp;MCP Bridge"]
  FA["📦&nbsp;Fulfillment API"] ~~~ PH2[ ] ~~~ BR
  FA --> BR
  DB[("🗄️&nbsp;Products DB")] ~~~ PH3[ ] ~~~ MS["🛠️&nbsp;MCP Server"]
  DB --> MS
  BR --> AG["🤖&nbsp;AI Agent<br/><i style='font-size:0.8em'>(e.g. Claude Desktop)</i>"]
  MS --> AG

  style OA fill:#F5F0EB,color:#1A1A1A,stroke:#B8B2AA,stroke-width:2px
  style FA fill:#F5F0EB,color:#1A1A1A,stroke:#B8B2AA,stroke-width:2px
  style DB fill:#F5F0EB,color:#1A1A1A,stroke:#B8B2AA,stroke-width:2px
  style BR fill:#00A1DF,color:#fff,stroke:none
  style MS fill:#D97757,color:#fff,stroke:none
  style AG fill:#0A0A0A,color:#FAF8F5,stroke:#C4A265,stroke-width:2px
  style PX fill:#C4A265,color:#fff,stroke:none
  style PH2 fill:none,stroke:none,color:transparent
  style PH3 fill:none,stroke:none,color:transparent
```

---
layout: two-cols-header
---

# 🌉 Step 1 — Create the MCP Bridge
**Tool**: API Manager > MCP Bridge

**In API Manager**, create an MCP Bridge on top of the **Order API** and **Fulfillment API**.

::left::

Browse each API spec and **select which endpoints to expose as tools** — not every endpoint needs to be agent-callable. Pick the ones that make sense for the use case.

The bridge translates your selection into MCP-compatible tools — no code required.

Deploy it on the **Ingress Flex Gateway** provided in your environment.

📖 [MCP Bridge docs](https://docs.mulesoft.com/api-manager/latest/create-instance-task-mcp-bridge)

::right::

![Selecting endpoints in the MCP Bridge UI](/screenshot-mcp-bridge.png)

---
layout: two-cols-header
---

# 🛠️ Step 2 — Vibe-Code the MCP Server
**Tool**: Claude Code / ACB in VS Code

Using **Claude Code** with the ACB extension, vibe-code a Mule application that connects to the **Products Database** and exposes it as an MCP server.

Use these details to connect to the **Products Database**:

::left::

### 🔐 Connection

```yaml
host: cloud-services.demos.mulesoft.com
port: 31717
username: root
password: Autom-tionR0cks.
database: lvmh
```

::right::

### 🛢️ Table `product_catalog`

```sql
id            INT AUTO_INCREMENT PRIMARY KEY
product_id    VARCHAR(50)   -- PRD-XXXXXXXX
sku           VARCHAR(50)
name          VARCHAR(255)
brand         VARCHAR(100)
category      VARCHAR(100)
subcategory   VARCHAR(100)
price         DECIMAL(10,2)
currency      VARCHAR(3)    -- default EUR
stock_status  ENUM('IN_STOCK','OUT_OF_STOCK','LOW_STOCK')
created_at    TIMESTAMP
```


---
layout: two-cols-header
---

# 🛠️ Step 2 — Vibe-Code the MCP Server
::left::

Try different prompt strategies — start broad, then iterate and refine. Experiment with what works best.

> Hint: Claude is great at general Mule code, but newer components (like MCP) may not be in its training data. You could ask it to **search the web for examples** before generating unfamiliar syntax.

::right::

![Claude Code in VS Code](/screenshot-claude-code.png)

---

# 🚀 Step 3 — Deploy to Anypoint Platform

Deploy your MCP server to the provided Anypoint environment using **MuleSoft Vibes**.

Ask Vibes to deploy your application — it handles packaging, environment selection, and deployment through natural language commands. Both MCPs must be live and callable.

---

# 🧪 Step 4 — Test with an AI Agent

Connect both MCPs to **Claude Desktop** (or any MCP-compatible agent) and test a live conversation that queries **all three systems** in a single interaction.

<v-click>

> Try: *"Show me the 3 latest orders for customer tao.c@gmail.com, with shipment info, and the full product details for every item ordered."*

</v-click>

---

# 🔒 Bonus A — Data Masking

<v-clicks>

1. Create an **API proxy** of the Order API in API Manager
2. Apply a **data masking policy** on the proxy using MuleSoft Vibes
3. Update your **MCP Bridge routing** to point to the proxy instead of the original API
4. Test that sensitive fields are masked in the agent's response

</v-clicks>

---

# 📏 Bonus B — LVMH Best Practices

On Anypoint Exchange, you will find an MCP server connected to Confluence that exposes LVMH's integration standards and best practices.

**Add this MCP to your environment and re-generate or refine your code to follow LVMH standards. Compare the before and after.**

---
layout: image-right
image: /pexels-a-darmel-7710087.jpg
zoom: 0.75
---

# 🎤 Show & Tell

Prepare a short presentation with a **live demo** of your agent conversation end to end.

**Tell us:**

- **Live demo** — show your agent querying all three systems in one conversation, your IDE / flows
- **The journey** — your vibe-coding process, prompts that worked (and didn't), how you iterated
- **What surprised you** — moments that changed how you think about prompting, building integrations...
- **What's next** — if you had another 4 hours, what would you add?

<h2 style="color: #C4A265; margin-top: 24px; margin-bottom: 24px;">Be fun. Be creative. 🎉</h2>

> **Need a slide deck?** [Fork this one](https://github.com/victorbahl/lvmh-hk-integration-mule-brief) — built with [Slidev](https://sli.dev) and mainly vibe-coded with Claude Code 😊



