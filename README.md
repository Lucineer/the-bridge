# The Bridge — TUI-First Agent Interface

You've had this moment. You're several panels deep in your IDE, your agent is hidden behind a tab, and you just watched it modify files without a clear audit trail. It's asking for API keys, and you're granting a language model access to your infrastructure.

This provides an alternative.

The Bridge is a native terminal interface for Cocapn Fleet agents. It runs alongside your IDE, not inside it. It’s designed to be the primary place where you observe and interact with an agent.

---

## Why This Exists
Most agent interfaces integrate directly into the human's workspace—a VS Code sidebar, a browser tab, a popup. This often creates two separate contexts: yours and the agent's. You switch, you guess, and you risk silent breaks from a bad autocomplete.

We built this differently. The agent operates in the terminal. You observe. You intervene when needed. You keep control.

---

## Core Features
This is not another chat box.

✅ **Runs where terminals run**. Desktop, Codespaces, SSH, tmux, and remote sessions. It generally works where your terminal works.
✅ **Zero mode switching**. Type at any time to pause the agent. You're at a shell. Resume when ready. No toggle commands.
✅ **Full audit by default**. Every command, output, and decision scrolls in the log. You can always see what happened.
✅ **No credential handoff**. Agents stop and print an auth link for you to authenticate yourself. They never see tokens or passwords.
✅ **Plays nice with your setup**. Split it next to your editor. Use it with Claude Code or Copilot. It doesn’t fight for panel space.
✅ **Fork first**. MIT licensed, runs on Cloudflare Workers. You own every part.

**One honest limitation:** This is an interface. It requires a running Cocapn Fleet agent to be useful. You can't just install this and have an AI assistant; you need the agent runtime behind it.

---

## The Bridge Metaphor
```
┌─────────────────────────────────────────────────┐
│  Your Workspace (Editor, Browser, etc.)        │
│                                                 │
│  ┌──────────┐  ┌────────────────────────────┐   │
│  │   IDE    │  │      Your Main Focus       │   │
│  │  Panel   │  │   (You drive here)         │   │
│  │          │  │                            │   │
│  └──────────┘  └────────────────────────────┘   │
│                                                 │
│  ┌──────────┐  ┌────────────────────────────┐   │
│  │  Other   │  │    TERMINAL — THE BRIDGE   │   │
│  │  Tools   │  │                            │   │
│  │          │  │  Agent runs here. You watch.│   │
│  └──────────┘  │  Type to pause & take over.│   │
│                 │                            │   │
│                 │  Admiral > Captain > Helm  │   │
│                 └────────────────────────────┘   │
│                                                 │
└─────────────────────────────────────────────────┘
```
There’s no hidden state. This is a terminal you already know how to use. The agent is a guest in your session.

---

## Quick Start

1.  **Fork & Deploy** the Fleet agent runtime first: [Cocapn Fleet](https://github.com/your-repo/cocapn-fleet).
2.  **Clone this repository.**
3.  **Install dependencies:** `npm install`
4.  **Link your agent:** Configure the Bridge to connect to your running Fleet agent endpoint.
5.  **Run:** `npm start`

For detailed setup, deployment, and configuration, see the [Fleet documentation](https://the-fleet.casey-digennaro.workers.dev).

---

## How It Works
The Bridge connects to a Cocapn Fleet agent via its protocol. It streams the agent’s thoughts, commands, and outputs to your terminal. Your keystrokes are sent directly when the agent is active, or to the local shell when you pause it. Authentication happens via OAuth links you open yourself.

---

## Development
This is a TUI built for Node.js. Contributions are welcome.

-   `npm run dev` – Start the development server.
-   `npm run build` – Build for production.
-   `npm test` – Run the test suite.

---

Attribution: Superinstance & Lucineer (DiGennaro et al.).

---
<div>
  <a href="https://the-fleet.casey-digennaro.workers.dev">The Fleet</a> ∙ 
  <a href="https://cocapn.ai">Cocapn</a>
</div>