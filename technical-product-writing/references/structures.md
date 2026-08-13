# Document shape and technical description

Choose structure from purpose. Do not mechanically use Introduction, Features,
Benefits, Conclusion.

Use only the sections that help the reader. Do not turn every paragraph into a
section. Prefer descriptive headings ("How reports become cases") over generic
ones ("Processing"). Avoid cute headings when clarity matters.

Start with useful information. A reader should quickly understand what is being
described, why they should care, and whether the material is relevant. Skip
lengthy scene-setting unless the context genuinely requires it.

Do not add a conclusion because documents traditionally have one. End when the
useful information has been delivered. Sales and website material may need a
call to action. Technical descriptions may end on limitations, deployment, or
next steps.

Calls to action should name a real next step (request API access, schedule a
technical review, read the API documentation). Avoid "Learn more", "Get started
today", and "Unlock your potential" unless they genuinely fit.

## Product page

- Clear statement of purpose
- Problem or context
- Capabilities
- How it works
- Integration or workflow
- Differentiation
- Next step

## Technical overview

- Purpose
- Architecture
- Components
- Data flow
- Interfaces
- Operations
- Security
- Constraints

## Service description

- Service purpose
- Scope
- Delivery
- Inputs
- Activities
- Outputs
- Responsibilities
- Limitations

## Executive summary

- Situation
- Proposed capability
- Business relevance
- Implementation implications
- Key considerations

## Architecture

Help the reader form a mental model: components, responsibilities, boundaries,
request or data flow, state ownership, dependencies.

Avoid narrating source-code structure unless that is what the reader needs.

A useful architecture description answers: What are the major parts? What does
each part own? How do they communicate? Where does state live? What crosses
trust boundaries? What happens during a normal request or workflow?

## APIs and integrations

Describe known characteristics: purpose, authentication, protocol, endpoint
model, request and response structure, pagination, error behavior, rate limits,
asynchronous behavior, webhooks, idempotency, versioning.

Do not invent these when they are not documented. For product-level API
descriptions, explain what the API enables rather than reproducing reference
documentation.

## Data

Distinguish source data, derived data, cached data, customer data, metadata, and
operational data. Be precise about retention, ownership, replication,
consistency, and processing only where known. Do not infer data-protection
characteristics from architecture alone.

## Editing existing material

1. Preserve the factual meaning
2. Preserve established terminology
3. Remove ambiguity
4. Correct grammar and awkward construction
5. Reduce unnecessary repetition
6. Improve structure where useful
7. Preserve the author's natural voice
8. Avoid adding claims merely to make the text stronger
