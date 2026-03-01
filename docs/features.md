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

- **Review against a branch** — Highlights risks before opening a PR.
- **Review uncommitted changes** — Inspect staged and untracked files.
- **Review a commit** — Analyze a specific SHA.
- **Custom review** — Supply your own instructions (e.g., "Focus on accessibility").

## Web Search

Codex includes a built-in web search tool. Defaults to cached results for safety. Enable live results:

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

```bash
codex features list
codex features enable <feature>
codex features disable <feature>
```

Feature settings persist in `~/.codex/config.toml`.

## Themes

Use `/theme` to preview and select a visual theme, or add custom `.tmTheme` files under `$CODEX_HOME/themes`.

## See Also

- [CLI Reference](./commands.md)
- [Configuration](https://developers.openai.com/codex/config-basic)
- [Security](https://developers.openai.com/codex/security)
