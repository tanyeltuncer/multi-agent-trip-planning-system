# Multi Agent Trip planning system

This repository implements a multi-agent travel planning system powered by Large Language Models (LLMs).
The system uses specialized agents — each with a defined role — to collaboratively generate complete travel plans including:

- destination research
- itinerary generation
- activity suggestions
- budget estimation
- multi-step reasoning and validation

It demonstrates how multiple LLM-driven agents can cooperate through structured workflows, tool-calling, and memory to solve real-world planning tasks.

The AI travel agent fulfills advanced reasoning techniques, including role-based prompting, chain-of-thought reasoning, ReAct prompting, and feedback loops (further information can be found under project_starter.ipynb)

<?xml version="1.0" encoding="UTF-8"?>
<svg width="1100" height="650" viewBox="0 0 1100 650" xmlns="http://www.w3.org/2000/svg">

  <style>
    .node {
      fill: #ffffff;
      stroke: #1f2933;
      stroke-width: 1.6;
      rx: 10;
      ry: 10;
    }
    .node-header {
      fill: #e5f0ff;
      stroke: #1f2933;
      stroke-width: 1.6;
      rx: 10;
      ry: 10;
    }
    .title {
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      font-size: 16px;
      font-weight: 600;
      fill: #111827;
      text-anchor: middle;
    }
    .subtitle {
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      font-size: 12px;
      fill: #4b5563;
      text-anchor: middle;
    }
    .label {
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      font-size: 12px;
      fill: #111827;
      text-anchor: middle;
    }
    .small {
      font-size: 11px;
    }
    .arrow {
      stroke: #111827;
      stroke-width: 1.5;
      fill: none;
      marker-end: url(#arrowhead);
    }
    .lane-label {
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      font-size: 13px;
      font-weight: 600;
      fill: #374151;
    }
    .swimlane {
      fill: #f9fafb;
      stroke: #e5e7eb;
      stroke-width: 1;
    }
  </style>

  <!-- Arrow marker definition -->
  <defs>
    <marker id="arrowhead" markerWidth="8" markerHeight="8" refX="6" refY="3" orient="auto">
      <polygon points="0 0, 6 3, 0 6" fill="#111827" />
    </marker>
  </defs>

  <!-- Title -->
  <text x="550" y="40" class="title">
    Multi-Agent Trip Planning System – Flow
  </text>
  <text x="550" y="62" class="subtitle">
    Orchestrated by a State Machine with LLM-powered agents and tools
  </text>

  <!-- Swimlanes -->
  <!-- User Lane -->
  <rect x="40" y="80" width="1020" height="80" class="swimlane" />
  <text x="60" y="105" class="lane-label">User</text>

  <!-- Orchestrator Lane -->
  <rect x="40" y="160" width="1020" height="90" class="swimlane" />
  <text x="60" y="185" class="lane-label">Orchestrator / State Machine</text>

  <!-- Research Agent Lane -->
  <rect x="40" y="250" width="1020" height="100" class="swimlane" />
  <text x="60" y="275" class="lane-label">Research Agent</text>

  <!-- Itinerary Agent Lane -->
  <rect x="40" y="350" width="1020" height="100" class="swimlane" />
  <text x="60" y="375" class="lane-label">Itinerary Agent</text>

  <!-- Budget Agent Lane -->
  <rect x="40" y="450" width="1020" height="100" class="swimlane" />
  <text x="60" y="475" class="lane-label">Budget Agent</text>

  <!-- Validation / Answer Lane -->
  <rect x="40" y="550" width="1020" height="70" class="swimlane" />
  <text x="60" y="575" class="lane-label">Validation & Final Answer</text>

  <!-- Nodes -->

  <!-- User Request -->
  <rect x="150" y="100" width="220" height="40" class="node" />
  <text x="260" y="120" class="label">🧑 User Request</text>
  <text x="260" y="136" class="label small">
    "Plan a 5-day trip to Japan in April"
  </text>

  <!-- Orchestrator Node -->
  <rect x="410" y="180" width="260" height="50" class="node" />
  <text x="540" y="205" class="label">
    🎛️ Orchestrator / State Machine
  </text>
  <text x="540" y="221" class="label small">
    Creates workflow & routes between agents
  </text>

  <!-- Research Agent Node -->
  <rect x="120" y="280" width="290" height="60" class="node" />
  <text x="265" y="304" class="label">🔎 Research Agent</text>
  <text x="265" y="320" class="label small">
    Destination info, attractions, seasons, constraints
  </text>

  <!-- Research Tools Node -->
  <rect x="470" y="280" width="260" height="60" class="node" />
  <text x="600" y="304" class="label">🛠 Tools (Search / APIs)</text>
  <text x="600" y="320" class="label small">
    Web search, datasets, local knowledge, embeddings
  </text>

  <!-- Research Output -->
  <rect x="770" y="280" width="230" height="60" class="node" />
  <text x="885" y="304" class="label">📄 Research Summary</text>
  <text x="885" y="320" class="label small">
    Key cities, travel times, must-see points, notes
  </text>

  <!-- Itinerary Agent Node -->
  <rect x="200" y="380" width="280" height="60" class="node" />
  <text x="340" y="404" class="label">🗓 Itinerary Agent</text>
  <text x="340" y="420" class="label small">
    Day-by-day schedule, routing, timing
  </text>

  <!-- Itinerary Output Node -->
  <rect x="580" y="380" width="260" height="60" class="node" />
  <text x="710" y="404" class="label">📅 Proposed Itinerary</text>
  <text x="710" y="420" class="label small">
    Activities, ordering, travel between locations
  </text>

  <!-- Budget Agent Node -->
  <rect x="260" y="480" width="280" height="60" class="node" />
  <text x="400" y="504" class="label">💰 Budget Agent</text>
  <text x="400" y="520" class="label small">
    Flights, hotels, transport, activity costs
  </text>

  <!-- Budget Output Node -->
  <rect x="620" y="480" width="260" height="60" class="node" />
  <text x="750" y="504" class="label">📊 Cost Estimation</text>
  <text x="750" y="520" class="label small">
    Total + per-day breakdown
  </text>

  <!-- Validation / Final Answer Node -->
  <rect x="360" y="570" width="380" height="40" class="node" />
  <text x="550" y="590" class="label">
    ✅ Validation & Final Answer
  </text>
  <text x="550" y="606" class="label small">
    Check feasibility, refine, respond to user
  </text>

  <!-- Arrows -->

  <!-- User -> Orchestrator -->
  <line x1="370" y1="120" x2="410" y2="205" class="arrow" />

  <!-- Orchestrator -> Research Agent -->
  <line x1="540" y1="230" x2="265" y2="280" class="arrow" />

  <!-- Research Agent -> Tools -->
  <line x1="410" y1="310" x2="470" y2="310" class="arrow" />

  <!-- Tools -> Research Summary -->
  <line x1="730" y1="310" x2="770" y2="310" class="arrow" />

  <!-- Research Summary -> Itinerary Agent -->
  <line x1="885" y1="340" x2="340" y2="380" class="arrow" />

  <!-- Itinerary Agent -> Itinerary Output -->
  <line x1="480" y1="410" x2="580" y2="410" class="arrow" />

  <!-- Itinerary Output -> Budget Agent -->
  <line x1="710" y1="440" x2="400" y2="480" class="arrow" />

  <!-- Budget Agent -> Budget Output -->
  <line x1="540" y1="510" x2="620" y2="510" class="arrow" />

  <!-- Itinerary Output + Budget Output -> Validation -->
  <line x1="710" y1="440" x2="550" y2="570" class="arrow" />
  <line x1="750" y1="540" x2="550" y2="570" class="arrow" />

  <!-- Validation -> User -->
  <line x1="550" y1="610" x2="550" y2="640" class="arrow" />
  <text x="550" y="647" class="subtitle">🧳 Final trip plan returned to user</text>

</svg>
