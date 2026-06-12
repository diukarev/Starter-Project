# Welcome to Conductor

This is the starter project for Conductor, a macOS app for running multiple coding agents in parallel in isolated git worktree workspaces.

The app is intentionally tiny: one dependency-free `index.html` file plus a few static assets in `public/`. There is no install step, build step, package manager, framework, or dev server.

## How Conductor Uses This Project

Conductor creates each workspace as its own git worktree and branch. The checked-in `.conductor/settings.toml` tells Conductor how to prepare and run this starter app:

```toml
"$schema" = "https://conductor.build/schemas/settings.repo.schema.json"

[scripts]
setup = "true"
run = "open index.html"
```

When you create a workspace, setup succeeds immediately. When you click Run on macOS, Conductor opens the HTML file in your default browser.

## Local Development

Open the app directly:

```sh
open index.html
```

Edit `index.html`, then refresh the browser.

## Project Structure

- `index.html` contains the UI, styling, and interaction logic.
- `public/` contains static assets used by the page.
- `.conductor/settings.toml` contains the shared Conductor workspace scripts.
- `.claude/commands/` contains project slash commands available in every workspace.
- `.context/` is available in Conductor workspaces for gitignored notes and handoff files between agents.

## Remote control

Run `/remote-control` in any workspace to make the session reachable from another
device. It pushes your branch and surfaces a pull request link you can follow from
your phone, then leave steering notes as PR comments. Native Conductor pairing for
Claude Code's built-in remote control is tracked in
[conductor-releases#19](https://github.com/meltylabs/conductor-releases/issues/19).

## Learn More

- [Conductor docs](https://conductor.build/docs)
