# OpenAI Codex CLI Changelog

> Curated changelog sourced from the [official Codex changelog](https://developers.openai.com/codex/changelog).
> Last updated: 2026-04-30

## Codex CLI 0.128.0 (2026-04-30)

### New Features
- Added persisted /goal workflows with app-server APIs, model tools, runtime continuation, and TUI controls for create, pause, resume, and clear. (#18073)
- Added codex update, configurable TUI keymaps, plan-mode nudges, action-required terminal titles, and active-turn /statusline and /title edits. (#19933)
- Expanded permission profiles with built-in defaults, sandbox CLI profile selection, cwd controls, and active-profile metadata for clients. (#19900)
- Improved plugin workflows with marketplace installation, remote bundle caching, remote uninstall, plugin-bundled hooks, hook enablement state, and external-agent config import. (#18704)
- Added external agent session import, including background imports and imported-session title handling. (#19895)
- Made MultiAgentV2 configuration more explicit with thread caps, wait-time controls, root/subagent hints, and v2-specific depth handling. (#19360)

### Bug Fixes
- Fixed several resume and interruption issues, including stale interrupt hangs, persisted provider restoration, large remote resume responses, and slow filtered resume lists. (#18392)
- Improved TUI reliability around terminal resize reflow, markdown list spacing, slash-command popup layout, keyboard cleanup, shell-mode escape, and working status updates. (#18575)

---

## Codex CLI 0.125.0 (2026-04-24)

### New Features
- App-server integrations now support Unix socket transport, pagination-friendly resume/fork, sticky environments, and remote thread config/store plumbing. (#18255)
- App-server plugin management can install remote plugins and upgrade configured marketplaces. (#18917)
- Permission profiles now round-trip across TUI sessions, user turns, MCP sandbox state, shell escalation, and app-server APIs. (#18284)

---

## Codex CLI 0.124.0 (2026-04-23)

### New Features
- The TUI now has quick reasoning controls: Alt+, lowers reasoning, Alt+. raises it, and accepted model upgrades now reset reasoning to the new model’s default instead of carrying over stale settings. (#18866)
- App-server sessions can now manage multiple environments and choose an environment and working directory per turn, which makes multi-workspace and remote setups easier to target precisely. (#18401)
- Added first-class Amazon Bedrock support for OpenAI-compatible providers, including AWS SigV4 signing and AWS credential-based auth. (#17820)
- Remote plugin marketplaces can now be listed and read directly, with more reliable detail lookups and larger result pages. (#18452)
- Hooks are now stable, can be configured inline in config.toml and managed requirements.toml, and can observe MCP tools as well as apply_patch and long-running Bash sessions. (#18893)

---

## Codex CLI 0.123.0 (2026-04-23)

### New Features
- Added a built-in amazon-bedrock model provider with configurable AWS profile support.
- Added /mcp verbose for full MCP server diagnostics, resources, and resource templates while keeping plain /mcp fast.
- Made plugin MCP loading accept both mcpServers and top-level server maps in .mcp.json.

---

## Codex CLI 0.122.0 (2026-04-20)

### New Features
- Standalone installs are more self-contained, and codex app now opens or installs Desktop correctly on Windows and Intel Macs.
- The TUI can open /side conversations for quick side questions, and queued input now supports slash commands and ! shell prompts while work is running.
- Plan Mode can start implementation in a fresh context, with context-usage shown before deciding whether to carry the planning thread forward.
- Plugin workflows now include tabbed browsing, inline enable/disable toggles, marketplace removal, and remote, cross-repo, or local marketplace sources.
- Filesystem permissions now support deny-read glob policies, managed deny-read requirements, platform sandbox enforcement, and isolated codex exec runs that ignore user config or rules.
- Tool discovery and image generation are now enabled by default, with higher-detail image handling and original-detail metadata support for MCP and js_repl image outputs.

---

## Codex CLI 0.121.0 (2026-04-15)

### New Features
- Added codex marketplace add and app-server support for installing plugin marketplaces from GitHub, git URLs, local directories, and direct marketplace.json URLs.
- Added TUI prompt history improvements, including Ctrl+R reverse search and local recall for accepted slash commands.
- Added TUI and app-server controls for memory mode, memory reset/deletion, and memory-extension cleanup.
- Expanded MCP/plugin support with MCP Apps tool calls, namespaced MCP registration, parallel-call opt-in, and sandbox-state metadata for MCP servers.
- Added realtime and app-server APIs for output modality, transcript completion events, raw turn item injection, and symlink-aware filesystem metadata.
- Added a secure devcontainer profile with bubblewrap support, plus macOS sandbox allowlists for Unix sockets.

---

## Codex CLI 0.120.0 (2026-04-11)

### New Features
- Realtime V2 can now stream background agent progress while work is still running and queue follow-up responses until the active response completes
- Hook activity in the TUI is easier to scan, with live running hooks shown separately and completed hook output kept only when useful
- Custom TUI status lines can include the renamed thread title
- Code-mode tool declarations now include MCP outputSchema details so structured tool results are typed more precisely
- SessionStart hooks can distinguish sessions created by /clear from fresh startup or resume sessions

---

## Codex CLI 0.119.0 (2026-04-10)

### New Features
- Realtime voice sessions now default to the v2 WebRTC path, with configurable transport, voice selection, native TUI media support, and app-server coverage for the new flow.
- MCP Apps and custom MCP servers gained richer support, including resource reads, tool-call metadata, custom-server tool search, server-driven elicitations, file-parameter uploads, and more reliable plugin cache refreshes.
- Remote/app-server workflows now support egress websocket transport, remote --cd forwarding, runtime remote-control enablement, sandbox-aware filesystem APIs, and an experimental codex exec-server subcommand.
- The TUI can copy the latest agent response with Ctrl+O, including better clipboard behavior over SSH and across platforms.
- /resume can now jump directly to a session by ID or name from the TUI.
- TUI notifications are more configurable, including Warp OSC 9 support and an opt-in mode for notifications even while the terminal is focused.

---

## Codex CLI 0.118.0 (2026-03-31)

### New Features
- Windows sandbox runs can now enforce proxy-only networking with OS-level egress rules, instead of relying on environment variables alone.
- App-server clients can now start ChatGPT sign-in with a device code flow, which helps when browser callback login is unreliable or unavailable.
- codex exec now supports the prompt-plus-stdin workflow, so you can pipe input and still pass a separate prompt on the command line.
- Custom model providers can now fetch and refresh short-lived bearer tokens dynamically, instead of being limited to static credentials from config or environment variables.

---

## Codex CLI 0.117.0 (2026-03-26)

### New Features
- Plugins are now a first-class workflow: Codex can sync product-scoped plugins at startup, browse them in /plugins, and install or remove them with clearer auth/setup handling.
- Sub-agents now use readable path-based addresses like /root/agent_a, with structured inter-agent messaging and agent listing for multi-agent v2 workflows.
- The /title terminal-title picker now works in both the classic TUI and the app-server TUI, making parallel sessions easier to tell apart.
- App-server clients can now send ! shell commands, watch filesystem changes, and connect to remote websocket servers with bearer-token auth.
- Image workflows got smoother: view_image now returns image URLs for code mode, generated images are reopenable from the TUI, and image-generation history survives resume.
- Prompt history recall now works in the app-server TUI, including across sessions.

---

## Introducing GPT-5.4 in Codex (2026-03-05)

GPT-5.4 is now available in Codex as OpenAI’s most capable and efficient
frontier model for professional work.
It combines recent advances in reasoning, coding, and agentic workflows in one
model, and it’s the recommended choice for most Codex tasks.

## Codex CLI 0.111.0 (2026-03-05)

### New Features
- Fast mode is now enabled by default, and the TUI header shows whether the session is running in Fast or Standard mode. (#13450, #13446)
- js_repl can now dynamically import local .js and .mjs files, making it easier to reuse workspace scripts from the REPL. (#13437)
- Codex now tells the model which plugins are enabled at session start, improving discovery of installed MCPs, apps, and skills. (#13433)
- App-server v2 now exposes MCP elicitation as a structured request/response flow instead of raw events, which simplifies client integrations. (#13425)
- Expanded image workflow support for clients, including client-side handling of image-generation events and model metadata for image-capable web search. (#13512)

---

## Codex CLI 0.110.0 (2026-03-05)

### New Features
- Added a plugin system that can load skills, MCP entries, and app connectors from config or a local marketplace, with an install endpoint for enabling plugins from the app server. (#12864, #13333, #13401, #13422)
- Expanded the TUI multi-agent flow with approval prompts, /agent-based enablement, clearer prompts, ordinal nicknames, and role-labeled handoff context. (#12995, #13246, #13404, #13412, #13505)

---

## Codex CLI artifact-runtime-v2.4.0 (2026-03-05)

- Empty draft
- Full release on Github

---

## Codex App 26.304 (2026-03-04)

### Codex app for Windows
The Codex app is now available on Windows. The app gives you one interface for working across projects, running parallel agent threads, and reviewing results in one place. The Windows app includes the same core features as the rest of the Codex app.

---

## Codex App 26.303 (2026-03-03)

### New features
- Added a Worktrees setting to turn automatic cleanup of Codex-managed worktrees on or off.
- Added Handoff support for moving a thread between Local and Worktree.
- Added an explicit English option in the language menu.

### Performance improvements and bug fixes
- Improved GitHub and pull request workflows.
- Improved approval prompts and app connection sign-in flows.
- Additional performance improvements and bug fixes.

---

## Codex App 26.228 (2026-02-28)

### Performance improvements and bug fixes
- Fixed a regression where conversation and task views could stop updating while Codex was streaming a response.
- Additional performance improvements and bug fixes.

---

## Codex App 26.227 (2026-02-27)

### New features
- Added pull request status badges in task rows and PR buttons, including draft, open, merged, and closed states.
- Added a Worktrees setting to choose how many Codex-managed worktrees to keep before older ones are cleaned up.

### Performance improvements and bug fixes
- Improved scrolling and navigation in long conversations and code review, including fixes for thread jumpiness, sidebar jitter, and diff scrolling.
- Improved app startup reliability and keyboard zoom behavior.
- Additional performance improvements and bug fixes.

---

## Codex CLI 0.107.0 (2026-03-02)

### New Features
- **Fork into sub-agents**: Easily branch work without leaving the current conversation. (#12499)
- **Realtime voice improvements**: Pick microphone and speaker devices, persist choices, and better audio format for transcription. (#12849, #12850, #13030)
- **Multimodal tool output**: Custom tools can now return images and other structured content. (#12948)
- **Model availability metadata**: App server exposes richer metadata, with TUI tooltips for plan-gated models. (#12958, #12972, #13021)
- **Configurable memories**: New `codex debug clear-memories` command to reset saved memory state. (#12997, #12999, #13002, #13085)

### Bug Fixes
- Reconnecting with `thread/resume` restores pending approval and input requests. (#12560)
- `thread/start` no longer blocks unrelated app-server requests. (#13033)
- TUI diff rendering respects theme colors and displays more cleanly in low-color environments. (#13016, #13037)

## Codex CLI 0.106.0 (2026-02-26)

### New Features
- **Direct install script** for macOS/Linux published as GitHub release asset (#12740)
- **App-server v2 thread API**: Thread-scoped realtime endpoints and `thread/unsubscribe` flow (#12715, #10954)
- **js_repl promoted to /experimental** with startup compatibility checks and Node 22.22.0 minimum (#12712, #12824, #12857)
- **request_user_input in Default mode** — not just Plan mode (#12735)
- **GPT-5.3-Codex visible** in CLI model list for API users (#12808)
- **Memory improvements**: Diff-based forgetting and usage-aware memory selection (#12900, #12909)

### Bug Fixes
- WebSocket reliability: Retry timeout-related HTTP 400 handshake failures, prefer WS v2 (#12791, #12838)
- **zsh-fork sandbox bypass** fixed — shell execution path could drop sandbox wrappers (#12800)
- ~1M-character input size cap in TUI and app-server (#12823)
- TUI local file-link rendering — hide absolute paths, preserve line/column refs (#12705, #12870)
- Ctrl-C handling for sub-agents (#12911)

### Documentation
- Fixed stale sign-in success link (#12805)
- Clarified CLI login hint for remote/device-auth (#12813)

---

## Codex App 26.226 (2026-02-26)

### New Features
- MCP shortcuts in composer (install keyword suggestions, MCP server submenu in Add context)
- @mentions and skill mentions in inline review comments

### Fixes
- Improved MCP tool call rendering and Mermaid diagram error handling
- Fixed stopped terminal commands appearing as running

---

## Codex CLI 0.105.0

### Highlights
- Voice transcription support (#3381)
- `/clear` and `/copy` TUI commands (#12444, #12613)
- Theme-aware diff backgrounds (#12581)
- Agent jobs (spawn_agents_on_csv) with progress UI (#10935)
- Search term filtering in thread list (#12578)
- Pending child-thread approvals in TUI (#12767)

*See [full changelog](https://developers.openai.com/codex/changelog) for earlier versions.*
