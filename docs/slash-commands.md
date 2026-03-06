# Slash Commands

Slash commands give you quick access to specialized workflows like `/review`, `/fork`, or your own reusable prompts. Codex ships with a curated set of built-ins, and you can create custom ones for team-specific tasks or personal shortcuts.

## Interactive Slash Commands

| Command | Description |
|---|---|
| `/agent` | Switch the active agent thread |
| `/apps` | Browse apps (connectors) and insert them into your prompt |
| `/clear` | Clear the terminal and start a new chat in the same session |
| `/compact` | Summarize the visible conversation to free tokens |
| `/copy` | Copy the latest response to your clipboard |
| `/debug-config` | Print config layer and requirements diagnostics |
| `/diff` | Show the Git diff |
| `/exit` | Exit the CLI (same as /quit) |
| `/experimental` | Toggle experimental features |
| `/feedback` | Send logs to the Codex maintainers |
| `/fork` | Fork the current conversation into a new thread |
| `/init` | Generate an AGENTS.md scaffold |
| `/logout` | Sign out of Codex |
| `/mcp` | List configured Model Context Protocol (MCP) tools |
| `/mention` | Attach a file to the conversation |
| `/model` | Switch models or adjust reasoning |
| `/new` | Start a new conversation inside the same CLI session |
| `/permissions` | Set what Codex can do without asking first |
| `/personality` | Choose a communication style for responses |
| `/plan` | Switch to plan mode and optionally send a prompt |
| `/ps` | Show experimental background terminals and their recent output |
| `/quit` | Exit the CLI |
| `/resume` | Resume a saved conversation from your session list |
| `/review` | Open code review presets |
| `/sandbox-add-read-dir` | Grant sandbox read access to an extra directory (Windows only) |
| `/status` | Display session configuration and token usage |
| `/statusline` | Configure TUI status-line fields interactively |
| `/theme` | Preview and select a visual theme |

## Control your session

The following workflows keep your session on track without restarting Codex.

### Set the active model with `/model`

1. Start Codex and open the composer.
2. Type `/model` and press Enter.
3. Choose a model such as `gpt-5.4` or `gpt-5.3-codex` from the popup.

**Expected:** Codex confirms the new model in the transcript. Run `/status` to verify the change.

### Set a communication style with `/personality`

Use `/personality` to change how Codex communicates without rewriting your prompt.

1. In an active conversation, type `/personality` and press Enter.
2. Choose a style from the popup.

**Expected:** Codex confirms the new style in the transcript and uses it for later responses in the thread.

Codex supports `friendly`, `pragmatic`, and `none` personalities. Use `none` to disable personality instructions.

### Switch to plan mode with `/plan`

1. Type `/plan` and press Enter to switch the active conversation into plan mode.
2. Optional: provide inline prompt text (for example, `/plan Propose a migration plan for this service`).

**Expected:** Codex enters plan mode and uses your optional inline prompt as the first planning request.

### Toggle experimental features with `/experimental`

1. Type `/experimental` and press Enter.
2. Toggle the features you want (for example, Multi-agents), then restart Codex.

**Expected:** Codex saves your feature choices to config and applies them on restart.

### Clear the terminal and start a new chat with `/clear`

1. Type `/clear` and press Enter.

**Expected:** Codex clears the terminal, resets the visible transcript, and starts a fresh chat in the same CLI session.

### Update permissions with `/permissions`

1. Type `/permissions` and press Enter.
2. Select the approval preset that matches your comfort level, for example `Auto` for hands-off runs or `Read Only` to review edits.

**Expected:** Codex announces the updated policy. Future actions respect the updated approval mode until you change it again.

### Copy the latest response with `/copy`

1. Type `/copy` and press Enter.

**Expected:** Codex copies the latest completed Codex output to your clipboard.

### Grant sandbox read access with `/sandbox-add-read-dir`

This command is available only when running the CLI natively on Windows.

1. Type `/sandbox-add-read-dir C:\absolute\directory\path` and press Enter.
2. Confirm the path is an existing absolute directory.

**Expected:** Codex refreshes the Windows sandbox policy and grants read access to that directory for later commands that run in the sandbox.

### Inspect the session with `/status`

