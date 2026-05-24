# OpenAI Codex CLI Changelog

> Curated changelog sourced from the [official Codex changelog](https://developers.openai.com/codex/changelog).
> Last updated: 2026-05-14

## Work with Codex from anywhere (2026-05-14)

You can now use Codex from the ChatGPT mobile app by connecting it to a Mac running the Codex app. Codex runs from the connected host, so the same projects, files, credentials, plugins, skills, and configuration are available from your phone.

## Expanded Auto-review documentation (2026-05-11)

Added a dedicated Auto-review page covering the reviewer lifecycle, trigger conditions, failure behavior, and local or managed configuration.

## Codex CLI 0.130.0 (2026-05-08)

### New Features
- Plugin details now show bundled hooks, and plugin sharing exposes link metadata plus discoverability controls.
- Added `codex remote-control` as a simpler entrypoint for starting a headless, remotely controllable app-server.
- App-server clients can page large threads with unloaded, summary, or full turn item views.
- Bedrock auth can now use AWS console-login credentials from aws login profiles.
- `view_image` can resolve files through the selected environment for multi-environment sessions.

## Codex for Chrome (2026-05-07)

With the new extension for Chrome, Codex is even better at working with apps and websites in your browser. It works in parallel across tabs in the background without taking over your browser, and you stay in control of which websites Codex can use.

## Codex CLI 0.129.0 (2026-05-07)

### New Features
- The TUI now supports modal Vim editing in the composer, including `/vim`, default-mode config, and Vim-specific keymap contexts.
- TUI workflows are easier to resume and copy from with a redesigned resume/fork picker, raw scrollback mode, `/ide` context injection, and workspace-aware `/diff`.
- The status line can show theme-aware colors plus optional PR and branch-change summaries, and `/keymap` debug helps inspect terminal key events.
- Plugin management now supports workspace sharing, share access controls, source filtering, local share path tracking, marketplace removal/upgrades, remote bundle sync, and admin-disabled status handling.
- Hooks can be browsed and toggled from `/hooks`, can run before/after compaction, and can add PreToolUse context; Codex Apps auth and eligible MCP elicitations now surface through TUI/Guardian flows.
- Experimental goals are now discoverable, stay paused across resume unless the user opts back in, and show clearer validation and multi-day duration output.

## Codex CLI 0.128.0 (2026-04-30)

### New Features
- Added persisted `/goal` workflows with app-server APIs, model tools, runtime continuation, and TUI controls for create, pause, resume, and clear.
- Added `codex update`, configurable TUI keymaps, plan-mode nudges, action-required terminal titles, and active-turn `/statusline` and `/title` edits.
- Expanded permission profiles with built-in defaults, sandbox CLI profile selection, cwd controls, and active-profile metadata for clients.
- Improved plugin workflows with marketplace installation, remote bundle caching, remote uninstall, plugin-bundled hooks, hook enablement state, and external-agent config import.
- Added external agent session import, including background imports and imported-session title handling.
- Made MultiAgentV2 configuration more explicit with thread caps, wait-time controls, root/subagent hints, and v2-specific depth handling.

## Codex CLI 0.125.0 (2026-04-24)

### New Features
- App-server integrations now support Unix socket transport, pagination-friendly resume/fork, sticky environments, and remote thread config/store plumbing.
- App-server plugin management can install remote plugins and upgrade configured marketplaces.
- Permission profiles now round-trip across TUI sessions, user turns, MCP sandbox state, shell escalation, and app-server APIs.
- Model providers now own model discovery, with AWS/Bedrock account state exposed to app clients.
- `codex exec --json` now reports reasoning-token usage for programmatic consumers.
- Rollout tracing now records tool, code-mode, session, and multi-agent relationships, with a debug reducer command for inspection.

## GPT-5.5 and Codex app updates (2026-04-23)

GPT-5.5 is now available in Codex as OpenAI’s newest frontier model for complex coding, computer use, knowledge work, and research workflows.

### Browser use in the Codex app
The Codex app can now let Codex operate the in-app browser for local development servers and file-backed pages. Ask Codex to use the browser when it needs to click through a rendered UI, reproduce a visual bug, or verify a local fix inside the app. Browser use runs through the bundled Browser plugin.

### Automatic approval reviews
Codex can route eligible approval prompts through an automatic reviewer agent before the request runs.

## Codex CLI 0.124.0 (2026-04-23)

### New Features
- The TUI now has quick reasoning controls: `Alt+,` lowers reasoning, `Alt+.` raises it.
- App-server sessions can now manage multiple environments and choose an environment and working directory per turn.
- Added first-class Amazon Bedrock support for OpenAI-compatible providers, including AWS SigV4 signing and AWS credential-based auth.
- Remote plugin marketplaces can now be listed and read directly, with more reliable detail lookups and larger result pages.
- Hooks are now stable, can be configured inline in `config.toml` and managed `requirements.toml`, and can observe MCP tools as well as `apply_patch` and long-running Bash sessions.

## Codex CLI 0.123.0 (2026-04-23)

### New Features
- Added a built-in amazon-bedrock model provider with configurable AWS profile support.
- Added `/mcp verbose` for full MCP server diagnostics, resources, and resource templates while keeping plain `/mcp` fast.
- Made plugin MCP loading accept both `mcpServers` and top-level server maps in `.mcp.json`.
- Improved realtime handoffs so background agents receive transcript deltas and can explicitly stay silent when appropriate.
- Added host-specific `remote_sandbox_config` requirements for remote environments.
- Refreshed bundled model metadata, including the current `gpt-5.4` default.

## Codex CLI 0.122.0 (2026-04-20)

### New Features
- Standalone installs are more self-contained, and `codex app` now opens or installs Desktop correctly on Windows and Intel Macs.
- The TUI can open `/side` conversations for quick side questions, and queued input now supports slash commands and `!` shell prompts while work is running.
- Plan Mode can start implementation in a fresh context, with context-usage shown before deciding whether to carry the planning thread forward.
- Plugin workflows now include tabbed browsing, inline enable/disable toggles, marketplace removal, and remote, cross-repo, or local marketplace sources.
- Filesystem permissions now support deny-read glob policies, managed deny-read requirements, platform sandbox enforcement, and isolated `codex exec` runs that ignore user config or rules.
- Tool discovery and image generation are now enabled by default, with higher-detail image handling and original-detail metadata support for MCP and js_repl image outputs.

## Codex can now help with more of your work 26.415 (2026-04-16)

Codex is becoming a broader workspace for getting work done with AI. This update makes it easier to start work with less setup, verify what Codex is building, create richer outputs, and keep momentum across longer-running tasks.

## Codex CLI 0.121.0 (2026-04-15)

### New Features
- Added `codex marketplace add` and app-server support for installing plugin marketplaces from GitHub, git URLs, local directories, and direct `marketplace.json` URLs.
- Added TUI prompt history improvements, including `Ctrl+R` reverse search and local recall for accepted slash commands.
- Added TUI and app-server controls for memory mode, memory reset/deletion, and memory-extension cleanup.
- Expanded MCP/plugin support with MCP Apps tool calls, namespaced MCP registration, parallel-call opt-in, and sandbox-state metadata for MCP servers.
- Added realtime and app-server APIs for output modality, transcript completion events, raw turn item injection, and symlink-aware filesystem metadata.
- Added a secure devcontainer profile with bubblewrap support, plus macOS sandbox allowlists for Unix sockets.

## Codex CLI 0.120.0 (2026-04-11)

### New Features
- Realtime V2 can now stream background agent progress while work is still running and queue follow-up responses until the active response completes.
- Hook activity in the TUI is easier to scan, with live running hooks shown separately and completed hook output kept only when useful.
- Custom TUI status lines can include the renamed thread title.
- Code-mode tool declarations now include MCP `outputSchema` details so structured tool results are typed more precisely.
- `SessionStart` hooks can distinguish sessions created by `/clear` from fresh startup or resume sessions.

## Codex CLI 0.119.0 (2026-04-10)

### New Features
- Realtime voice sessions now default to the v2 WebRTC path, with configurable transport, voice selection, native TUI media support, and app-server coverage for the new flow.
- MCP Apps and custom MCP servers gained richer support, including resource reads, tool-call metadata, custom-server tool search, server-driven elicitations, file-parameter uploads, and more reliable plugin cache refreshes.
- Remote/app-server workflows now support egress websocket transport, remote `--cd` forwarding, runtime remote-control enablement, sandbox-aware filesystem APIs, and an experimental `codex exec-server` subcommand.
- The TUI can copy the latest agent response with `Ctrl+O`, including better clipboard behavior over SSH and across platforms.
- `/resume` can now jump directly to a session by ID or name from the TUI.
- TUI notifications are more configurable, including Warp OSC 9 support and an opt-in mode for notifications even while the terminal is focused.

## Codex model availability update (2026-04-07)

We’re updating model availability for users who sign in with ChatGPT. Starting April 7, the model picker no longer shows `gpt-5.2-codex`, `gpt-5.1-codex-mini`, `gpt-5.1-codex-max`, `gpt-5.1-codex`, `gpt-5.1`, or `gpt-5`. On April 14, we’ll remove those models from Codex for ChatGPT sign-in.

Users can still choose from `gpt-5.4`, `gpt-5.4-mini`, `gpt-5.3-codex`, and `gpt-5.2`. ChatGPT Pro users can also choose `gpt-5.3-codex-spark`.

## Build and install plugins in Codex (2026-03-25)

Codex now supports plugins: installable bundles that package skills, app integrations, and MCP server configuration for reusable workflows.
Plugins are available in the Codex app, CLI, and IDE extensions. You can install curated plugins from the plugin directory, or scaffold a local plugin with `@plugin-creator` and test it with workspace-scoped or home-scoped marketplaces.

## Codex app 26.323 (2026-03-24)

### New features
- Added search for past Codex app threads, including a sidebar shortcut and keyboard shortcuts for jumping to recent threads.
- Added a one-click option to archive all local threads in a project.
- Synced key settings between the Codex app and the VS Code extension, and added a settings entry point in the extension.

## Codex app 26.318 (2026-03-19)

### New features
- Added skills to the @ menu so you can insert them from the composer alongside other mentions.
- Cmd/Ctrl+F now starts with your current text selection, which makes searching reviews and diffs faster.

## Codex app 26.317 (2026-03-18)

### New features
- You can now fork a conversation from an earlier message, not just the latest turn.
- Added slash commands for switching models and reasoning levels, and made slash commands work in the middle of a draft prompt.
- Added notifications for plan mode questions so it’s easier to notice when Codex needs input.

## Introducing GPT-5.4 mini in Codex (2026-03-17)

GPT-5.4 mini is now available in Codex as a fast, efficient model for lighter coding tasks and subagents. It improves over GPT-5 mini across coding, reasoning, image understanding, and tool use while running more than 2x faster.

## Codex app 26.313 (2026-03-16)

### New features
- Added back and forward buttons in the header so you can move between recent screens more quickly.
- Added an Open in Finder, Open in Explorer, or Open in File Manager action from thread menus to jump straight to a thread’s project folder.

## Codex app 26.312 (2026-03-12)

### Themes
Change the Codex app appearance in Settings by choosing a base theme, adjusting accent, background, and foreground colors, and changing the UI and code fonts. You can also share your custom theme with friends.

### Revamped Automations
You can now choose whether automations run locally or on a worktree, define custom reasoning levels and models, and use templates to find inspiration for new automations.

## Codex app 26.311 (2026-03-11)

### New features
- Codex can now read the integrated terminal for the current thread, so it can check the status of a running development server or refer back to failed build output while it works with you.

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
