# Bifrost (source facts for eval)

Product: Bifrost (not BiFrost, not BIFROST)
Site: https://bifrost-mail.com
Source: https://github.com/lgforsberg/bifrost
License: MIT
Language: Go
Version in the current site hero: 1.25.1

What it is: a command-line email client and Go library.

Protocols it speaks: IMAP, SMTP, MIME. Against any standards-compliant provider.

Design constraints of the CLI:

- built for non-interactive and agent-driven use
- no TTY assumptions
- no editor spawning
- no prompts
- structured `--json` output on every command
- human-readable output by default

Install:

```
go install github.com/lgforsberg/bifrost/cmd/bifrost@latest
```

Not in this source, therefore unknown: POP3, GUI, hosted mail, customer logos, speed comparisons, "Fortune 500", uptime, number of users.
