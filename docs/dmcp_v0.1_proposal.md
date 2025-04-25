Distributed Model Context Protocol (dMCP) v0.1

Overview

Distributed Model Context Protocol (dMCP) is a proposed extension to the original Model Context Protocol (MCP), introducing asynchronous, event-driven, and distributed communication between agents, models, and context providers.

While MCP successfully defines tightly coupled, synchronous interaction patterns for model reasoning, dMCP enables large-scale, loosely coupled agentic ecosystems where reasoning happens independently and context evolves over time through events.

Motivation

As the number and diversity of autonomous agents grow, synchronous, request-response communication becomes a bottleneck. Real-world agent systems need:

Asynchronous communication: Agents publish and consume context updates at independent timescales.

Loose coupling: Producers and consumers of context need not know each other's identity.

Durability and resilience: Context and tasks survive temporary failures or disconnections.

Parallelism: Multiple agents can reason simultaneously on partially overlapping contexts.

Distributed MCP addresses these requirements by extending MCP into an event-driven, message-brokered architecture, while preserving its core principles of structured context management and model alignment.

Scalability Challenge in Synchronous Agent Systems

The original MCP design assumes direct, blocking request-response communication between agents and models. While this works well for small, tightly scoped systems, it becomes a major bottleneck in larger multi-agent environments:

Blocking Fragility: One slow agent stalls the entire chain of reasoning.

Sequentialism: Agents must reason one after another, missing opportunities for parallel thought.

Brittle Failures: Timeouts or unresponsive agents collapse entire multi-agent processes.

Resource Strain: Requires all agents to be online and responsive simultaneously.

Real-world intelligent systems (human organizations, ecosystems, neural networks) operate asynchronously and tolerate delays naturally. To mirror this robustness, agentic systems must evolve beyond synchronous blocking models.

Distributed MCP embraces this reality by allowing agents to communicate via durable message exchanges, making progress independently while asynchronously integrating shared context.

These insights are drawn from practical experience building AI Fireside Chat frameworks, where real-world agentic conversations revealed the natural need for asynchronous coordination.

Key Concepts

Concept

dMCP

MCP

Communication

Asynchronous, message-based

Synchronous, direct

Coupling

Loose

Tight

Context Evolution

Event streams, updates over time

Immediate context bundle

Reliability

Message durability, retries

Immediate or fail-fast

Memory Scope

Distributed and persistent

Local to session/call

dMCP Architecture

Agents, models, and services communicate via a distributed message bus (e.g., AMQP/RabbitMQ, Redis Streams, NATS).

Core Components

Context Producers: Publish partial or full context updates.

Context Consumers: Subscribe to relevant context updates.

Model Executors: Listen for prompts or decision tasks, produce outputs, and optionally publish them.

Context Broker: Routes events between participants, manages topics/queues.

Session Manager (optional): Maintains coherent long-running multi-agent sessions.

Message Types

Type

Description

context_update

New or modified context payloads

prompt_request

Request for model reasoning or task execution

prompt_response

Response to a prompt or decision task

error_notification

Errors or exceptions during processing

agent_heartbeat

Health monitoring and presence signaling

Example Flow

Sensor Agent publishes a context_update: "New event: Pressure anomaly detected."

Planning Agent subscribes to anomalies, receives event, triggers a prompt_request to a Model Executor.

Model Executor processes request asynchronously, emits a prompt_response suggesting mitigation steps.

Control Agent picks up the plan from the bus and executes real-world action.

All of this happens without any direct synchronous calls.

Formal dMCP Message Structure

Each message should be a JSON object with:

{
  "dMCP_version": "0.1",
  "type": "context_update | prompt_request | prompt_response | error_notification | agent_heartbeat",
  "session_id": "optional session grouping",
  "timestamp": "ISO 8601 UTC",
  "sender_id": "agent-name-or-uuid",
  "payload": { "structured_data": "depends on message type" }
}

Backward Compatibility with MCP

dMCP is a superset of MCP ideas: agents operating within a synchronous MCP session could be wrapped as microservices under dMCP.

Adapters can bridge dMCP event streams into traditional MCP synchronous APIs where needed.

Future Work

dMCP-Streams: Formalize persistent event replay for training models.

Security: Define optional signing and encryption layers.

Quality of Service (QoS): Define message priority, retries, and dead-letter queues.

Agent Profiles: Standardize agent capabilities and presence announcements.

License

Distributed MCP (dMCP) v0.1 Proposal © 2025 Ashish Malpekar

Released under an open-source, permissive license to encourage innovation, community improvement, and practical adoption in real-world distributed agent systems.

Status

This is a draft proposal (v0.1). Feedback and contributions are welcome.

Please open an issue or a pull request if you would like to discuss extensions, examples, or integration pathways.

Author

ashish@madkaikar.com 

@AshishBuildsAIApril 2025