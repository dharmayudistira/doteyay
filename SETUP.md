# Interactive setup prompt

Follow this workflow only when the user explicitly asks to set up this repository's instructions. `AGENTS.md` is the source of truth for the shared rules. Do not execute a script or change global configuration just because this file was opened.

## 1. Discover, read-only

- Identify the AI coding agent currently running and other agents installed on this device. Use narrow, read-only checks such as available commands, application locations, and environment variables. A leftover config directory alone does not prove an agent is installed. Do not read credential contents or scan the whole home directory.
- For each detected agent, search its current official documentation for how to configure global instructions, including supported paths, overrides, and whether it can use a symlink to `AGENTS.md`. If the documentation is unavailable or unclear, ask the user rather than guessing.
- Inspect only the prospective instruction targets and any higher-priority override files. Record whether each target is absent, a file, or a symlink, and whether existing instructions conflict with `AGENTS.md`.

## 2. Ask before changing anything

- Show the detected agents, exact target paths, existing-file status, and proposed action for each. Ask which agents or profiles the user wants configured. Do not treat detection as permission to configure all of them.
- Explain whether each target would link to `AGENTS.md`, import it, or receive a copy. Prefer a link when the agent supports it and the clone will stay at a stable path. Explain that a copy will need manual resync after edits.
- Require explicit confirmation before creating directories, links, or files. If a target already exists, ask whether to skip, merge, or replace it. Never silently overwrite, delete, rename, or redirect an existing file or link. Before an approved replacement, preserve a recoverable backup and confirm any conflicting rules with the user.
- If the agent's instruction mechanism or a user choice remains uncertain, pause and ask a concise question. Do not assume an answer from silence.

## 3. Apply only the approved plan

- Change only the approved instruction targets. Do not install agents or tools, change models, permissions, hooks, MCP servers, authentication, or other settings unless the user separately requests them.
- Keep `AGENTS.md` as the only editable source for shared rules. Use an agent-specific adapter only when its instruction loader requires one.
- If an approved action fails, stop for that target, explain the cause, and ask before trying a different method.

## 4. Verify and report

- Check every created link or file and, when feasible, confirm the agent loads the shared rules with a safe, read-only check. Ask before a live test that may use network access, incur cost, or trigger hooks.
- Report configured, skipped, and unresolved agents; exact paths changed; any backups; and what the user must do to keep copied instructions in sync.
