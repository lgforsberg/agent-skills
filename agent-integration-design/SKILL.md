---
name: agent-integration-design
description: Choose the right interface for exposing functionality to AI agents, favouring CLIs for local tooling, HTTP APIs for application services, and MCP only where it earns its keep. Use when an MCP server is being proposed, when designing a new tool or service boundary that agents will consume, or when deciding between a CLI, an API, an SDK, and MCP.
---

# Agent Integration Design

Choose the simplest and most appropriate integration boundary for the problem.

Do not choose MCP merely because the consumer is an AI agent.

## Core principle

Use established software interfaces where they already solve the problem well.

Prefer:

- CLI commands for local tools and developer workflows
- HTTP APIs for normal networked application services
- native database clients and query tools for database access
- SDKs or libraries for in-process integration
- MCP for remotely accessible capabilities where it provides meaningful value to
  AI clients

MCP is not the default wrapper around every capability an agent may need.

## Local agent functionality

When functionality executes on the same machine as the coding agent, prefer a CLI.

This covers most developer tooling: browser automation, repository utilities, code
generators, deployment helpers, file transformation, database utilities, test
runners, and project-specific automation. The agent can invoke the CLI directly.

A local MCP server that merely converts MCP tool calls into shell commands adds
protocol complexity, extra processes, configuration, failure modes, and debugging
overhead, and buys nothing in return.

Do not create an MCP wrapper merely to expose an existing CLI command. If a good
CLI already exists, teach the agent to use the CLI.

## CLI design for agents

When building local tooling intended for agent use, make the CLI agent-friendly:

- deterministic commands and clear exit codes
- structured output, with JSON available where useful
- concise stdout, errors on stderr
- non-interactive operation with explicit flags
- predictable command names and a useful `--help`
- idempotent operations where appropriate

Avoid interfaces that require an interactive terminal when an agent is the intended
consumer.

## HTTP APIs

If the capability is fundamentally an application service rather than an
agent-specific one, prefer a normal HTTP API. Account management, billing,
application data, business workflows, CRUD services, internal microservices,
asynchronous jobs, and webhooks all belong here.

Do not turn a normal application API into an MCP server merely because agents may
consume it. Agents can use an API client, CLI client, or SDK.

A service may expose both a normal API and an MCP interface when the MCP interface
provides genuine additional value.

## When MCP is appropriate

Prefer MCP when the capability is intentionally exposed as a reusable remote
service for AI clients and benefits from MCP semantics. For example:

- remote tool services and hosted agent infrastructure
- reusable context providers
- shared organisational AI capabilities
- services intended to work across multiple MCP-compatible clients
- remotely hosted systems where tool discovery is valuable
- services exposing resources, prompts, or other MCP-native capabilities

An MCP server should represent a meaningful service boundary, not a disposable
wrapper around a command.

Where MCP is the answer, build it as a properly hosted Streamable HTTP service and
treat it as production software. For how to build one, apply the
`mcp-server-builder` skill.

## Ownership

Good:

```
AI client → MCP server → application / service layer → database / API
AI client → MCP server → remote service integrations
```

Usually bad:

```
AI client → MCP server → shell command → application
```

Usually unnecessary:

```
AI client → local MCP server → CLI command
```

For that last case, prefer:

```
AI agent → CLI command
```

## Existing systems

Do not rewrite an existing integration simply to conform to these preferences.

If a project already has an established MCP, API, CLI, RPC, or SDK interface,
understand it first, preserve it, and work within its conventions. Only propose
migration when there is a concrete problem to solve.

These rules primarily guide new architectural decisions.

## Decision checklist

Before creating an MCP server, ask:

1. Is this functionality local to the agent's machine? Prefer a CLI.
2. Is this fundamentally a normal application service? Prefer an HTTP API.
3. Does a suitable API or CLI already exist? Use it directly.
4. Does MCP provide meaningful interoperability, discovery, context, or
   AI-specific capabilities? MCP may be appropriate.
5. Will this run as a genuine remote service used by one or more AI clients?
   Streamable HTTP MCP is a strong candidate.
6. Is the proposed MCP server mostly forwarding calls to shell commands?
   Reconsider the architecture.

## General philosophy

Prefer interfaces that remain useful without an AI agent.

A good CLI should be a good CLI. A good API should be a good API. A good MCP server
should be a good network service designed around AI-client interaction.

Do not confuse protocol adoption with architecture.
