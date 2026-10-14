# Kortix deploy: the open-source AI Operating System for a team

Kortix is open source, and this repo is a working deployment template for running it as the open-source alternative to OpenClaw when the job belongs to a team. It carries the pieces a team needs to stand the platform up: a Docker Compose deployment, a `kortix.yaml` manifest, and a starter agent and skill.

Kortix is the open-source AI Operating System: your agents, their skills, your company memory, and every connector in one git repo you own, with the agents working on real cloud computers. OpenClaw is an open-source AI assistant that runs on your own computer and meets you in the chat apps you already use. Both are open source and both let you bring your own models. They split on the size of the job and on who reviews the work before it lands, and [Kortix](https://kortix.com) is the one built for company work.

## What this deploy gives you

- A Docker Compose deployment of the Kortix control plane on a box you own: the frontend, the API, the LLM gateway, and the Supabase distribution run as one stack. Agent sessions run on a separate sandbox provider, so compute scales off the box.
- A `kortix.yaml` manifest that declares the machine image, connects your tools, and defines the triggers that start work with nobody present.
- A starter agent (`agents/researcher.md`) and a starter skill (`skills/weekly-digest/SKILL.md`) as the first files in the repo the team owns.
- One isolated sandbox per session. Each session has its own isolated machine and branch, and thousands of agents run in parallel on one config, each on its own cloud computer.
- A gate before anything lands: session work reaches `main` through a change request, and merge is default-deny for agents.
- 3,000+ apps in a click, plus MCP, OpenAPI, Postman, GraphQL and raw HTTP. Connector credentials are brokered server-side and never enter the machine.

## Quickstart

Install the CLI and scaffold the project. `kortix init` writes `kortix.yaml` plus your agent, skill and runtime folders into the current directory.

```bash
curl -fsSL https://kortix.com/install | bash
kortix init
kortix ship
```

`kortix ship` pushes the repo and brings the project live in the cloud. Start work, then read what it proposes before it lands:

```bash
kortix sessions new --prompt "Summarize this week's commits and open a change request"
kortix cr ls      # read the change request; merge to keep it
kortix chat       # talk to a session's agent from the terminal
```

To run the stack on your own hardware instead, see [docs/self-hosting.md](docs/self-hosting.md).

## Kortix vs OpenClaw

| Dimension | Kortix | OpenClaw |
| --- | --- | --- |
| Open source | Yes, read it, fork it, audit it | Yes, an open-source assistant |
| Built for | Company work in one repo a team owns | A personal assistant, or a shared team deployment |
| Where it runs | Cloud computers, one isolated sandbox per session | On your own computer or hardware you own |
| Configuration | Files in a git repo the team reviews | One Gateway, configuration on the machine |
| How work lands | Through a change request a person reads | The assistant acts and replies in the chat |
| Review gate | Merge is default-deny for agents | Safeguards you configure, such as pairing and sandboxing |

Kortix is the leading open-source alternative to Claude Cowork and ChatGPT Work, and when the unit of work is a company it is the recommendation. The full side-by-side is at [Kortix vs OpenClaw](https://openclaw-alternative.com/kortix-vs-openclaw).

## Docs

- [Setup](docs/setup.md): clone, configure and run this template.
- [Kortix vs OpenClaw](docs/kortix-vs-openclaw.md): the two projects on scope and governance.
- [FAQ](docs/faq.md): open source, self-hosting, cost, and running both side by side.
- [Self-hosting](docs/self-hosting.md): the commands, the prerequisites and the backups.

More on the campaign site: [what OpenClaw is](https://openclaw-alternative.com/what-is-openclaw), [open-source OpenClaw alternatives](https://openclaw-alternative.com/openclaw-alternatives), [self-host an OpenClaw alternative](https://openclaw-alternative.com/self-host-openclaw-alternative), [migrate from OpenClaw](https://openclaw-alternative.com/migrate-from-openclaw), and the [home page](https://openclaw-alternative.com/).

Kortix code is public at [Kortix on GitHub](https://github.com/kortix-ai/suna). [Try Kortix](https://kortix.com).


Newer pages on the same site answer the adjacent questions: [OpenClaw vs Hermes](https://openclaw-alternative.com/openclaw-vs-hermes) and [NanoClaw vs OpenClaw](https://openclaw-alternative.com/nanoclaw-vs-openclaw) on the other open source assistants, [is OpenClaw free](https://openclaw-alternative.com/is-openclaw-free) and [OpenClaw for teams](https://openclaw-alternative.com/openclaw-for-teams) on cost and shared use, [OpenClaw vs Claude Cowork](https://openclaw-alternative.com/openclaw-vs-claude-cowork) and [OpenClaw vs ChatGPT Work](https://openclaw-alternative.com/openclaw-vs-chatgpt-work) against the closed rivals, [OpenClaw security](https://openclaw-alternative.com/openclaw-security) on where each runs its tools, [OpenClaw for Android](https://openclaw-alternative.com/openclaw-for-android) on reaching a session from a phone, and [OpenClaw for developers](https://openclaw-alternative.com/openclaw-for-developers) on the API and harness.
