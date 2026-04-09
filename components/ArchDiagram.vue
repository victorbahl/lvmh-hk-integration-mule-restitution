<template>
  <svg viewBox="0 0 500 420" xmlns="http://www.w3.org/2000/svg" class="arch-svg">
    <defs>
      <filter id="bshadow" x="-8%" y="-8%" width="116%" height="124%">
        <feDropShadow dx="0" dy="2" stdDeviation="4" flood-opacity="0.07"/>
      </filter>
    </defs>

    <!-- Always visible: 3 backend systems at the bottom -->
    <g filter="url(#bshadow)">
      <rect x="6" y="340" width="134" height="44" rx="8" fill="var(--cream)" stroke="var(--light-gray)" stroke-width="1.5"/>
      <text x="73" y="366" text-anchor="middle" class="box-label" fill="var(--charcoal)">🛒 Order API</text>
    </g>
    <g filter="url(#bshadow)">
      <rect x="183" y="340" width="134" height="44" rx="8" fill="var(--cream)" stroke="var(--light-gray)" stroke-width="1.5"/>
      <text x="250" y="366" text-anchor="middle" class="box-label" fill="var(--charcoal)">📦 Fulfillment API</text>
    </g>
    <g filter="url(#bshadow)">
      <rect x="360" y="340" width="134" height="44" rx="0" fill="var(--cream)" stroke="var(--light-gray)" stroke-width="1.5"/>
      <text x="427" y="366" text-anchor="middle" class="box-label" fill="var(--charcoal)">🗄️ Products DB</text>
    </g>

    <!-- MCP Bridge + connections from both APIs -->
    <g class="arch-el">
      <line x1="250" y1="340" x2="188" y2="234" class="data-link" stroke="var(--mulesoft-blue)" stroke-width="1.5"/>
      <g filter="url(#bshadow)" class="arch-clickable" @click="$slidev.nav.go(5)">
        <rect x="94" y="190" width="132" height="44" rx="8" fill="var(--mulesoft-blue)"/>
        <text x="160" y="216" text-anchor="middle" class="box-label" fill="#fff">🌉 MCP Bridge</text>
      </g>
    </g>

    <!-- API Proxy (Bonus A) — Order API routes through the proxy before reaching the Bridge -->
    <g class="arch-el">
      <line x1="73" y1="340" x2="58" y2="302" class="data-link" stroke="var(--bonus-color)" stroke-width="1.2"/>
      <line x1="78" y1="268" x2="116" y2="234" class="data-link" stroke="var(--bonus-color)" stroke-width="1.2"/>
      <g filter="url(#bshadow)" class="arch-clickable" @click="$slidev.nav.go(5)">
        <rect x="13" y="268" width="100" height="34" rx="6" fill="var(--bonus-color)"/>
        <text x="63" y="289" text-anchor="middle" class="box-label" fill="#fff">🔒 Proxy</text>
      </g>
    </g>

    <!-- MCP Server + connection from DB -->
    <g class="arch-el">
      <line x1="427" y1="340" x2="395" y2="234" class="data-link" stroke="var(--mulesoft-blue)" stroke-width="1.5"/>
      <g filter="url(#bshadow)" class="arch-clickable" @click="$slidev.nav.go(6)">
        <rect class="mcp-server-box" x="329" y="190" width="132" height="44" rx="8" fill="var(--mulesoft-blue)"/>
        <text x="395" y="216" text-anchor="middle" class="box-label" fill="#fff">🛠️ MCP Server</text>
      </g>
    </g>

    <!-- Deploy check mark — MCP Server only (Bridge is auto-deployed) -->
    <g class="arch-el">
      <circle cx="451" cy="196" r="8" fill="var(--deploy-green)"/>
      <path d="M447 196 l3 3 l5 -6" fill="none" stroke="#fff" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/>
    </g>

    <!-- AI Agent + connections from Bridge & Server -->
    <g class="arch-el">
      <line x1="160" y1="190" x2="226" y2="86" class="data-link" stroke="var(--gold)" stroke-width="1.5"/>
      <line x1="395" y1="190" x2="300" y2="86" class="data-link" stroke="var(--gold)" stroke-width="1.5"/>
      <g filter="url(#bshadow)" class="arch-clickable" @click="$slidev.nav.go(9)">
        <rect x="182" y="42" width="148" height="44" rx="10" fill="#c15f3c" stroke="var(--gold)" stroke-width="2"/>
        <text x="256" y="68" text-anchor="middle" class="box-label" fill="var(--warm-white)">🤖 AI Agent</text>
      </g>
    </g>
  </svg>
</template>

<style>
/* SVG box labels — change font-size here to resize all labels at once */
.box-label {
  font-family: 'DM Sans', sans-serif;
  font-size: 14px;
  font-weight: 800;
}

/* Architecture entrance animation */
.arch-el {
  transition: all 0.6s cubic-bezier(0.22, 1, 0.36, 1) !important;
}
g.arch-el.slidev-vclick-hidden {
  opacity: 0 !important;
  transform: translateY(14px);
}

/* Data flow — marching dashes */
@keyframes dash-flow {
  from { stroke-dashoffset: 0; }
  to { stroke-dashoffset: -16; }
}
.data-link {
  fill: none;
  stroke-dasharray: 6 4;
  animation: dash-flow 0.9s linear infinite;
  stroke-linecap: round;
}

/* Best Practices enhancement glow */
@keyframes bp-glow-pulse {
  0%, 100% { opacity: 0.3; }
  50% { opacity: 0.7; }
}
.bp-glow {
  animation: bp-glow-pulse 2.5s ease-in-out infinite;
}

.arch-svg {
  width: 100%;
  max-height: 400px;
}
</style>
