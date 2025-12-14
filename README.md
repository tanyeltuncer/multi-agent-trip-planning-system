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

flowchart TD

    %% USER INPUT
    A[🧑 User Request<br/>e.g., 'Plan a 5-day trip to Japan'] --> B

    %% ENTRY: ORCHESTRATOR / STATE MACHINE
    B[🎛️ State Machine<br/>Start Workflow] --> C

    %% AGENT 1: RESEARCH
    C --> D[🔎 Research Agent<br/>Gather destination info]
    D --> D1[🌍 Retrieve data<br/>Weather, attractions,<br/>transport, costs]
    D1 --> D2[📝 Summarize insights]
    D2 --> E

    %% AGENT 2: ITINERARY
    E[➡️ Pass to Itinerary Agent] --> F
    F[🗓 Itinerary Agent<br/>Generate day-by-day plan] --> F1
    F1[📅 Build schedule<br/>Activities, timing, routing] --> F2
    F2[🧩 Validate feasibility] --> G

    %% AGENT 3: BUDGETING
    G[➡️ Pass to Budget Agent] --> H
    H[💰 Budget Agent<br/>Estimate total costs] --> H1
    H1[✈️ Flights • 🏨 Hotels<br/>🚇 Transport • 🎟 Activities] --> I

    %% AGENT 4: VALIDATOR
    I --> J[🧠 Validation Agent<br/>Check consistency]
    J --> J1[✔ Verify itinerary, budget,<br/>timing, missing info]

    %% FINAL OUTPUT
    J1 --> K[🧳 Final Trip Plan<br/>- Research summary<br/>- Full itinerary<br/>- Budget breakdown]

    K --> L[📤 Output to User]
