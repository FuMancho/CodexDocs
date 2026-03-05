# OpenAI Codex CLI Changelog

> Curated changelog sourced from the [official Codex changelog](https://developers.openai.com/codex/changelog).
> Last updated: 2026-03-05

## Codex CLI 0.111.0 (2026-03-05)

### New Features
- Fast mode is now enabled by default, and the TUI header shows whether the session is running in Fast or Standard mode.
- `js_repl` can now dynamically import local `.js` and `.mjs` files, making it easier to reuse workspace scripts from the REPL.
- Codex now tells the model which plugins are enabled at session start, improving discovery of installed MCPs, apps, and skills.
- App-server v2 now exposes MCP elicitation as a structured request/response flow instead of raw events, which simplifies client integrations.
- Expanded image workflow support for clients, including client-side handling of image-generation events and model metadata for image-capable web search.

### Bug Fixes
- Resuming a thread now preserves its stored git context and keeps apps enabled, avoiding broken state after `codex resume`.

## Codex CLI 0.110.0 (2026-03-05)

### New Features
- Added a plugin system that can load skills, MCP entries, and app connectors from config or a local marketplace, with an install endpoint for enabling plugins from the app server.
- Expanded the TUI multi-agent flow with approval prompts, `/agent`-based enablement, clearer prompts, ordinal nicknames, and role-labeled handoff context.
- Added a persisted `/fast` toggle in the TUI and app-server support for fast and flex service tiers.
- Improved memories with workspace-scoped writes, renamed memory settings, and guardrails against saving stale or polluted facts.
- Added a direct Windows installer script to published release artifacts.

### Bug Fixes
- Fixed `@` file mentions so parent-directory `.gitignore` rules no longer hide valid repository files.
- Made sub-agents faster and more reliable by reusing shell state correctly and fixing `/status`, `Esc`, pending-message handling, and startup/profile race conditions.
- Fixed project trust parsing so CLI overrides apply correctly to trusted project-local MCP transports.
- Fixed read-only sandbox policies so network access is preserved when it is explicitly enabled.
- Fixed multiline environment export capture and Windows state DB path handling in session state.
- Fixed ANSI/base16 syntax highlighting so terminal-themed colors render correctly in the TUI.

## Codex App 26.304 (2026-03-04)

### New Features
- The Codex app is now available on Windows. The app gives you one interface for working across projects, running parallel agent threads, and reviewing results in one place.
- The Windows app includes the same core features as the rest of the Codex app: Skills, Automations, and Worktrees.

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
