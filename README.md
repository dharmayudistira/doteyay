# dotclaude

Portable, agent-neutral coding instructions. `AGENTS.md` is the single source of truth for shared behavioral rules. The repo name is historical; the rules are not Claude-specific.

## Set up a new device

Clone this repo, open it in an AI coding agent with local file access, and send this prompt:

> Read `SETUP.md` and guide me through setting up the shared instructions on this device. Detect installed agents, show me the proposed changes, and ask before writing anything.

`SETUP.md` is an interactive prompt, not a script. The agent will inspect installed tools and their instruction paths, then ask which agents or profiles to configure and how to handle existing files. Nothing is installed simply by opening this repo. You can also send `/setup` if your agent passes that text to the model; slash commands are tool-specific, so the prompt above is the portable entry point.

Keep this clone at a stable path if you approve symlinks to `AGENTS.md`. Agent-specific settings, credentials, hooks, skills, and MCP servers are outside this setup. Configure those separately and never commit secrets here.

## Instruction layers

`AGENTS.md` in this repo contains personal defaults that apply across projects. A separate project's `AGENTS.md` should contain only that project's architecture, commands, and conventions. For Claude Code in a project, a `CLAUDE.md` symlink to that project's `AGENTS.md` lets both agents read the same project rules.

This repo's `CLAUDE.md` is only a Claude Code adapter that points back to the shared file. An agent may see the shared rules twice when editing this repo, once globally and once from the repo. Other projects receive only the global copy plus their own project rules.

The four-point structure is adapted from Andrej Karpathy's CLAUDE.md: think before coding, simplicity first, surgical changes, then goal-driven execution.

## Author

[Dharma Yudistira](https://dharma-yudistira.com), Frontend and Flutter Engineer based in Sidoarjo, Indonesia.
