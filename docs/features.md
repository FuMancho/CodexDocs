# Codex CLI Features

Overview of the core features available in the Codex terminal client.

## Interactive Mode

Launch a full-screen terminal UI that can read your repository, make edits, and run commands:

```bash
codex
codex "Explain this codebase to me"
```

In interactive mode you can:

- Send prompts, code snippets, or screenshots.
- Watch Codex explain its plan before making changes.
- Approve or reject steps inline.
- Press `Ctrl+C` or use `/exit` to close the session.

## Resuming Conversations

Codex stores transcripts locally so you can pick up where you left off:

```bash
codex resume                    # Pick from recent sessions
codex resume --all              # Show all sessions (any cwd)
codex resume --last             # Jump to most recent session
codex resume <SESSION_ID>       # Resume a specific run
```

Non-interactive runs can resume too:

```bash
codex exec resume --last "Fix the race conditions you found"
```

## Models & Reasoning

The default model for coding tasks is `gpt-5.3-codex`. Switch models mid-session:

```text
/model
```

For extra fast tasks, ChatGPT Pro subscribers have access to the `GPT-5.3-Codex-Spark` model in research preview.

Or from the command line:

```bash
codex --model gpt-5.3-codex
```

See [Models](https://developers.openai.com/codex/models) for details.

## Approval Modes

Control when Codex pauses for human approval:

| Mode | Behavior |
|---|---|
| `untrusted` | Pause for each action |
| `on-request` | Pause only when Codex requests it |
| `never` | Execute without pausing |

```bash
codex --ask-for-approval on-request
codex --full-auto                      # Shortcut: on-request + workspace-write sandbox
codex --yolo                           # No approvals, no sandbox (use cautiously)
```

## Multi-Agent Mode (Experimental)

Parallelize larger tasks with multiple Codex agents. Configure roles via `[agents]` in `config.toml`. See [Multi-Agents](https://developers.openai.com/codex/multi-agent).

## Image Inputs

Attach screenshots or design specs:

```bash
codex -i screenshot.png "Explain this error"
codex --image img1.png,img2.jpg "Summarize these diagrams"
```

## Code Review

Use `/review` in the CLI to open built-in review presets:

- **Review against a base branch** — Highlights risks before opening a PR by finding the merge base against its upstream.
- **Review uncommitted changes** — Inspect staged, not staged, or not tracked files.
- **Review a commit** — Analyze a specific SHA.
- **Custom review instructions** — Supply your own instructions (e.g., "Focus on accessibility").

## Web Search

Codex includes a built-in web search tool. For local tasks in the Codex CLI, Codex enables web search by default and serves results from a web search cache. The cache is an OpenAI-maintained index of web results, so cached mode returns pre-indexed results instead of fetching live pages. Defaults to cached results for safety. Enable live results:

```bash
codex --search
```

Or set in config:

```toml
web_search = "live"       # or "cached" (default), "disabled"
```

## Scripting & Automation

Run Codex non-interactively for CI/CD and scripting:

```bash
codex exec "Write tests for auth.py"
codex exec --json "Analyze this codebase" > report.json
```

## Feature Flags

Codex includes a small set of feature flags like `unified_exec` and `shell_snapshot`.

```bash
codex features list
codex features enable <feature>
codex features disable <feature>
```

Feature settings persist in `~/.codex/config.toml`.

## Themes

Use `/theme` to preview and select a visual theme, or add custom `.tmTheme` files under `$CODEX_HOME/themes`.

## Slash Commands

Slash commands give you quick access to specialized workflows like `/review`, `/fork`, or your own reusable prompts. Codex ships with a curated set of built-ins, and you can create custom ones for team-specific tasks or personal shortcuts.

See the [Slash Commands Guide](https://developers.openai.com/codex/guides/slash-commands) to browse the catalog of built-ins, learn how to author custom commands, and understand where they live on disk.

## Prompt Editor

When you’re drafting a longer prompt, it can be easier to switch to a full editor and then send the result back to the composer.

In the prompt input, press `Ctrl+G` to open the editor defined by the `VISUAL` environment variable (or `EDITOR` if `VISUAL` isn’t set).

## Model Context Protocol (MCP)

Connect Codex to more tools by configuring Model Context Protocol servers. Add STDIO or streaming HTTP servers in `~/.codex/config.toml`, or manage them with the `codex mcp` CLI commands—Codex launches them automatically when a session starts and exposes their tools next to the built-ins. You can even run Codex itself as an MCP server when you need it inside another agent.

See [Model Context Protocol](https://developers.openai.com/codex/mcp) for example configurations, supported auth flows, and a more detailed guide.

## Working with Codex cloud

The `codex cloud` command lets you triage and launch [Codex cloud tasks](https://developers.openai.com/codex/cloud) without leaving the terminal. Run it with no arguments to open an interactive picker, browse active or finished tasks, and apply the changes to your local project.

You can also start a task directly from the terminal:

```bash
codex cloud exec --env ENV_ID "Summarize open bugs"
```

Add `--attempts` (1–4) to request best-of-N runs when you want Codex cloud to generate more than one solution.

## See Also

- [CLI Reference](./commands.md)
- [Configuration](https://developers.openai.com/codex/config-basic)
- [Security](https://developers.openai.com/codex/security)
