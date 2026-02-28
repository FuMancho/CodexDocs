# CLI Reference

Complete command-line options and flags for the Codex terminal client. See [CLI Features](./features.md) for usage details.

## Global Flags

| Flag | Values | Description |
|---|---|---|
| `--add-dir` | `path` | Grant additional directories write access |
| `--ask-for-approval`, `-a` | `untrusted`, `on-request`, `never` | Control when Codex pauses for approval |
| `--cd`, `-C` | `path` | Set the working directory |
| `--config`, `-c` | `key=value` | Override configuration values |
| `--yolo` | — | Skip all approvals and sandboxing |
| `--disable` | `feature` | Force-disable a feature flag |
| `--enable` | `feature` | Force-enable a feature flag |
| `--full-auto` | — | Shortcut for `on-request` approval + `workspace-write` sandbox |
| `--image`, `-i` | `path[,path...]` | Attach image files to the prompt |
| `--model`, `-m` | `string` | Override the configured model |
| `--no-alt-screen` | — | Disable alternate screen mode for the TUI |
| `--oss` | — | Use local open source model provider (Ollama) |
| `--profile`, `-p` | `string` | Load a config profile from `config.toml` |
| `--sandbox`, `-s` | `read-only`, `workspace-write`, `danger-full-access` | Sandbox policy for shell commands |
| `--search` | — | Enable live web search |
| `PROMPT` | `string` | Optional initial prompt text |

> [!WARNING]
> The `--yolo` flag disables all safety checks. Only use inside an externally hardened environment.

## Commands

| Command | Description |
|---|---|
| `codex` | Start interactive TUI session |
| `codex "prompt"` | Start with an initial prompt |
| `codex exec "prompt"` | Non-interactive execution |
| `codex exec --json` | Non-interactive with JSON output |
| `codex resume` | Resume a previous session |
| `codex resume --last` | Resume the most recent session |
| `codex features list` | List feature flags |
| `codex features enable <flag>` | Enable a feature flag |
| `codex features disable <flag>` | Disable a feature flag |
| `codex login` | Authenticate |
| `codex logout` | Log out |
| `codex mcp` | Manage MCP servers |
| `codex mcp-server` | Run Codex as an MCP server |
| `codex app-server` | Start the app server |
| `codex sandbox` | Manage sandbox settings |
| `codex completion` | Shell completion setup |
| `codex cloud` | Launch Codex Cloud tasks |
| `codex apply` | Apply a patch file |
| `codex fork` | Fork a session to a new ID |

## Slash Commands (Interactive)

| Command | Description |
|---|---|
| `/model` | Switch models or adjust reasoning |
| `/review` | Open code review presets |
| `/theme` | Preview and select a visual theme |
| `/exit` | Close the interactive session |
| `/status` | Show current session info |

## Configuration

Codex CLI reads defaults from `~/.codex/config.toml`. CLI flags override config values for the current invocation. See:

- [Config Basics](https://developers.openai.com/codex/config-basic) — Configuration precedence and structure
- [Advanced Config](https://developers.openai.com/codex/config-advanced) — Complex configurations
- [Config Reference](https://developers.openai.com/codex/config-reference) — All configuration keys
- [Sample Config](https://developers.openai.com/codex/config-sample) — Example `config.toml`
- [AGENTS.md](https://developers.openai.com/codex/guides/agents-md) — Project-level identity and instructions
- [Rules](https://developers.openai.com/codex/rules) — Rule definitions for Codex behavior

## See Also

- [CLI Features](./features.md)
- [Security](https://developers.openai.com/codex/security)
- [MCP](https://developers.openai.com/codex/mcp)
- [Multi-Agent](https://developers.openai.com/codex/multi-agent)
