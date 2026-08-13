# Relay (working name) — source facts for eval

What it is: a small Go service that accepts outbound email from internal tools and agents over HTTP, then sends it through an existing SMTP relay.

Who it is for: operators who do not want every agent to hold SMTP credentials.

What exists today:

- HTTP API, authenticated with a bearer token
- one upstream SMTP relay, configured in a YAML file
- per-request timeout
- JSON error responses
- structured logs
- MIT license
- single binary

What it does not have yet (explicitly not shipped):

- a web UI
- bounce handling
- multiple upstreams
- a queue that survives process restart

Unknown, not in this source: customers, case studies, ROI, cost savings, message volume, delivery rates, SLAs, competitors, pricing.
