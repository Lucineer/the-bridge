# The Bridge — TUI-First Agent Interface

You watch your agent work. Every command, output, and reasoning step streams live in your terminal, in order, with nothing hidden or collapsed.

The Bridge is a terminal-native interface for [Cocapn Fleet](https://github.com/user-attachments/assets/26b003bf-81bf-4142-bcc4-6a7a9d0801d4) agents. It runs alongside your editor as a persistent, auditable log of all agent activity.

**Live URL:** [https://the-bridge.casey-digennaro.workers.dev](https://the-bridge.casey-digennaro.workers.dev)

## Why It Exists

Agent UIs often hide work behind summaries or chat interfaces. You see a final change, not the process. This was built for supervision: to let you watch and verify each step as it happens, directly in your terminal.

## Quick Start

1.  **Fork** this repository.
2.  **Deploy** to Cloudflare Workers (use the "Deploy with Workers" button). Deployment typically completes within a minute.
3.  Optionally, tweak TUI colors or prompts in `src/index.js`.
4.  Configure your Cocapn Fleet agent to use your deployed Bridge endpoint.

Your instance is now running. You control it.

## Architecture

A lightweight WebSocket server built on Cloudflare Workers. It streams structured events (commands, outputs, prompts) from your Fleet agent to a terminal client and relays your input back. Credentials and agent logic remain entirely on your side.

## Features

- **Terminal-First**: Runs anywhere a terminal does: locally, over SSH, or in tmux. No browser or IDE required.
- **Continuous Log**: Every emitted line—commands, stdout, agent reasoning—scrolls in a single, uninterrupted stream.
- **Pause/Resume Interaction**: Type at any time to pause the agent and input a response. No toggle commands or mode switches.
- **Credential Isolation**: Agents cannot access tokens. When needed, they print an auth link for you to handle directly.
- **Fork & Own**: MIT licensed, zero dependencies, and designed to run on your Cloudflare Workers account. You own the deployment.

## Limitations

- **Single Session**: Each Bridge instance supports one active agent connection at a time. Concurrent sessions require multiple deployments.
- **Agent Dependency**: This is an interface layer. It requires a running Cocapn Fleet agent backend to function.

<div style="text-align:center;padding:16px;color:#64748b;font-size:.8rem"><a href="https://the-fleet.casey-digennaro.workers.dev" style="color:#64748b">The Fleet</a> &middot; <a href="https://cocapn.ai" style="color:#64748b">Cocapn</a> &middot; Superinstance and Lucineer (DiGennaro et al.)</div>