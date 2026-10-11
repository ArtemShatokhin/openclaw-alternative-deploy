# Setup: run open-source Kortix from this template

Kortix is open source, and this page takes the deployment template in this repo from a bare host to a running project with its first reviewed change. Agents, skills, memory and connector rules are files in the repo, so setup is a clone, a manifest and a stack to start.

## 1. Clone the repo

```bash
git clone https://github.com/ArtemShatokhin/openclaw-alternative-deploy.git
cd openclaw-alternative-deploy
```

The repo holds `kortix.yaml` (the Kortix layer), `agents/researcher.md` (a starter agent) and `skills/weekly-digest/SKILL.md` (a starter skill). `kortix.yaml` declares the machine image, the connectors and the triggers, and secret names and grants. Secret values never appear in the repo.

## 2. Run the stack

Kortix runs as one Docker Compose stack. Install the CLI, point DNS at the box, then initialize, start and configure it:

```bash
curl -fsSL https://kortix.com/install | bash
kortix self-host init --domain kortix.example.com
kortix self-host start
kortix self-host configure
```

`kortix self-host status`, `kortix self-host logs` and `kortix self-host doctor` report what is happening while the stack comes up. `configure` prompts for the sandbox provider key. The `docker-compose.yml` in this repo layers your team's settings onto the stack the CLI prepares.

## 3. Connect a model and a repo

Open your domain in a browser and sign up with the admin email. Connect GitHub at Settings → Git, then connect your own model key in the model picker. Any model provider with your own keys. Or the ChatGPT plan you already pay for. Or sign in with your OpenCode Console account for OpenCode Zen and Go.

## 4. Start a session and read the change request

```bash
kortix sessions new --prompt "Summarize this week's commits and open a change request"
kortix cr ls
```

The session works on its own sandbox and its own branch. Session work reaches `main` through a change request, and merge is default-deny for agents, so you read the diff before it lands.

## If something fails

The instance keeps its data under `~/.config/kortix/self-host/<instance>/`. Back up `volumes/db/data`, `volumes/storage` and the instance `.env` before you change the stack, then rerun `kortix self-host start`. The full command surface is in the Kortix docs, and [self-hosting](self-hosting.md) covers the prerequisites in more detail.
