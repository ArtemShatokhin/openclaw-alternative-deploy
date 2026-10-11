---
name: weekly-digest
description: Turns a week of project activity on open-source Kortix into a digest file and a change request.
---

# Weekly digest for open-source Kortix

Use this skill when an agent is asked for a weekly summary of project activity on open-source Kortix.

1. Collect the week's sessions, change requests and notable commits from the project repo.
2. Write the digest to `memory/digests/<YYYY-MM-DD>.md`, with one section per workstream and a link to each source.
3. Keep every figure tied to the commit or change request it came from. Leave out anything you cannot source.
4. Commit the digest to your session branch and open a change request.

A person reads the digest in the change request before it lands.
