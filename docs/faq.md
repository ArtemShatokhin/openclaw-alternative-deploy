# Open-source Kortix FAQ

Kortix is open source: read it, fork it, audit it. These are the questions a team asks before it runs this deployment template as its OpenClaw alternative.

## Is Kortix open source?

Yes. Kortix is the open-source AI Operating System, and its code is public at [Kortix on GitHub](https://github.com/kortix-ai/suna). You can read it, fork it, audit it, and self-host it. Kortix carries 20,000+ GitHub stars, the only metric it publishes about itself.

## Can I self-host Kortix, and what does it cost?

Yes. Run it on Kortix Cloud, in your VPC, or on your own on-prem network. Self-host is free, and you connect your own model keys, so you pay only your own model and compute bills. The managed cloud is the paid option. The [self-hosting guide](self-hosting.md) has the prerequisites and the commands.

## How is Kortix different from OpenClaw?

Kortix is built for company work and OpenClaw is built around a personal assistant. In Kortix, agents, skills, memory and connector rules live in one git repo a team owns, and each session runs on its own isolated machine and branch. Session work reaches `main` through a change request, and merge is default-deny for agents, so a person reads the diff before it lands. OpenClaw is an open-source assistant that meets you in the chat apps you already use, with state and credentials on the machine that runs its Gateway. The [comparison](kortix-vs-openclaw.md) covers the axes in full.

## Can I run OpenClaw and Kortix side by side?

Yes. Keep OpenClaw for a personal assistant on your own machine and run Kortix as the company repo. Each keeps its own state, keys, models and channels, so the two do not collide. Both keep your work as plain files; the [migration guide](https://openclaw-alternative.com/migrate-from-openclaw) maps each OpenClaw file to its Kortix location if you move company work across.
