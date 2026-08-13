# Dispatch (source facts for eval)

Product: Dispatch
Site: https://dispatch-newsletter.com
Source: https://github.com/markedo-org/dispatch
License: MIT
Language: Go
Shape: one binary, typically deployed as a systemd service behind a reverse proxy

What it is: a self-hosted newsletter service. Subscriber lists, HTML newsletters, sending. Operated by humans and AI agents via REST API, CLI, and MCP.

Known capabilities:

- Multi-list subscriber management with double opt-in, unsubscribe, and status tracking
- HTML template newsletters with personalization (name, unsubscribe link, tracking pixel)
- Rate-limited sending with worker pool, retry logic, and per-recipient tracking
- Scheduled sends with background scheduler and cancellation
- Subscriber tags for segmentation and tag-filtered sends
- Open tracking via embedded pixel
- Bounce handling: SMTP 5xx classification, webhook endpoints (SES, Mailgun, generic), IMAP bounce monitor for RFC 3464 DSN reports
- REST API
- CLI for management, sending, importing, exporting
- Built-in MCP server: 30 tools, 4 resources
- Web UI for subscriber management and newsletter preview
- Interactive API docs at /docs (OpenAPI 3.0 + Scalar)
- Image hosting for newsletter assets
- CSV import/export
- Bot protection on public subscribe forms: honeypot fields, time-based checks, name sanitization, optional hCaptcha
- Transactional raw email via POST /api/v1/send/raw (auth codes, notifications) without editions or lists
- Email standards: RFC 2047 subject encoding, List-Id, List-Unsubscribe (RFC 2369 and RFC 8058 one-click), Feedback-ID, DKIM signing (RFC 6376), multipart/alternative with auto-generated plain text

Backends that ship: SMTP, AWS SES, Mailgun, SQLite.

On the roadmap, not shipped: Resend, PostgreSQL, MySQL.

Prerequisites: Go 1.24+, GCC (SQLite driver via CGo), and a sender (SMTP, SES, Mailgun, or a third-party relay).

Default listen address in the docs: 0.0.0.0:8025.

Not in this source, therefore unknown: hosted SaaS pricing, uptime SLAs, named customers, performance benchmarks, number of messages sent, geographic regions, support hours.
