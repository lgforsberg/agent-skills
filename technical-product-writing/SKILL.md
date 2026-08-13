---
name: technical-product-writing
description: Write accurate, clear, credible technical, product, system, service, sales, and customer-facing content. Use for product and service descriptions, system overviews, technical explainers, solution descriptions, proposals, brochures, website copy with technical substance, executive summaries, and technical sales material. Also use when asked to describe a product, explain how a system or service works, draft a service offering, write a technical overview, or produce sales material that must stay factually true. Preserve established terminology, facts, positioning, and voice. Never invent capabilities or claims. For conversion headlines and landing-page persuasion, use copywriting. For polishing existing marketing copy, use copy-editing. For UI microcopy, use ux-writing. For Diátaxis software docs (tutorials, how-tos, reference), use documentation-writer. For creating the shared positioning file, use product-marketing.
---

# Technical Product Writing

Write technically accurate, useful, and credible content for products, systems,
services, and organisations.

This skill sits between pure technical documentation and marketing copy. Its
purpose is to explain real technology clearly and persuasively without
exaggerating, inventing capabilities, or burying useful information under
corporate language.

## Neighbouring skills

Once this skill has triggered, stay in its lane:

| Need | Skill |
| --- | --- |
| Shared positioning, ICP, messaging file | `product-marketing` |
| Conversion headlines, landing-page persuasion | `copywriting` |
| Polish of existing marketing copy | `copy-editing` |
| UI strings, errors, empty states | `ux-writing` |
| Tutorials, how-tos, reference (Diátaxis) | `documentation-writer` |
| Product, system, service, or technical sales prose that must stay true | this skill |

If `.agents/product-marketing.md` exists, read it for audience, positioning,
terminology, and objections. Do not create that file unless the task asks for it.
User instructions and project source always take precedence over it.

## Workflow

### 1. Inspect before writing

Prefer information in this order:

1. Explicit instructions from the user
2. Existing project documentation and source material
3. Existing product or company terminology
4. Existing website, sales, proposal, or marketing material
5. Technical implementation and source code when relevant
6. Project-local context files
7. Reasonable inference, clearly identified as inference

Never replace known facts with assumptions.

If the project already has terminology, positioning, naming, tone, or
architecture, preserve it unless asked to change it. Do not rename concepts to
make the writing sound more polished. Do not impose this skill's preferred
vocabulary on an existing product.

When sources disagree, prefer the most authoritative or recent one, and keep
uncertainty visible rather than picking the convenient version.

### 2. Choose audience and mode

Write for the intended reader. Adjust terminology, depth, and explanation to
them. Technical sophistication shows up as precision and useful explanation, not
as extra vocabulary.

Pick a mode from the task, then read [`references/modes.md`](references/modes.md)
for the mode you chose. Read [`references/structures.md`](references/structures.md)
only if you need a document shape, heading advice, or help describing
architecture, APIs, or data.

| Mode | For |
| --- | --- |
| Technical | Engineers, architects, operators, evaluators |
| Product | Customers, partners, product teams |
| Executive | Management and decision-makers |
| Sales | Prospects and commercial conversations |
| Explainer | Knowledgeable readers who are not specialists here |
| Service description | Professional or managed services |
| System description | Platforms, infrastructure, internal systems |
| Website / brochure | Public pages, product sheets, concise marketing |

### 3. Write from behavior, not adjectives

Describe what the system actually does. Behavior establishes credibility better
than adjectives.

Weak:

> The platform provides powerful and comprehensive domain intelligence.

Better:

> The platform collects WHOIS/RDAP, DNS, TLS, HTTP, and related domain data and
> exposes it through a common interface for analysis and automation.

It is useful to explain why a capability matters. It is not useful to invent
outcomes. "Can", "allows", "enables", or "reduces the need for" are appropriate
for a logical consequence. Quantified benefits need evidence.

Read [`references/claims.md`](references/claims.md) before stating capabilities,
results, security properties, competitors, or commercial terms.

### 4. Match the existing voice

When editing or extending material, keep its established voice unless asked to
change it: depth, directness, informality, industry terms, sentence length,
person, spelling, product naming, capitalization.

Do not make every organisation sound like the same SaaS company. Improve the
writing without erasing the author.

If wording looks deliberately precise for legal or contractual reasons, edit
conservatively. Do not silently change commercial, legal, technical, or
contractual meaning.

### 5. Check before handing over

Run the quality check at the end of this file. Fix anything it catches rather
than decorating around it.

## Style

Prefer specific, concrete, concise, active, natural, and credible. Useful beats
decorative. Direct statements beat rhetorical setup. Meaningful examples beat
adjectives.

Use short sentences when they help. Do not force every sentence to be short.
One idea per paragraph is usually enough. Use lists when the information is
list-shaped; do not turn ordinary prose into endless bullets.

Use the correct term. For a mixed audience: use it, explain it once if needed,
then keep using it. Expand unfamiliar acronyms on first use. Preserve product,
service, protocol, and company names exactly as the project uses them.

Do not produce recognisably synthetic corporate prose. Do not open with
landscape, connected-world, or "now more than ever" scene-setting. Do not create
artificial importance around ordinary features. Words such as innovative,
revolutionary, cutting-edge, powerful, robust, seamless, comprehensive,
next-generation, best-in-class, state-of-the-art, transformative, game-changing,
and holistic are acceptable only when they communicate something specific and
defensible.

Skip constructions such as "not only X, but also Y", "whether you're X, Y, or Z",
"designed to empower", "unlock the power of", and "takes X to the next level".
Skip fake quotations, forced enthusiasm, and a recap at the end of every section.

## Scope

Write the document requested. Depth follows audience, destination, requested
length, and stage of the journey. Do not expand a short service description into
a white paper, turn technical documentation into marketing, or turn sales
material into an architecture specification.

If the project already defines voice, style, terminology, messaging, templates,
or branding, follow those and use this skill to improve execution inside them.

## Quality check

**Accuracy.** Are factual claims supported? Are capabilities distinguished from
plans and possibilities? Have metrics, certifications, customers, or performance
claims been invented? Is the terminology correct?

**Audience.** Is the detail right? Does the reader understand what the thing does?
Is internal terminology explained or removed?

**Clarity.** Can vague claims become concrete behavior? Are sentences
unnecessarily complicated? Is the structure easy to scan?

**Credibility.** Does this sound like someone who understands the subject? Is
anything oversold? Are generic marketing claims still sitting where facts should
be?

**Voice.** Does it preserve the project's style? Does it sound natural? Have
common AI-writing patterns crept in?

**Purpose.** Does every major section serve the requested task? Is the length
right for the destination?

## Final principle

Understand the technology. Understand the audience. State what is true. Explain
why it matters. Do not decorate weak understanding with stronger adjectives.
