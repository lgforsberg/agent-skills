---
name: mcp-server-builder
description: Design and implement production-quality remote Model Context Protocol servers in Go using Streamable HTTP. Use when building, reviewing, deploying, or debugging an MCP server, once MCP has been established as the right integration boundary. Builds genuine network services rather than local command wrappers.
---

# MCP Server Builder

Build MCP servers as proper remotely hosted network services.

This skill assumes MCP has already been selected as the appropriate integration
architecture. If that is still open, apply the `agent-integration-design` skill first.

## Check the spec before writing code

The MCP specification changes materially between revisions. Handshake, transport
requirements, and available primitives have all been rewritten in past revisions,
and features have been deprecated outright.

Never implement from remembered protocol behavior. Before writing code, read:

- the current MCP specification
- the release notes and docs for the SDK version being used

Then pin the SDK version and record which protocol revision the server targets.

## Architecture

```
AI client
  → Streamable HTTP
    → MCP server
      → application / domain layer
        → database / APIs / services
```

The MCP server should be deployable and operable like any other production HTTP
service.

Do not build MCP servers whose primary purpose is wrapping local CLI commands or
shell scripts. For local agent tooling, build a CLI instead.

## Transport

For new remote MCP servers, use the current MCP Streamable HTTP transport.

Do not use STDIO unless explicitly requested for compatibility or local deployment.

Prefer stateless operation. Recent spec revisions require it to serve the newest
protocol version over Streamable HTTP, and stateful sessions cause clients to
negotiate down. Verify the current requirement against the spec rather than
assuming this still holds.

Do not assume the MCP client runs on localhost.

## Language

Use Go.

Use the official Model Context Protocol Go SDK. Prefer standard `net/http`
conventions, explicit dependency injection, context propagation, graceful
shutdown, structured logging, and small interfaces. Avoid unnecessary frameworks.

Do not use Python, TypeScript, or Node.js merely because MCP examples and SDKs
commonly use them, unless:

1. the existing project already uses them,
2. the user explicitly requests them, or
3. there is a concrete technical requirement that makes them appropriate.

If an existing project already uses another suitable language and architecture,
follow the existing project rather than rewriting it.

## Tool design

Tools should represent meaningful domain operations.

Prefer operations coarse enough that an agent can accomplish a useful task without
excessive round trips. Avoid giant multipurpose tools, and avoid trivially thin
tools when a more meaningful domain operation is available.

Tool descriptions should explain what the tool does, when to use it, its
constraints, and any meaningful side effects. Names should be stable, descriptive,
and action-oriented.

## Tool inputs

Use explicit schemas with meaningful field names, constrained values, useful
descriptions, and server-side validation.

Avoid forcing clients to construct opaque command strings.

Bad:

```
execute(command: string)
```

Better:

```
search_domains(query, status, created_after, limit)
```

Never expose arbitrary shell execution as an MCP tool unless that capability is
itself the product being built.

## Tool results

Return enough information for the agent to make its next decision without flooding
the context window. Prefer structured data, and support filtering, pagination, or
field selection wherever a result set can grow unbounded.

Errors should be actionable and should distinguish expected domain failures from
internal server failures.

## Choosing the right primitive

Do not model everything as a tool. Use resources or other protocol capabilities
where they represent the information or interaction more naturally, and check the
current spec for which primitives are live rather than assuming.

## Service concerns

Treat the MCP endpoint as production infrastructure, with the operational
properties any public HTTP service needs.

Two are specific to MCP and easy to miss:

- **Origin and DNS rebinding protection.** MCP clients are frequently browsers or
  local applications, so validate `Origin` and bind deliberately.
- **Cancellation.** Agents abandon requests routinely. Propagate cancellation into
  the domain layer rather than letting orphaned work continue.

## Authentication

Remote MCP servers should authenticate clients unless intentionally public.

Integrate with the surrounding product's existing auth rather than inventing a
custom security protocol. Keep authentication separate from authorization, and
enforce authorization per tool for the operation that tool exposes.

## Observability

Emit structured logs with request identifiers, plus latency, tool invocation, and
error metrics.

Never log credentials, tokens, secrets, or unnecessarily sensitive tool arguments.

## Layering

Keep database and domain logic out of MCP transport handlers:

```
MCP handler
  → application / domain service
    → repository / database layer
```

Use the existing project's database conventions.

## Testing

Test domain logic separately from MCP transport behavior.

Beyond normal service testing, cover the protocol surface specifically: connection
setup and capability discovery, tool discovery, invalid inputs, authorization
boundaries, cancellation mid-request, and concurrent sessions.

## Existing projects

Existing architecture takes precedence. Do not migrate languages, replace
frameworks or persistence layers, restructure an application, or introduce MCP into
unrelated components unless the task explicitly requires it.

## Documentation

Document the server's purpose, its MCP endpoint, authentication, available
capabilities, required configuration and environment variables, the deployment and
development workflow, and the protocol revision it targets.

Do not require developers to reverse-engineer tool behavior from source code.

## Final principle

An MCP server is a server. Design, implement, deploy, secure, monitor, and maintain
it as one.

If all that is needed is a command an agent can run locally, build a good CLI
instead.
