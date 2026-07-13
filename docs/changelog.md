# OpenAI Codex CLI Changelog

> Curated changelog sourced from the [official Codex changelog](https://developers.openai.com/codex/changelog).
> Last updated: 2026-07-13

## Codex CLI 0.144.3 (2026-07-13)

### Chores
- Published a version-only release with no merged pull request changes since rust-v0.144.2.

## Codex CLI 0.144.2 (2026-07-13)

### Bug Fixes
- Restored the previous Guardian auto-review policy, request format, and tool behavior after rolling back a prompting regression. (#32672)

## Codex joins the ChatGPT desktop app (2026-07-09)

Codex is now part of the ChatGPT desktop app on macOS and Windows.
Existing Codex app users can update as usual and keep their
projects, settings, and workflows. You can make Codex the default
view and, on macOS, keep the Codex app icon.

### New Features
- Edit Markdown and code directly in the app, use inline annotations, and ask Codex to revise selected content.
- Review GitHub pull requests in the sidebar, with reviewer feedback alongside the diff, without leaving the app.
- Work across repositories in one project.

### Performance improvements and bug fixes
- Made Computer Use faster with GPT-5.6.
- Made task activity and progress easier to follow while Codex works.
- Simplified plugin management by moving it into Settings.
- Improved mobile connection reliability and fixed video rendering for SSH projects.
- Additional performance improvements and bug fixes.

## Codex CLI 0.144.1 (2026-07-09)

### Bug Fixes
- Fixed standalone installs failing when GitHub returns compact or reordered release metadata. (#31913)
- Ensured macOS package installs expose the code-mode host alongside the codex executable. (#31913)
- Kept code mode working when the companion host binary is unavailable by falling back to the embedded runtime. (#31913)

## Codex CLI 0.144.0 (2026-07-09)

### New Features
- Usage-limit reset credits now show their type and expiration, and let you choose which credit to redeem. (#30488)
- Added a writes app-approval mode that allows declared read-only actions while prompting for writes. (#30482)
- MCP tools can now request authentication interactively without an experimental opt-in. (#28772)
- App-server hosts can provide Codex authentication at runtime and redirect successful logins to a hosted page. (#28745,
- Global pnunen installs are now detected so diagnostics and updates use the correct package manager. (#31503)
- Selecting Ultra reasoning now warns when high multi-agent concurrency could increase usage quickly. (#31621)

### Bug Fixes
- Resumed ChatGPT threads recover when compaction references a retired model by retrying with the currently selected model. (#30319)
- Fixed Code Mode crashes in Intel macOS release binaries. (#30953)
- Windows sandbox sessions can delete files in writable roots and access the managed primary runtime. (#31138,
- Pasted terminal control sequences can no longer corrupt TUI rendering or resumed conversation history. (#31494)
- Long-running app sessions now refresh expired authentication for the hosted codex_apps connector. (#31486)
- Responses WebSockets continue using the low-latency transport while respecting system proxies and custom certificate authorities. (#31441, #31622)

### Documentation
- Device-code login warnings now explain how to recognize and stop phishing attempts. (#31648)

### Chores
- Reduced plugin skill-loading time on remote executors by resolving namespaces once per root. (#31348)
- Made the /review branch picker faster and more reliable in large repositories. (#31464)
- Improved automatic review behavior with clearer instructions and a focused tool set. (#31480)
- Made Amazon Bedrock model names clearly identify their GPT-5.6 family and variant. (#31636)

## Codex CLI 0.143.0 (2026-07-08)

### New Features
- Remote plugins are now enabled by default, with richer catalog rows, npm marketplace sources, and visible remote/local versions. (#30297, #26705, #29375, #30981)
- Codex can route authentication and Responses API traffic through macOS and Windows system proxies, including PAC and WPAD configurations. (#26708, #26709, #31335)
- Added codex remote-control pair for generating manual pairing codes from a running daemon. (#29913)
- Added Amazon Bedrock GPT-5.6 Sol, Terra, and Luna models, with first-class support for max reasoning effort. (#30285,
- MCP tools now use tool search by default, and ChatGPT-hosted MCP servers can explicitly use session authentication. (#29486, #29733)
- App-server clients can inspect environments, list descendant threads, and fork history through a specific turn. (#30291, #29591, #30277)

### Bug Fixes
- Fixed Windows ConPTY input handling for line endings and backspace, plus sandbox credential retry edge cases. (#29734, #29624, #29637)
- Fixed stale TUI safety prompts and cancelled reviews that could leave MCP startup appearing busy. (#30490,
- Improved recovery when exec servers are temporarily offline and prevented remote-control token refresh retry storms. (#30098, #30201)
- Preserved trailing realtime transcript text and terminal rollout events during shutdown. (#29918, #30144)
- Improved incremental WebSocket request success by ignoring response metadata during comparisons. (#30770)
- Reduced installer failures from GitHub API rate limits by reusing release metadata. (#31056)

### Documentation
- Documented UUID7 thread and turn IDs, plus recommended remote-executor integration-test workflows. (#27714,

### Chores
- Updated OpenSSL, Hono, fast-uri, quick-xml, and crossbeam-epoch to address security advisories. (#29487,

## ChatGPT for iOS 1.2026.181 (2026-07-06)

### New Features
- Added support for creating, searching, opening, forking, and managing Codex tasks directly from a conversation.
- Added filters for staged, unstaged, branch, and last-turn changes, with controls for comparing branches.
- Added support for adding selected transcript text directly to the composer.
- Added previews for image and file attachments before sending.
- Added inline Photos and Camera pickers to the attachment menu.
- Added a connection shortcut and support for SSH hosts using private keys or no credentials.
- Added usage limits and credit details to the task menu.

### Performance improvements and bug fixes
- Improved the task list with consistent task terminology, clearer delegated task titles, and a Needs input status.
- Improved initial task loading and foreground recovery.
- Improved autocomplete by selecting the first result automatically and accepting it with Return.
- Improved model, reasoning, and Fast settings so changes remain scoped to the current task.
- Improved task-management and dynamic tool activity presentation.
- Improved side chats to open directly when only one conversation is available.
- Improved plugin autocomplete with installed plugins and their icons.
- Improved workspace diff accuracy and expand-and-collapse navigation.
- Improved recovery by preserving thread state across reconnects and host pairings across sign-out.
- Fixed stuck thread-list loading, prompt mode deadlocks, stale images, and microphone permission alerts.
- Fixed shake to undo and keyboard refocusing after sending a prompt.

## Codex CLI 0.142.5 (2026-07-01)

### Bug Fixes
- Prevented full Responses WebSocket request payloads from being written to trace logs. (#30771) June 2026

## Codex CLI 0.142.4 (2026-06-29)

### Chores
- No user-facing changes were identified for this release.

## Codex CLI 0.142.3 (2026-06-26)

### Chores
- Maintenance-only patch release with no user-facing changes since 0.142.2.

## Codex Remote reaches general availability (2026-06-25)

Codex Remote has reached general availability. Use Codex from the
ChatGPT mobile app to start or continue work on a connected Mac or
Windows host, review progress, and approve actions from your phone.
Remote Control now uses authenticated one-to-one QR pairing between
each iOS or Android device and each host. Update the ChatGPT mobile
app and Codex App to the latest versions before connecting.
Connections used since June 8, 2026, remain paired; older inactive
connections need to pair again.
The new DigitalOcean plugin lets Codex provision a
DigitalOcean Droplet, configure SSH access, and connect it to the
Codex App as a remote workspace.
See Remote connections for setup and troubleshooting.

## Codex CLI 0.142.2 (2026-06-25)

### New Features
- MCP tools now use tool search by default when supported, improving tool discovery while preserving compatibility with older models and providers.
- macOS authentication clients can honor system proxy, PAC, and WPAD settings when respect_system_proxy is enabled.
- Plugins can provide dedicated dark-mode logos through local manifests and remote catalogs.
- Apps can display richer safety-buffering UI using server-provided visibility and faster-model metadata.

### Bug Fixes
- Remote plugin catalogs now return curated featured-plugin rankings.
- Expired Amazon Bedrock credentials now produce actionable recovery guidance instead of a generic authorization error.
- Remote stdio MCP servers now accept absolute working directories written in the remote platform’s path format.
- Remote HTTP(S) image inputs now return clear model-visible validation errors; inline data URLs and local images remain supported.
- PowerShell commands containing executable AST regions the safety classifier cannot inspect now require approval.
- Code Mode now warns when the selected model lacks the required metadata.

### Chores
- Updated bundled OpenSSL and esbuild dependencies to patched releases.
- Successful formatter runs are now quiet while failures still show diagnostics.

## Codex CLI 0.142.1 (2026-06-25)

### New Features
- Added opt-in Windows system proxy support for authentication, including PAC, WPAD, static proxies, and bypass rules.

## ChatGPT for iOS 1.2026.167 (2026-06-22)

### New Features
- Added per-host personality settings with Friendly and Pragmatic options.
- Added support for editing goals directly in the composer.
- Added a link from forked conversations back to the original thread.

### Performance improvements and bug fixes
- Improved side chat visibility with separate conversations above the composer.
- Improved composer autocomplete for commands, skills, and plugins from any prefix.
- Improved progress visibility for subagents, tasks, and worktree creation.
- Fixed long threads loading.
- Improved workspace file search, code review drafts, steering, and host setup and recovery.
- Fixed Face ID unlocking, stopping responses, collapsed sections, and dark-mode host indicators.

## Codex CLI 0.142.0 (2026-06-22)

### New Features
- /usage can now show and redeem earned usage-limit reset credits, with confirmation, retry, and refreshed availability states.
- /plugins now organizes remote plugins into OpenAI Curated, Workspace, and Shared with me sections, while eligible turns can recommend and install relevant plugins.
- Configurable rollout token budgets track usage across agent threads, provide remaining-budget reminders, and abort turns when exhausted.
- App-server clients can configure multi-agent delegation as disabled, explicit-request-only, or proactive at the thread and turn level.
- Added an indexed web-search mode that permits live searches while restricting direct page access to server-approved URLs.
- Codex can now receive scheduled UTC time reminders and query the current time directly, including through client-provided app-server clocks.

### Bug Fixes
- Restored reliable Linux TUI rendering after suspending with Ctrl+Z and resuming with fg.
- Exec-server processes and stdio MCP sessions now survive transient disconnects, including signed-URL refresh and retry-safe stdin writes.
- Remote environments now preserve executor-native paths, shells, AGENTS.md discovery, and sandbox behavior across operating systems.
- Plugin loading and installation now handle root marketplace layouts, manifest fallbacks, multiple skill paths, actionable download errors, and immediate tool refreshes.
- Parent agents now receive terminal subagent errors instead of seeing failed work as an empty successful completion.
- Goal-first threads are once again persisted and returned by thread/list and thread/search.

### Chores
- Reduced startup and session latency by deferring unnecessary DNS work, warming the model cache, reusing parsed plugin skills, parallelizing skill metadata reads, and skipping redundant catalog synchronization.
- Reduced persistent-log churn by removing per-event WebSocket payload logging and filtering duplicated telemetry records.

## Codex app 26.616 (2026-06-18)

### New Features
- Added Record & Replay, a macOS feature that turns a demonstrated workflow into a reusable skill. Initial availability excludes the European Economic Area, the United Kingdom, and Switzerland. You or your administrator must also enable Computer Use.
- Added bulk actions to automation run history so you can mark every run as read or archive eligible runs.
- Added thread handoff between local and remote hosts, so you can move a thread to a matching project on a connected host and continue it there. Codex can also coordinate the handoff for you.

### Performance improvements and bug fixes
- Added new deep links to manage SSH connections.
- Improved Browser Use so visible-tab routing and annotations persist when a draft browser session moves to the server.
- Additional performance improvements and bug fixes.

## Codex CLI 0.141.0 (2026-06-18)

### New Features
- Remote executors now use authenticated, end-to-end encrypted Noise relay channels.
- Cross-platform remote execution now preserves executor-native working directories and shells, including filesystem permission paths across app-server and exec-server boundaries.
- Selected executor plugins can activate their stdio MCP servers per thread; plugin discovery also adds a created-by-me marketplace and auth-specific curated catalogs.
- App-server clients can list immediate child threads, correlate external-agent imports with detailed results, and read or redeem rate-limit reset credits.
- Realtime clients can explicitly append speech, control how Codex responses enter conversations, and omit startup context.
- TUI input prompts can auto-resolve after inactivity, with a countdown that pauses on interaction.

### Bug Fixes
- Hook trust bypass now persists through codex exec thread start and resume, while blocking PostToolUse hooks correctly reject code-mode tool calls.
- Plugin capabilities now route consistently by authentication mode, deduplicate conflicting App/MCP declarations, and preserve remote marketplace ordering.
- Windows sandbox execution repairs stale credentials automatically and gives PowerShell commands more time before backgrounding.
- Idle exec-server relays remain connected, and steered user input immediately interrupts wait_agent.
- Bundled SQLite is pinned to a version containing the WAL-reset corruption fix.
- TLS connections now support P-521 certificate signatures commonly used by enterprise proxies.

### Chores
- Reduced latency and memory use in large, tool-heavy sessions by caching tool search and eliminating repeated request and history copies.
- Bounded prompt-image caching to 64 MiB and feedback uploads to eight related threads.
- Terminal resize reflow is now always enabled, ignoring obsolete disabled settings.

## Codex app features are available in the EEA, UK, and Switzerland (2026-06-16)

More Codex app capabilities are rolling out to users in the
European Economic Area, the United Kingdom, and Switzerland:
- Computer Use is available on macOS and Windows in these regions, so Codex can operate desktop apps by seeing, clicking, and typing.
- The Codex Chrome extension is available for browser tasks that need signed-in Chrome context, working across tabs in the background without taking over your browser.
- Memories can remember useful preferences, recurring workflows, tech stacks, and repository conventions when enabled. Memories are off by default in the European Economic Area, the United Kingdom, and Switzerland.
- Chronicle is available as an opt-in research preview for ChatGPT Pro subscribers on macOS, helping Codex build memories from recent screen context.

## ChatGPT for iOS 1.2026.160 (2026-06-15)

### New Features
- Added a workspace file browser for previewing files and linking workspace paths into prompts.
- Added a directory picker for choosing a workspace folder when starting a new thread.
- Added controls to expand or collapse all diffs while reviewing changed files.
- Added MCP approval choices for allowing requested actions in the current chat or across chats.
- Added LaTeX rendering in Codex messages and plans.

### Performance improvements and bug fixes
- Improved status indicators for running threads, queued prompts, side chats, and subagents.
- Improved pairing and onboarding with clearer errors, manual pairing-code support, and more reliable host selection after pairing.
- Improved task-list recovery, reconnect state, host-specific refresh, and thread performance.
- Improved Codex profile sharing, activity history, and settings layout.
- Improved goal workflows with a composer shortcut, desktop-aligned goal message actions, and better resumed question handling.
- Improved assistant message actions, transcript layout, and public rate-limit names.
- Fixed stuck thread-list swipe actions, duplicate messages when reopening a new thread, spawned subagents appearing as top-level task rows, and misleading connection errors when sending prompts.

## Codex CLI 0.140.0 (2026-06-15)

### New Features
- Added /usage views for daily, weekly, and cumulative account token activity.
- /goal now preserves oversized text, large pasted blocks, and image attachments, including in remote app-server sessions.
- Added permanent session deletion through codex delete, /delete, and app-server thread/delete, with confirmation safeguards and subagent cleanup.
- Added /import for selectively importing setup, project configuration, and recent chats from Claude Code.
- Typing @ now opens the unified mentions menu for files, plugins, and skills by default.
- Added managed Amazon Bedrock API-key authentication and encrypted local storage for CLI and MCP OAuth credentials.

### Bug Fixes
- Corrupted SQLite state databases are now backed up and rebuilt automatically from rollout data, including malformed database-directory cases.
- Prevented /review from crashing when Esc is pressed with queued guidance, while preserving that guidance when the review is canceled.
- Improved MCP reliability by retrying transient startup failures, reporting unusable OAuth credentials as logged out, and preserving explicitly disabled servers.
- Fixed remote plugin uninstall requests and correctly surfaced apps requiring authentication during installation.
- Persisted “Don’t remind me” update dismissals reliably and cleared stale running-hook indicators after completed turns.
- Non-TTY background commands can now be interrupted with Ctrl-C while preserving their final output and exit status.

### Documentation
- Clarified contributor guidance around keeping crate APIs narrow and supporting Linux, macOS, and Windows.

### Chores
- Improved responsiveness for large repositories and long sessions by preserving Git’s built-in filesystem monitor, avoiding duplicate history reads, accelerating archive lookup, and caching turn-diff rendering.
- Removed the experimental /realtime voice controls and related audio dependencies from the TUI.

## Codex app 26.609 (2026-06-11)

### New Features
- Added rate-limit reset banking for Plus and Pro users, including one free reset at launch and referral invitations for earning more during the current promotion. Eligible Business members can invite coworkers to earn shared workspace credits through a separate referral program.
- Added Developer mode for Browser use in Chrome and the Codex in-app browser. It gives Codex controlled Chrome DevTools Protocol (CDP) access for performance profiling and deeper debugging of network traffic, console output, runtime errors, and page state.
- Added the /init command to the app composer for creating project instructions with the same initialization workflow as the Codex CLI.
- Added customizable macOS Dock icons with light and dark Codex variants.
- Added Computer Use for Enterprise users outside the European Economic Area, the United Kingdom, and Switzerland.
- Added support for configuring per-app access controls for Computer Use on Windows.
- Added an Unread chats section to the command menu, with the most recently updated unread chat selected by default.

### Performance improvements and bug fixes
- Made Browser use up to 2x faster through CDP and DOM snapshot optimizations that reduce browser round trips.
- Made command, browser, integration, and source activity summaries easier to understand, and improved how completed chats present files, automations, and other durable output.
- Improved plugin management by including workspace plugins, refreshing plugin state more reliably after installation or removal, and letting you upload a new version of an already-shared plugin without changing its access.
- Improved usage-limit errors with inline plan and workspace guidance, including reset timing when available.
- Added Cmd+Enter and Ctrl+Enter as shortcuts for submitting custom approval feedback.
- Fixed Browser use download handling and improved Developer mode recovery and diagnostics.
- Fixed scheduled automations so they honor the selected approval mode, and fixed manual project ordering, Browser tab dragging, MCP app sizing after right-pane transitions, and clickable ChatGPT thread mentions.
- Fixed issues affecting background agent tab restoration, commit and pull request message generation, sidebar pull request status updates, Codex Mobile QR pairing, remote-control MFA, remote SSH installation and connection, updater prompts, and overlay positioning at non-default zoom levels.
- Additional performance improvements and bug fixes.

## Codex app 26.608 (2026-06-09)

### New Features
- Added Import to Codex flows for importing supported setup from Claude Code and Claude Cowork, including during onboarding.
- Revamped plugins screen with separate tabs, marketplace and category filters, keyboard navigation, and clearer install actions.
- Expanded Settings search to find options from more panels, including Git and pets.

### Performance improvements and bug fixes
- Fixed goal timer overlap in narrow layouts.
- Reduced unread notifications while an active goal continues running.
- Kept review diff ordering consistent with the file tree.
- Improved window rendering on systems that don’t support translucent backdrops, including Windows 10.
- Additional performance improvements and bug fixes.

## ChatGPT for iOS 1.2026.153 (2026-06-09)

### New Features
- Added support for choosing a branch, creating a worktree, and running an environment setup script for new threads.
- Added a Codex profile screen with usage stats and token activity charts.
- Added /goal support for creating and managing goals from Codex Mobile.
- Added inline review comments when viewing changed files.
- Added support for asking in side chat from selected transcript text.
- Added support for editing the latest sent prompt.

### Performance improvements and bug fixes
- Improved attachment support on Windows hosts.
- Skills and plugins now appear directly inline in the composer.
- Improved side chat and queued prompt visibility while a thread is running.
- Improved message styling, navigation, tool activity, Face ID behavior, archived-thread browsing, and thread UI polish.

## Codex CLI 0.139.0 (2026-06-09)

### New Features
- Code mode can now call standalone web search directly, including from nested JavaScript tool calls, and receive plaintext search results.
- Tool and connector input schemas now preserve oneOf and allOf, and large schemas keep more shallow structure when compacted, improving compatibility with richer MCP tools.
- codex doctor now includes editor and pager environment details in the local report while redacting raw values in JSON output.
- Plugin marketplace automation is more informative and responsive: codex plugin marketplace list --json now includes each marketplace source, and plugin lists can return from the cached remote catalog before refreshing in the background.

### Bug Fixes
- codex resume --last "..." and codex fork --last "..." now treat the trailing argument as the initial prompt instead of misreading it as a session ID.
- MCP startup warnings from subagents now stay in the thread that owns them, avoiding duplicate parent-thread alerts and stuck startup spinners in the TUI.
- Image edits now use the exact referenced image file paths instead of guessing from conversation history, so attached-image edits land on the intended input.
- Bare URLs with ~ in the path are now linkified end to end in the TUI instead of being truncated before the tilde.
- Thread resets such as /new, /clear, and /fork no longer drop cloud-managed requirements or feature flags during TUI config reloads.
- Sandbox execution now preserves approved escalation decisions and enforces configured proxy-only networking more consistently.

### Chores
- Release builds once again publish separate symbol archives with line tables, improving post-release crash symbolication without bringing back the earlier full-debug build slowdown.
- The embedded V8 toolchain was updated to rusty_v8 149.2.0.

## Codex CLI 0.138.0 (2026-06-08)

### New Features
- The /app command can now hand off the current CLI thread into Codex Desktop on macOS and native Windows, and Windows workspace launches can open directly into Desktop instead of stopping at a manual prompt.
- Local image attachments and standalone image generations now expose their saved file paths to the model, which makes follow-up edits and file references more reliable.
- Reasoning effort selection is more flexible: the TUI adds fallback shortcuts for terminals that miss Alt bindings, and model-defined effort levels now flow through in the order advertised by the model.
- App-server integrations can now read account token usage, and Codex auth supports v2 personal access tokens in CLI and app-server flows.
- Plugin automation got richer structured output: add/remove and marketplace commands support --json, plugin list JSON includes marketplace source, and plugin detail data now exposes default prompts, remote MCP servers, and unavailable app templates.

### Bug Fixes
- Goal workflows are more predictable: multiline paste in /goal edit no longer submits early, idle auto-turns stay out of Plan mode, and goals stop auto-continuing after terminal turn failures.
- Forked threads now keep user-renamed titles instead of falling back to the original first-prompt name.
- The TUI no longer adds extra blank space while streaming, and cancelled prompts reopen with the cursor at the end so you can keep editing naturally.
- TUI config write failures now show the underlying cause, making validation problems and read-only filesystem issues much easier to diagnose.
- Startup is more resilient across environments, with support for /usr/bin/bash, shorter Linux proxy socket paths, and pre-refresh of expired OAuth-backed MCP credentials.
- Workspace instruction loading is more accurate for remote and symlinked workspaces, so the right AGENTS.md files are picked up consistently.

### Documentation
- The CLI README was refreshed to remove stale guidance and better match the current documentation flow.

### Chores
- TUI startup does less repeated plugin work by reusing discovery results and loading only hook metadata on the critical path.
- resume --last now finds the newest matching session through the state DB first, which speeds up restore on large local histories.
- Large MCP/Ollama streams and long message histories process much faster thanks to optimized byte scanning.

## Codex app updates 26.602 (2026-06-04)

### New Features
- Added activity insights and share cards to the Profile section. You can review Codex usage highlights and save a profile card; sharing is available on consumer ChatGPT plans.

### Performance improvements and bug fixes
- Improved Computer Use startup readiness and appshot error reporting.
- Fixed browser and review UI issues, including fullscreen browser composer controls, hex color swatches, terminal scrollbar alignment, and animated diff stat alignment.
- Expanded onboarding with more role choices so Codex can tailor first-run suggestions more accurately.
- Fixed configuration writes after plugin installation.
- Additional performance improvements and bug fixes.


## Appshots, goal mode, and more 26.519 (2026-05-21)

Appshots are now available in the Codex app on macOS. Press both Command keys to send the frontmost app window to Codex with a screenshot and available text, so Codex can work from context in another app without you copying, pasting, or describing it manually.

This launch also includes:
- Goal mode is no longer an experimental feature and is available in the Codex app, IDE extension, and CLI. With Goal mode, you can have Codex drive toward a specific objective for hours or even days.
- Remote computer use, so Codex can use desktop apps after your Mac locks, including remotely via Codex Mobile. Codex scopes locked use to active, trusted computer use turns and includes safeguards such as short-lived authorization, covered displays, relock on local input, and manual-unlock fallback.
- Plugin sharing through marketplace sources is available for ChatGPT Business. Enterprise support will be available in a future update. Teams can distribute reusable plugin bundles that include skills, app integrations, MCP servers, and lifecycle hooks.
- Advanced in-app browser annotations let you tweak styling such as font size, colors, and spacing directly using annotations. This gives Codex a clearer signal for changes.
- Browser-use improvements across in-app browser & Chrome:
  - Codex can now download and extract all image assets from a page much more quickly.
  - Codex can now extract structured data from pages more effectively and find information more quickly with a read-only JS sandbox.
- Chrome extension will create less clutter when using it. Codex will no longer create tab groups when taking over existing tabs, and at the end of a task for handoff. Instead, it uses tab icons to indicate status.
- Significantly improved reliability for browser use. We fixed bugs on Windows, flaky availability of the plugin to non geo-blocked regions, and many other issues impacting performance.

## Codex CLI 0.133.0 (2026-05-21)

### New Features
- Goals are now enabled by default, backed by dedicated storage, and track progress across active turns.
- `codex remote-control` now runs like a foreground command, waits for readiness, reports machine status, and keeps explicit daemon-style start/stop commands.
- Permission profiles gained list APIs, inheritance, managed `requirements.toml` support, runtime refresh behavior, and stronger Windows sandbox integration.
- Plugin discovery is easier to inspect, with marketplace-aware list output, installed versions, visible marketplace roots, and remote collection support.
- Extensions can observe more lifecycle events, including subagent start/stop, tool execution, turn metadata, and async approval/turn processing.

## Codex CLI 0.132.0 (2026-05-20)

### New Features
- The Python SDK now supports first-class authentication, including API key login, ChatGPT browser and device-code flows, account inspection, and logout APIs.
- Python turn APIs are easier to use for text-only workflows: you can pass a plain string as input, and handle-based runs now return a richer TurnResult with collected items, timing, and usage data.
- `codex exec resume` now accepts `--output-schema`, so resumed automations can keep session context while still enforcing structured JSON output.
- TUI startup is faster because terminal capability probes are now batched instead of waiting on several serial checks before the first interactive frame.
- Remote executor registration can now use standard Codex auth instead of a separate registry credential flow.
- App-server turns can preserve requested image fidelity, including original-resolution local images, across user inputs and image-producing tools.

## Codex CLI 0.131.0 (2026-05-18)

### New Features
- The TUI now offers richer session controls and display: data-driven service-tier commands, blended token usage, permissions/approval mode, effective workspace roots, and responsive Markdown tables.
- `@` mentions now search files, directories, plugins, and skills in one picker, backed by app-server plugin metadata.
- Plugin workflows gained marketplace CLI commands, version-aware sharing, share checkout, clearer shared-workspace buckets, and default-enabled plugin hooks.
- Remote workflows now support daemon-managed `codex remote-control`, runtime enable/disable APIs, status reads, and registry-backed/configured remote environments.
- The Python SDK moved to `openai-codex` / `openai_codex`, with pinned runtime-generated types, concurrent turn routing, approval modes, and integration coverage.
- Added `codex doctor` for support-ready diagnostics across runtime, auth, terminal, network, config, and local state.

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
