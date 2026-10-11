# Self-hosting open-source Kortix

Kortix is open source and self-hostable: self-host is free, and you pay only your own model and compute bills. This page covers the commands this deployment template uses, the prerequisites, and the backups that matter.

## Prerequisites

A production self-host needs four things, and you can check each one before you install anything:

- A domain with A and AAAA records for the domain and for `api.<domain>`, both pointing at the box's IP.
- Ports 80 and 443 reachable, so the bundled Caddy proxy can get a TLS certificate.
- The `kortix` CLI on macOS or Linux, or WSL on Windows.
- A sandbox provider key for agent sessions.

## The commands

Install the CLI, then initialize, start and configure the stack:

```bash
curl -fsSL https://kortix.com/install | bash
kortix self-host init --domain kortix.example.com
kortix self-host start
kortix self-host configure
```

`kortix self-host status`, `kortix self-host logs` and `kortix self-host doctor` report what is happening while the stack comes up. To evaluate with no domain, `kortix self-host init --tunnel cloudflare` runs the stack behind a tunnel; the tunnel URL changes on every restart, so use it for evaluation rather than production.

## What runs where

Kortix runs as one Docker Compose stack: the frontend, the API, the LLM gateway, and the Supabase distribution. Agent sessions run on a separate sandbox provider, not on this stack, so compute scales off the box. The box must stay reachable so the sandbox can call back to the API. The default provider is Daytona; Platinum and E2B are also supported.

## Updates and scale

Every instance updates itself. Pin an exact version with `kortix self-host update --tag <version>`, or turn the updater off with `--auto-update off`. Each API container has a 640 MiB memory limit by default; raise it on a 16 GiB host with `kortix self-host env set KORTIX_API_MEMORY_LIMIT=1024m` when API traffic reaches the default.

## Backups

Kortix has no separate backup system. Each instance stores its data under `~/.config/kortix/self-host/<instance>/`: `volumes/db/data` for the Postgres database and `volumes/storage` for file storage. The instance's `.env` holds every secret and signing key it uses. Back up all three before a destructive command.

The full command surface and the architecture notes are in the Kortix docs: [Read the docs](https://kortix.com/docs).
