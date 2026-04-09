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
<span class="cover-subtitle"><strong>Theme</strong>: Integration / MuleSoft</span>

# Agent-Ready Order Management with MCPs

<p class="cover-description">
Your mission: make Order Management <strong>agent-ready</strong> — exposing APIs and data as MCPs that an AI agent can orchestrate in natural language.
</p>

<div class="cover-meta">
  <div><span class="cover-meta-label">Date</span><br>April 9, 2026</div>
  <div><span class="cover-meta-label">Location</span><br>Station F, Paris</div>
  <div><span class="cover-meta-label">Format</span><br>4-hour hackathon</div>
  <div><span class="cover-meta-label">Tools</span><br>Anypoint Platform · MuleSoft Vibes · Claude (Code) Maison</div>
</div>

<div class="absolute top-8 right-10 flex items-center gap-4">
  <img src="/logo-lvmh.svg" class="cover-logo-lvmh" />
  <img src="/logo-mulesoft.svg" class="cover-logo-mulesoft" />
</div>


---

# The Context
Measuring the European Marketing Campaign — Live.

The **CIO needs immediate visibility** on how our latest campaign is driving sales across our European customer base. Traditional development means long cycles and delayed insights — by the time the dashboard ships, the campaign momentum is gone.

Thanks to **AI**, we **empower the team to access the data and talk to it** — unlocking **live visibility** by conversing naturally with an agent across two APIs and a product database.

<br/>

| System | Type | Role in the campaign insight |
|---|---|---|
| **🛒 Order API** | 🌐 REST API | Surface orders tied to the campaign — customer info, items, timestamps |
| **📦 Fulfillment API** | 🌐 REST API | Map delivery data to isolate our European customer base |
| **🗄️ Product Catalog** | 🛢 DB | Identify the exact items promoted — name, category, price |


---

# Build Plan & Architecture

<div class="build-overview">

<div class="steps-col">

<div class="step-card clickable" @click="$slidev.nav.go(5)">
  <div class="step-num" style="background: var(--mulesoft-blue);">1</div>
  <div><div class="step-title"><span class="step-emoji">🌉</span> MCP Bridge</div><div class="step-desc">Bridge the REST APIs via API Manager</div></div>
</div>

<div class="step-card clickable" @click="$slidev.nav.go(6)">
  <div class="step-num" style="background: var(--mulesoft-blue);">2</div>
  <div><div class="step-title"><span class="step-emoji">🛠️</span> MCP Server</div><div class="step-desc">Vibe-code a Mule app for the Database</div></div>
</div>

<div class="step-card clickable" @click="$slidev.nav.go(8)">
  <div class="step-num" style="background: var(--deploy-green);">3</div>
  <div><div class="step-title"><span class="step-emoji">🚀</span> Deploy</div><div class="step-desc">Ship to Anypoint Platform</div></div>
</div>

<div class="step-card clickable" @click="$slidev.nav.go(9)">
  <div class="step-num" style="background: var(--gold);">4</div>
  <div><div class="step-title"><span class="step-emoji">🧪</span> Test</div><div class="step-desc">Agent queries all three systems</div></div>
</div>

<div class="step-card bonus clickable" @click="$slidev.nav.go(5)">
  <div class="step-num" style="background: var(--bonus-color);">A</div>
  <div><div class="step-title"><span class="step-emoji">🔒</span> Data Masking</div><div class="step-desc">Apply policies on the Order API</div></div>
</div>

</div>

<div class="arch-col">
  <ArchDiagram />
</div>

</div>

---

# 🤖 How AI Helped

- **Code production and deployment** — from a blank editor to a running MCP on Anypoint, with the agent handling scaffolding, connector wiring and packaging end-to-end
- **Planning** — the agent helped us break the challenge into concrete steps, weigh trade-offs and keep the team aligned on the next action
- **Auto-fixing and troubleshooting** — stack traces and config errors were diagnosed and resolved in the loop, without leaving the IDE
- **Presentation creation** — even this deck was largely vibe-coded, turning raw notes into a structured, on-brand story

---

# 💡 Key Learnings

- **It works well — but it needs iteration.** First prompts rarely land; refining intent and feeding back context is where the real value comes from
- **Costs are high at the start.** Exploration and trial-and-error burn tokens fast — discipline and good prompting habits pay off quickly

---

# 🔄 Impact on Ways of Working

- **No coding skills strictly required to make things happen** — product, data and business folks can now go from idea to working prototype by describing what they want in plain language
- **Expertise is still essential — for verification.** Someone has to read the code, validate the architecture, catch the subtle bugs and own quality. AI doesn't remove the need for senior judgment, it amplifies it
- **Everyone needs a developer mindset** — thinking in terms of inputs, outputs, edge cases and testability becomes a baseline skill, even for non-developers steering the agent

---

# 🚀 Next Steps in Your Daily Work

- **Make Claude (Code) Maison your daily driver** — not just for coding, but for writing specs, drafting architecture diagrams, reviewing PRs and documenting decisions. Treat the agent as a pair, not a tool
- **Learn to optimize costs as you learn the craft** — scope prompts tightly, reuse context, pick the right model for the task, and measure what each workflow actually costs so value stays ahead of spend