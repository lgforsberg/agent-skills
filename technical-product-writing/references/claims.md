# Claims, evidence, and dangerous language

Technical accuracy comes before persuasive language. Read this before stating
capabilities, results, security properties, competitors, or commercial terms.

## What not to invent

Do not invent or imply unsupported product capabilities, features, integrations,
APIs, protocols, compatibility, automation, benchmarks, performance, customer
results or names, testimonials, market share, certifications, compliance,
security properties, uptime, availability guarantees, deployment models,
scalability, geographic coverage, support commitments, roadmap items, release
dates, pricing, or commercial terms.

Do not turn possibilities into capabilities.

Distinguish clearly between what exists, what is supported, what can be
configured, what is possible, what is planned, what is being evaluated, and what
is recommended.

If a claim cannot be supported by the available material, omit it or qualify it.

## The evidence ladder

**Direct fact.** State it plainly.

> The API supports JSON responses.

**Supported consequence.** State it carefully.

> JSON responses make the API straightforward to consume from automated
> workflows.

**Inference.** Make the inference visible if it is material.

> This architecture should also make horizontal scaling relatively
> straightforward.

**Unknown.** Do not guess. If the information matters and is unavailable, mark
it as needing verification.

## Outcomes

Good:

> Results can be returned as structured JSON, allowing the service to be
> integrated into automated workflows.

Bad:

> This dramatically reduces operational costs.

The latter requires evidence. Use "can", "allows", "enables", or "reduces the
need for" for a logical consequence. Do not use quantified benefits without
evidence.

## Sales claims

Do not use manipulation as a substitute for substance. Avoid fake scarcity,
invented urgency, unsupported ROI, fear-based exaggeration, false certainty,
attacking competitors, and uniqueness claims without evidence.

## Competitors

Remain factual. Distinguish known differences from assumptions. Do not insult,
invent weaknesses, or speculate about proprietary implementation. Prefer
describing your own approach and verified differences.

## Security

Be particularly careful. Do not describe something as secure, fully secure,
compliant, zero trust, encrypted, privacy preserving, or hardened unless the
underlying statement is known and scoped.

Prefer:

> API requests require authenticated access tokens.

rather than:

> The API is completely secure.

When encryption is relevant, state what is encrypted, where, when, and using
what mechanism if known. Do not infer compliance from technical controls.
