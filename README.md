# agent-skills

My Personal Agent Skills. Use them if you want. Don't come at me for them. They are meant for me.

Licensed MIT, see [LICENSE](LICENSE).

## Skills in this repo

- [`server-rendered-web`](server-rendered-web/SKILL.md): Semantic HTML, modern CSS, Open Props, HTMX, and Alpine.js, while respecting the stack a project already has.
- [`agent-integration-design`](agent-integration-design/SKILL.md): CLI for local tooling, HTTP API for services, MCP only where it earns its keep.
- [`mcp-server-builder`](mcp-server-builder/SKILL.md): Build remote MCP servers in Go over Streamable HTTP, as real production services rather than local command wrappers.
- [`html-document`](html-document/SKILL.md): Print-first HTML documents that export cleanly to PDF: proposals, quotes, reports, letters. Ships a neutral template.
- [`html-presentation`](html-presentation/SKILL.md): Editorial or cinematic reveal.js decks as one self-contained HTML file. Ships a neutral template.

`agent-integration-design` decides whether to build an MCP server at all;
`mcp-server-builder` takes over once that decision is made.

`html-document` and `html-presentation` own craft, not brand. Each carries the
brand as a single `:root` block of CSS custom properties, so branding one is
editing that block. Both defer to a project-local brand or `make-*` skill when
one exists, which is what keeps them from fighting house skills in a company
repo. See the brand contract table in either skill.

### Installing these

The skills CLI discovers `SKILL.md` files recursively, so the top-level-per-skill
layout here installs directly:

```bash
# List available skills
npx skills add lgforsberg/agent-skills --list

# Install one skill globally for Cursor
npx skills add lgforsberg/agent-skills \
  --skill server-rendered-web \
  --global \
  --agent cursor

# Install several
npx skills add lgforsberg/agent-skills \
  --skill server-rendered-web \
  --skill agent-integration-design \
  --skill mcp-server-builder \
  --global \
  --agent cursor
```

For local development of this repo, clone it and symlink (or use `--copy`) into
your agent skills directory instead.

### Layout

One folder per skill, each with a `SKILL.md` carrying `name` and `description`
frontmatter. Supporting `reference.md`, `examples.md`, or `scripts/` live beside
it in the same folder. No `skills/` wrapper is required.

## Other skills I use

Not mine, kept here so I can rebuild a machine without hunting them down.
Credit and licences belong to their authors.

### Vercel Agent Browser

```bash
brew install agent-browser
agent-browser install

npx skills add vercel-labs/agent-browser \
  --skill agent-browser \
  --global \
  --agent cursor
```

### The rest

```bash
npx skills add zarazhangrui/frontend-slides \
  --global \
  --agent cursor

npx skills add anthropics/skills \
  --skill frontend-design \
  --global \
  --agent cursor

npx skills add addyosmani/agent-skills \
  --skill api-and-interface-design \
  --global --agent cursor

npx skills add addyosmani/agent-skills \
  --skill code-review-and-quality \
  --global --agent cursor

npx skills add addyosmani/agent-skills \
  --skill performance-optimization \
  --global --agent cursor

npx skills add addyosmani/agent-skills \
  --skill documentation-and-adrs \
  --global --agent cursor

npx skills add github/awesome-copilot \
  --skill sql-code-review \
  --global --agent cursor

npx skills add trailofbits/skills \
  --skill differential-review \
  --global --agent cursor

npx skills add anthropics/skills \
  --skill skill-creator \
  --global --agent cursor
```
