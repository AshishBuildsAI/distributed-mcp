# Distributed Model Context Protocol (dMCP) distributed-mcp
Distributed Model Context Protocol (dMCP) is a proposed extension to the original Model Context Protocol (MCP), introducing asynchronous, event-driven, and distributed communication between agents, models, and context providers.

## Table of Contents
- [Overview](#overview)
- [Why Distributed MCP?](#why-distributed-mcp)
- [Architecture](#architecture)
- [Core Message Types](#core-message-types)
- [Status](#status)
- [Author](#author)
- [License](#license)
## Overview

**Distributed MCP (dMCP)** is a proposed extension to the Model Context Protocol (MCP), introducing asynchronous, event-driven, and distributed communication between agents, models, and context providers.

Where MCP defines tightly coupled, synchronous interaction patterns, **dMCP enables large-scale, loosely coupled agentic ecosystems** where reasoning happens independently and context evolves through message-driven events.

---

## Why Distributed MCP?

Modern intelligent systems — like human teams, neural networks, and ecological systems — operate asynchronously, not in rigid synchronous loops.

Distributed MCP addresses:
- **Scalability bottlenecks** in synchronous agent systems
- **Agent parallelism** without global blocking
- **Fault tolerance** through decoupled, durable messaging
- **Real-world modeling** of independent, adaptive agent behaviors

**Key Features:**
- Event-driven architecture (context updates, prompts, responses)
- Loose coupling between agents
- Resilient to delays, failures, and offline participants
- Based on standard messaging brokers (e.g., AMQP/RabbitMQ, NATS)

---

## Architecture

![Architecture Diagram](diagrams/dmcp_architecture.png)

Agents, Models, and Context Providers communicate asynchronously through a distributed message broker, using defined event types like `context_update`, `prompt_request`, and `prompt_response`.

---

## Core Message Types

| Type | Purpose |
|:-----|:--------|
| `context_update` | Share updated information about the world or internal state |
| `prompt_request` | Ask a model or agent to reason based on context |
| `prompt_response` | Respond to prompts with generated outputs |
| `error_notification` | Share exceptions or error conditions |
| `agent_heartbeat` | Health and presence signaling |

---

## Status

🛠 **Version:** Draft v0.1  
📆 **Last Updated:** April 2025

Distributed MCP is an open, evolving specification.  
**Feedback, collaboration, and pull requests are welcome!**

## Contributing

I welcome issues, discussions, pull requests, and feedback!  
Let's collaboratively build the future of scalable, distributed agent systems.

---

## Author

Ashish Madkaikar  
[@AshishBuildsAI](https://x.com/AshishBuildsAI)

---

## License

This project is licensed under the MIT License.