1. In any conversation, type `/status`.
2. Review the output for the active model, approval policy, writable roots, and current token usage.

**Expected:** You see a summary like what `codex status` prints in the shell, confirming Codex is operating where you expect.

### Inspect config layers with `/debug-config`

1. Type `/debug-config`.
2. Review the output for config layer order (lowest precedence first), on/off state, and policy sources.

**Expected:** Codex prints layer diagnostics plus policy details such as `allowed_approval_policies`, `allowed_sandbox_modes`, `mcp_servers`, `rules`, `enforce_residency`, and `experimental_network` when configured.

### Configure footer items with `/statusline`

1. Type `/statusline`.
2. Use the picker to toggle and reorder items, then confirm.

**Expected:** The footer status line updates immediately and persists to `tui.status_line` in `config.toml`.

Available status-line items include model, model+reasoning, context stats, rate limits, git branch, token counters, session id, current directory/project root, and Codex version.

### Check background terminals with `/ps`

1. Type `/ps`.
2. Review the list of background terminals and their status.

**Expected:** Codex shows each background terminal’s command plus up to three recent, non-empty output lines so you can gauge progress at a glance.

### Keep transcripts lean with `/compact`

1. After a long exchange, type `/compact`.
2. Confirm when Codex offers to summarize the conversation so far.

**Expected:** Codex replaces earlier turns with a concise summary, freeing context while keeping critical details.

### Review changes with `/diff`

1. Type `/diff` to inspect the Git diff.
2. Scroll through the output inside the CLI to review edits and added files.

**Expected:** Codex shows changes you’ve staged, changes you haven’t staged yet, and files Git hasn’t started tracking, so you can decide what to keep.

### Highlight files with `/mention`

1. Type `/mention` followed by a path, for example `/mention src/lib/api.ts`.
2. Select the matching result from the popup.

**Expected:** Codex adds the file to the conversation, ensuring follow-up turns reference it directly.

### Start a new conversation with `/new`

1. Type `/new` and press Enter.

**Expected:** Codex starts a fresh conversation in the same CLI session, so you can switch tasks without leaving your terminal.

### Resume a saved conversation with `/resume`

1. Type `/resume` and press Enter.
2. Choose the session you want from the saved-session picker.

**Expected:** Codex reloads the selected conversation’s transcript so you can pick up where you left off, keeping the original history intact.

### Fork the current conversation with `/fork`

1. Type `/fork` and press Enter.

**Expected:** Codex clones the current conversation into a new thread with a fresh ID, leaving the original transcript untouched so you can explore an alternative approach in parallel.

### Generate AGENTS.md with `/init`

1. Run `/init` in the directory where you want Codex to look for persistent instructions.
2. Review the generated AGENTS.md, then edit it to match your repository conventions.

**Expected:** Codex creates an AGENTS.md scaffold you can refine and commit for future sessions.

### Ask for a working tree review with `/review`

1. Type `/review`.
2. Follow up with `/diff` if you want to inspect the exact file changes.

**Expected:** Codex summarizes issues it finds in your working tree, focusing on behavior changes and missing tests.

### List MCP tools with `/mcp`

1. Type `/mcp`.
2. Review the list to confirm which MCP servers and tools are available.

**Expected:** You see the configured Model Context Protocol (MCP) tools Codex can call in this session.

### Browse apps with `/apps`

1. Type `/apps`.
2. Pick an app from the list.

**Expected:** Codex inserts the app mention into the composer as `$app-slug`, so you can immediately ask Codex to use it.

### Switch agent threads with `/agent`

1. Type `/agent` and press Enter.
2. Select the thread you want from the picker.

**Expected:** Codex switches the active thread so you can inspect or continue that agent’s work.

### Send feedback with `/feedback`

1. Type `/feedback` and press Enter.
2. Follow the prompts to include logs or diagnostics.

**Expected:** Codex collects the requested diagnostics and submits them to the maintainers.

### Sign out with `/logout`

1. Type `/logout` and press Enter.

**Expected:** Codex clears local credentials for the current user session.

### Exit the CLI with `/quit` or `/exit`

1. Type `/quit` (or `/exit`) and press Enter.

**Expected:** Codex exits immediately. Save or commit any important work first.
