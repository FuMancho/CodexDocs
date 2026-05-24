# OpenAI Codex CLI Changelog

> Curated changelog sourced from the [official Codex changelog](https://developers.openai.com/codex/changelog).
> Last updated: 2026-05-21

## Appshots, goal mode, and more 26.519 (2026-05-21)

  [Appshots](/codex/appshots "/codex/appshots") are now available in the Codex app on macOS. Press
  both Command keys to send the frontmost app window to Codex with a screenshot
  and available text, so Codex can work from context in another app without you
  copying, pasting, or describing it manually.

  This launch also includes:

- [Goal mode](/codex/prompting#goal-mode "/codex/prompting#goal-mode") is no longer an experimental feature
    and is available in the Codex app, IDE extension, and CLI. With Goal mode, you
    can have Codex drive toward a specific objective for hours or even days.
- [Remote computer use](/codex/app/computer-use#locked-use "/codex/app/computer-use#locked-use"), so Codex can use
    desktop apps after your Mac locks, including remotely via Codex Mobile. Codex
    scopes locked use to active, trusted computer use turns and includes
    safeguards such as short-lived authorization, covered displays, relock on
    local input, and manual-unlock fallback.
- [Plugin sharing](/codex/plugins/build#share-a-local-plugin-with-your-workspace "/codex/plugins/build#share-a-local-plugin-with-your-workspace")
    through marketplace sources is available for ChatGPT Business. Enterprise
    support is arriving shortly. Teams can distribute reusable plugin bundles that
    include skills, app integrations, MCP servers, and lifecycle hooks.
- [Advanced in-app browser annotations](/codex/app/browser#styling-feedback "/codex/app/browser#styling-feedback")
    let you tweak styling such as font size, colors, and spacing directly using
    annotations. This gives Codex a clearer signal for changes.
- Browser-use improvements across in-app browser & Chrome:
    - Codex can now download and extract all image assets from a page much more
      quickly.
    - Codex can now extract structured data from pages more effectively and find
      information more quickly with a read-only JS sandbox.
- Chrome extension will create less clutter when using it. Codex will no longer
    create tab groups when taking over existing tabs, and at the end of a task for
    handoff. Instead, it uses tab icons to indicate status.
- Significantly improved reliability for browser use. We fixed bugs on Windows,
    flaky availability of the plugin to non geo-blocked regions, and many other
    issues impacting performance.

---

## Codex CLI 0.133.0 (2026-05-21)


  ### New Features

- Goals are now enabled by default, backed by dedicated storage, and track progress across active turns. ([#23300](https://github.com/openai/codex/pull/23300 "https://github.com/openai/codex/pull/23300"), [#23685](https://github.com/openai/codex/pull/23685 "https://github.com/openai/codex/pull/23685"), [#23696](https://github.com/openai/codex/pull/23696 "https://github.com/openai/codex/pull/23696"), [#23732](https://github.com/openai/codex/pull/23732 "https://github.com/openai/codex/pull/23732"))
- `codex remote-control` now runs like a foreground command, waits for readiness, reports machine status, and keeps explicit daemon-style `start`/`stop` commands. ([#22878](https://github.com/openai/codex/pull/22878 "https://github.com/openai/codex/pull/22878"))
- Permission profiles gained list APIs, inheritance, managed `requirements.toml` support, runtime refresh behavior, and stronger Windows sandbox integration. ([#22928](https://github.com/openai/codex/pull/22928 "https://github.com/openai/codex/pull/22928"), [#23412](https://github.com/openai/codex/pull/23412 "https://github.com/openai/codex/pull/23412"), [#22270](https://github.com/openai/codex/pull/22270 "https://github.com/openai/codex/pull/22270"), [#23433](https://github.com/openai/codex/pull/23433 "https://github.com/openai/codex/pull/23433"), [#22931](https://github.com/openai/codex/pull/22931 "https://github.com/openai/codex/pull/22931"), [#23715](https://github.com/openai/codex/pull/23715 "https://github.com/openai/codex/pull/23715"))
- Plugin discovery is easier to inspect, with marketplace-aware list output, installed versions, visible marketplace roots, and remote collection support. ([#23372](https://github.com/openai/codex/pull/23372 "https://github.com/openai/codex/pull/23372"), [#23584](https://github.com/openai/codex/pull/23584 "https://github.com/openai/codex/pull/23584"), [#23727](https://github.com/openai/codex/pull/23727 "https://github.com/openai/codex/pull/23727"), [#23730](https://github.com/openai/codex/pull/23730 "https://github.com/openai/codex/pull/23730"))
- Extensions can observe more lifecycle events, including subagent start/stop, tool execution, turn metadata, and async approval/turn processing. ([#22782](https://github.com/openai/codex/pull/22782 "https://github.com/openai/codex/pull/22782"), [#22873](https://github.com/openai/codex/pull/22873 "https://github.com/openai/codex/pull/22873"), [#23309](https://github.com/openai/codex/pull/23309 "https://github.com/openai/codex/pull/23309"), [#23688](https://github.com/openai/codex/pull/23688 "https://github.com/openai/codex/pull/23688"), [#23690](https://github.com/openai/codex/pull/23690 "https://github.com/openai/codex/pull/23690"), [#23692](https://github.com/openai/codex/pull/23692 "https://github.com/openai/codex/pull/23692"))

  ### Bug Fixes

- Fixed TUI startup choosing the wrong working directory when reusing a local app-server socket. ([#23538](https://github.com/openai/codex/pull/23538 "https://github.com/openai/codex/pull/23538"))
- Fixed plan-mode free-form answers so modified Enter keys, like Shift+Enter, no longer submit unexpectedly. ([#23536](https://github.com/openai/codex/pull/23536 "https://github.com/openai/codex/pull/23536"))
- Removed stale background terminal poll events after a process exits. ([#23231](https://github.com/openai/codex/pull/23231 "https://github.com/openai/codex/pull/23231"))
- Preserved raw code-mode exec output unless an explicit output token limit is requested. ([#23564](https://github.com/openai/codex/pull/23564 "https://github.com/openai/codex/pull/23564"))
- Made AGENTS instruction loading more reliable, including local global reads and warnings for invalid UTF-8 instead of silent drops. ([#23343](https://github.com/openai/codex/pull/23343 "https://github.com/openai/codex/pull/23343"), [#23232](https://github.com/openai/codex/pull/23232 "https://github.com/openai/codex/pull/23232"))
- Fixed app-server startup/shutdown races, empty resume/fork paths, plugin upgrade failures, and realtime v1 websocket compatibility. ([#23516](https://github.com/openai/codex/pull/23516 "https://github.com/openai/codex/pull/23516"), [#23578](https://github.com/openai/codex/pull/23578 "https://github.com/openai/codex/pull/23578"), [#23400](https://github.com/openai/codex/pull/23400 "https://github.com/openai/codex/pull/23400"), [#23356](https://github.com/openai/codex/pull/23356 "https://github.com/openai/codex/pull/23356"), [#23771](https://github.com/openai/codex/pull/23771 "https://github.com/openai/codex/pull/23771"))

  ### Documentation

- Added clearer plugin-creator guidance for updating and reinstalling local personal plugins. ([#23542](https://github.com/openai/codex/pull/23542 "https://github.com/openai/codex/pull/23542"))
- Expanded app-server/API docs and schema coverage around managed permission profile requirements. ([#23433](https://github.com/openai/codex/pull/23433 "https://github.com/openai/codex/pull/23433"), [#23555](https://github.com/openai/codex/pull/23555 "https://github.com/openai/codex/pull/23555"))

  ### Chores

- Added a canonical Codex package archive pipeline and moved installers, npm packages, DotSlash, and SDK runtimes toward that shared layout. ([#23513](https://github.com/openai/codex/pull/23513 "https://github.com/openai/codex/pull/23513"), [#23582](https://github.com/openai/codex/pull/23582 "https://github.com/openai/codex/pull/23582"), [#23586](https://github.com/openai/codex/pull/23586 "https://github.com/openai/codex/pull/23586"), [#23596](https://github.com/openai/codex/pull/23596 "https://github.com/openai/codex/pull/23596"), [#23635](https://github.com/openai/codex/pull/23635 "https://github.com/openai/codex/pull/23635"), [#23636](https://github.com/openai/codex/pull/23636 "https://github.com/openai/codex/pull/23636"), [#23637](https://github.com/openai/codex/pull/23637 "https://github.com/openai/codex/pull/23637"), [#23638](https://github.com/openai/codex/pull/23638 "https://github.com/openai/codex/pull/23638"), [#23786](https://github.com/openai/codex/pull/23786 "https://github.com/openai/codex/pull/23786"))
- Fixed Linux Python runtime wheel tags so glibc-based systems can install the runtime artifacts. ([#21812](https://github.com/openai/codex/pull/21812 "https://github.com/openai/codex/pull/21812"))
- Improved release and CI reliability with package-builder tests, prebuilt resource packaging, DotSlash zstd handling, platform-sharded Rust tests, and Codex Linux release runners. ([#23760](https://github.com/openai/codex/pull/23760 "https://github.com/openai/codex/pull/23760"), [#23759](https://github.com/openai/codex/pull/23759 "https://github.com/openai/codex/pull/23759"), [#23752](https://github.com/openai/codex/pull/23752 "https://github.com/openai/codex/pull/23752"), [#23358](https://github.com/openai/codex/pull/23358 "https://github.com/openai/codex/pull/23358"), [#23761](https://github.com/openai/codex/pull/23761 "https://github.com/openai/codex/pull/23761"))

---

## Codex CLI 0.132.0 (2026-05-20)


  ### New Features

- The Python SDK now supports first-class authentication, including API key login, ChatGPT browser and device-code flows, account inspection, and logout APIs. ([#23093](https://github.com/openai/codex/pull/23093 "https://github.com/openai/codex/pull/23093"))
- Python turn APIs are easier to use for text-only workflows: you can pass a plain string as input, and handle-based runs now return a richer `TurnResult` with collected items, timing, and usage data. ([#23151](https://github.com/openai/codex/pull/23151 "https://github.com/openai/codex/pull/23151"), [#23162](https://github.com/openai/codex/pull/23162 "https://github.com/openai/codex/pull/23162"))
- `codex exec resume` now accepts `--output-schema`, so resumed automations can keep session context while still enforcing structured JSON output. ([#23123](https://github.com/openai/codex/pull/23123 "https://github.com/openai/codex/pull/23123"))
- TUI startup is faster because terminal capability probes are now batched instead of waiting on several serial checks before the first interactive frame. ([#23175](https://github.com/openai/codex/pull/23175 "https://github.com/openai/codex/pull/23175"))
- Remote executor registration can now use standard Codex auth instead of a separate registry credential flow. ([#22769](https://github.com/openai/codex/pull/22769 "https://github.com/openai/codex/pull/22769"))
- App-server turns can preserve requested image fidelity, including original-resolution local images, across user inputs and image-producing tools. ([#20693](https://github.com/openai/codex/pull/20693 "https://github.com/openai/codex/pull/20693"))

  ### Bug Fixes

- Goal continuations now stop when they hit usage limits or a repeated blocker instead of looping and burning more tokens, and completion responses phrase usage more naturally. ([#23094](https://github.com/openai/codex/pull/23094 "https://github.com/openai/codex/pull/23094"), [#22907](https://github.com/openai/codex/pull/22907 "https://github.com/openai/codex/pull/22907"))
- The session picker is easier to trust: renamed threads now show `name (thread-id)` in resume hints, and pasted text works in the picker search box. ([#23234](https://github.com/openai/codex/pull/23234 "https://github.com/openai/codex/pull/23234"), [#23338](https://github.com/openai/codex/pull/23338 "https://github.com/openai/codex/pull/23338"))
- Multi-session TUI flows are more reliable: in-progress MCP calls stay marked as active during replay, and elicitation replies are sent back to the thread that requested them. ([#23236](https://github.com/openai/codex/pull/23236 "https://github.com/openai/codex/pull/23236"), [#23241](https://github.com/openai/codex/pull/23241 "https://github.com/openai/codex/pull/23241"))
- Remote sessions now keep websocket connections alive and show repo-relative diff paths again instead of `/tmp/...`-prefixed paths. ([#23226](https://github.com/openai/codex/pull/23226 "https://github.com/openai/codex/pull/23226"), [#23261](https://github.com/openai/codex/pull/23261 "https://github.com/openai/codex/pull/23261"))
- Windows installs are more robust: `codex doctor` now detects npm-managed installs correctly, and MSVC release binaries no longer depend on separately installed VC++ runtime DLLs. ([#22967](https://github.com/openai/codex/pull/22967 "https://github.com/openai/codex/pull/22967"), [#22905](https://github.com/openai/codex/pull/22905 "https://github.com/openai/codex/pull/22905"))
- TUI polish fixes include immediate shutdown feedback on exit, hiding the ChatGPT usage link for non-OpenAI providers, and keeping a cleared Fast tier from reappearing after side-thread resume. ([#23323](https://github.com/openai/codex/pull/23323 "https://github.com/openai/codex/pull/23323"), [#23127](https://github.com/openai/codex/pull/23127 "https://github.com/openai/codex/pull/23127"), [#23121](https://github.com/openai/codex/pull/23121 "https://github.com/openai/codex/pull/23121"))

  ### Documentation

- The Python SDK docs, FAQ, and examples were refreshed around the new auth flow and turn APIs, with clearer setup guidance and simpler text-only examples. ([#22941](https://github.com/openai/codex/pull/22941 "https://github.com/openai/codex/pull/22941"), [#23093](https://github.com/openai/codex/pull/23093 "https://github.com/openai/codex/pull/23093"), [#23151](https://github.com/openai/codex/pull/23151 "https://github.com/openai/codex/pull/23151"), [#23162](https://github.com/openai/codex/pull/23162 "https://github.com/openai/codex/pull/23162"))

  ### Chores

- Memory summaries are now versioned and rebuilt when the stored format is stale, which should keep long-lived memory context leaner and more predictable. ([#23148](https://github.com/openai/codex/pull/23148 "https://github.com/openai/codex/pull/23148"))

---

## Codex CLI 0.131.0 (2026-05-18)


  ### New Features

- The TUI now offers richer session controls and display: data-driven service-tier commands, blended token usage, permissions/approval mode, effective workspace roots, and responsive Markdown tables. ([#21745](https://github.com/openai/codex/pull/21745 "https://github.com/openai/codex/pull/21745"), [#21906](https://github.com/openai/codex/pull/21906 "https://github.com/openai/codex/pull/21906"), [#21991](https://github.com/openai/codex/pull/21991 "https://github.com/openai/codex/pull/21991"), [#21669](https://github.com/openai/codex/pull/21669 "https://github.com/openai/codex/pull/21669"), [#21677](https://github.com/openai/codex/pull/21677 "https://github.com/openai/codex/pull/21677"), [#22052](https://github.com/openai/codex/pull/22052 "https://github.com/openai/codex/pull/22052"), [#22612](https://github.com/openai/codex/pull/22612 "https://github.com/openai/codex/pull/22612"))
- `@` mentions now search files, directories, plugins, and skills in one picker, backed by app-server plugin metadata. ([#19068](https://github.com/openai/codex/pull/19068 "https://github.com/openai/codex/pull/19068"), [#22375](https://github.com/openai/codex/pull/22375 "https://github.com/openai/codex/pull/22375"))
- Plugin workflows gained marketplace CLI commands, version-aware sharing, share checkout, clearer shared-workspace buckets, and default-enabled plugin hooks. ([#21396](https://github.com/openai/codex/pull/21396 "https://github.com/openai/codex/pull/21396"), [#22397](https://github.com/openai/codex/pull/22397 "https://github.com/openai/codex/pull/22397"), [#22425](https://github.com/openai/codex/pull/22425 "https://github.com/openai/codex/pull/22425"), [#22435](https://github.com/openai/codex/pull/22435 "https://github.com/openai/codex/pull/22435"), [#22549](https://github.com/openai/codex/pull/22549 "https://github.com/openai/codex/pull/22549"))
- Remote workflows now support daemon-managed `codex remote-control`, runtime enable/disable APIs, status reads, and registry-backed/configured remote environments. ([#20718](https://github.com/openai/codex/pull/20718 "https://github.com/openai/codex/pull/20718"), [#22218](https://github.com/openai/codex/pull/22218 "https://github.com/openai/codex/pull/22218"), [#22562](https://github.com/openai/codex/pull/22562 "https://github.com/openai/codex/pull/22562"), [#22578](https://github.com/openai/codex/pull/22578 "https://github.com/openai/codex/pull/22578"), [#22877](https://github.com/openai/codex/pull/22877 "https://github.com/openai/codex/pull/22877"), [#20667](https://github.com/openai/codex/pull/20667 "https://github.com/openai/codex/pull/20667"), [#21323](https://github.com/openai/codex/pull/21323 "https://github.com/openai/codex/pull/21323"))
- The Python SDK moved to `openai-codex` / `openai_codex`, with pinned runtime-generated types, concurrent turn routing, approval modes, and integration coverage. ([#21778](https://github.com/openai/codex/pull/21778 "https://github.com/openai/codex/pull/21778"), [#21891](https://github.com/openai/codex/pull/21891 "https://github.com/openai/codex/pull/21891"), [#21893](https://github.com/openai/codex/pull/21893 "https://github.com/openai/codex/pull/21893"), [#21896](https://github.com/openai/codex/pull/21896 "https://github.com/openai/codex/pull/21896"), [#21905](https://github.com/openai/codex/pull/21905 "https://github.com/openai/codex/pull/21905"), [#21910](https://github.com/openai/codex/pull/21910 "https://github.com/openai/codex/pull/21910"), [#22014](https://github.com/openai/codex/pull/22014 "https://github.com/openai/codex/pull/22014"))
- Added `codex doctor` for support-ready diagnostics across runtime, auth, terminal, network, config, and local state. ([#22336](https://github.com/openai/codex/pull/22336 "https://github.com/openai/codex/pull/22336"))

  ### Bug Fixes

- Fixed several TUI interaction and rendering issues, including URL wrapping, light-mode selection contrast, Shift+Enter in tmux, `/review` MCP startup status, `/side` Esc handling, and network approval history text. ([#21760](https://github.com/openai/codex/pull/21760 "https://github.com/openai/codex/pull/21760"), [#21950](https://github.com/openai/codex/pull/21950 "https://github.com/openai/codex/pull/21950"), [#21943](https://github.com/openai/codex/pull/21943 "https://github.com/openai/codex/pull/21943"), [#21624](https://github.com/openai/codex/pull/21624 "https://github.com/openai/codex/pull/21624"), [#22710](https://github.com/openai/codex/pull/22710 "https://github.com/openai/codex/pull/22710"), [#22229](https://github.com/openai/codex/pull/22229 "https://github.com/openai/codex/pull/22229"))
- Hardened Windows sandbox behavior around deny-read rules, scoped write roots, ineffective firewall policy, and PowerShell edge cases. ([#18202](https://github.com/openai/codex/pull/18202 "https://github.com/openai/codex/pull/18202"), [#21479](https://github.com/openai/codex/pull/21479 "https://github.com/openai/codex/pull/21479"), [#22353](https://github.com/openai/codex/pull/22353 "https://github.com/openai/codex/pull/22353"), [#21400](https://github.com/openai/codex/pull/21400 "https://github.com/openai/codex/pull/21400"), [#22643](https://github.com/openai/codex/pull/22643 "https://github.com/openai/codex/pull/22643"))
- Preserved managed read restrictions during permission escalation and cleaned up workspace-root permission profile resolution. ([#15977](https://github.com/openai/codex/pull/15977 "https://github.com/openai/codex/pull/15977"), [#22624](https://github.com/openai/codex/pull/22624 "https://github.com/openai/codex/pull/22624"), [#22683](https://github.com/openai/codex/pull/22683 "https://github.com/openai/codex/pull/22683"))
- Made app-server and local state startup safer by preserving SQLite data, failing closed when state cannot open, adding recovery paths, and softening optional metadata sync failures. ([#21831](https://github.com/openai/codex/pull/21831 "https://github.com/openai/codex/pull/21831"), [#21847](https://github.com/openai/codex/pull/21847 "https://github.com/openai/codex/pull/21847"), [#22580](https://github.com/openai/codex/pull/22580 "https://github.com/openai/codex/pull/22580"), [#22734](https://github.com/openai/codex/pull/22734 "https://github.com/openai/codex/pull/22734"), [#22899](https://github.com/openai/codex/pull/22899 "https://github.com/openai/codex/pull/22899"))
- Improved Git and auth reliability by using root worktree hooks consistently, ignoring repo hook/fsmonitor config in helper commands, binding local MCP OAuth callbacks, and revoking superseded login tokens. ([#21969](https://github.com/openai/codex/pull/21969 "https://github.com/openai/codex/pull/21969"), [#22843](https://github.com/openai/codex/pull/22843 "https://github.com/openai/codex/pull/22843"), [#22652](https://github.com/openai/codex/pull/22652 "https://github.com/openai/codex/pull/22652"), [#20237](https://github.com/openai/codex/pull/20237 "https://github.com/openai/codex/pull/20237"), [#21747](https://github.com/openai/codex/pull/21747 "https://github.com/openai/codex/pull/21747"))
- Reduced remote and Windows cleanup friction with longer exec-server transport timeouts, quieter `taskkill` cleanup, and non-queued plugin reads. ([#21825](https://github.com/openai/codex/pull/21825 "https://github.com/openai/codex/pull/21825"), [#21759](https://github.com/openai/codex/pull/21759 "https://github.com/openai/codex/pull/21759"), [#22058](https://github.com/openai/codex/pull/22058 "https://github.com/openai/codex/pull/22058"), [#22703](https://github.com/openai/codex/pull/22703 "https://github.com/openai/codex/pull/22703"))

  ### Documentation

- Clarified that general Codex product docs should not be added to this repo, while app-server API docs remain in scope. ([#21772](https://github.com/openai/codex/pull/21772 "https://github.com/openai/codex/pull/21772"))
- Updated plugin-creator guidance for the simplified local plugin handoff links. ([#22240](https://github.com/openai/codex/pull/22240 "https://github.com/openai/codex/pull/22240"))
- Documented new app-server/API contracts for remote environments and the desktop-owned config namespace. ([#21323](https://github.com/openai/codex/pull/21323 "https://github.com/openai/codex/pull/21323"), [#22584](https://github.com/openai/codex/pull/22584 "https://github.com/openai/codex/pull/22584"))

  ### Chores

- Improved CI and release reliability across Rust CI, exact PR-head checkout, Windows Bazel sharding, unsigned macOS artifacts, and signed macOS promotion. ([#21604](https://github.com/openai/codex/pull/21604 "https://github.com/openai/codex/pull/21604"), [#21628](https://github.com/openai/codex/pull/21628 "https://github.com/openai/codex/pull/21628"), [#21835](https://github.com/openai/codex/pull/21835 "https://github.com/openai/codex/pull/21835"), [#22408](https://github.com/openai/codex/pull/22408 "https://github.com/openai/codex/pull/22408"), [#22559](https://github.com/openai/codex/pull/22559 "https://github.com/openai/codex/pull/22559"), [#22649](https://github.com/openai/codex/pull/22649 "https://github.com/openai/codex/pull/22649"), [#22737](https://github.com/openai/codex/pull/22737 "https://github.com/openai/codex/pull/22737"), [#22788](https://github.com/openai/codex/pull/22788 "https://github.com/openai/codex/pull/22788"), [#22900](https://github.com/openai/codex/pull/22900 "https://github.com/openai/codex/pull/22900"))
- Split large TUI ChatWidget, history, and composer code into focused modules without intended behavior changes. ([#21866](https://github.com/openai/codex/pull/21866 "https://github.com/openai/codex/pull/21866"), [#22269](https://github.com/openai/codex/pull/22269 "https://github.com/openai/codex/pull/22269"), [#22407](https://github.com/openai/codex/pull/22407 "https://github.com/openai/codex/pull/22407"), [#22433](https://github.com/openai/codex/pull/22433 "https://github.com/openai/codex/pull/22433"), [#22518](https://github.com/openai/codex/pull/22518 "https://github.com/openai/codex/pull/22518"), [#22537](https://github.com/openai/codex/pull/22537 "https://github.com/openai/codex/pull/22537"), [#22704](https://github.com/openai/codex/pull/22704 "https://github.com/openai/codex/pull/22704"), [#22581](https://github.com/openai/codex/pull/22581 "https://github.com/openai/codex/pull/22581"), [#22656](https://github.com/openai/codex/pull/22656 "https://github.com/openai/codex/pull/22656"))
- Continued extracting extension and tool internals, including shared tool contracts plus guardian and memory extension plumbing. ([#21736](https://github.com/openai/codex/pull/21736 "https://github.com/openai/codex/pull/21736"), [#21737](https://github.com/openai/codex/pull/21737 "https://github.com/openai/codex/pull/21737"), [#21738](https://github.com/openai/codex/pull/21738 "https://github.com/openai/codex/pull/21738"), [#22138](https://github.com/openai/codex/pull/22138 "https://github.com/openai/codex/pull/22138"), [#22147](https://github.com/openai/codex/pull/22147 "https://github.com/openai/codex/pull/22147"), [#22216](https://github.com/openai/codex/pull/22216 "https://github.com/openai/codex/pull/22216"), [#22258](https://github.com/openai/codex/pull/22258 "https://github.com/openai/codex/pull/22258"), [#22344](https://github.com/openai/codex/pull/22344 "https://github.com/openai/codex/pull/22344"), [#22476](https://github.com/openai/codex/pull/22476 "https://github.com/openai/codex/pull/22476"), [#22480](https://github.com/openai/codex/pull/22480 "https://github.com/openai/codex/pull/22480"), [#22485](https://github.com/openai/codex/pull/22485 "https://github.com/openai/codex/pull/22485"), [#22498](https://github.com/openai/codex/pull/22498 "https://github.com/openai/codex/pull/22498"))
- Removed obsolete tool paths, feature flags, config gates, and legacy hooks as defaults stabilized. ([#21651](https://github.com/openai/codex/pull/21651 "https://github.com/openai/codex/pull/21651"), [#21805](https://github.com/openai/codex/pull/21805 "https://github.com/openai/codex/pull/21805"), [#22173](https://github.com/openai/codex/pull/22173 "https://github.com/openai/codex/pull/22173"), [#22246](https://github.com/openai/codex/pull/22246 "https://github.com/openai/codex/pull/22246"), [#22565](https://github.com/openai/codex/pull/22565 "https://github.com/openai/codex/pull/22565"), [#22711](https://github.com/openai/codex/pull/22711 "https://github.com/openai/codex/pull/22711"), [#22717](https://github.com/openai/codex/pull/22717 "https://github.com/openai/codex/pull/22717"), [#22724](https://github.com/openai/codex/pull/22724 "https://github.com/openai/codex/pull/22724"), [#22730](https://github.com/openai/codex/pull/22730 "https://github.com/openai/codex/pull/22730"))

---

## Work with Codex from anywhere (2026-05-14)

  You can now use Codex from the ChatGPT mobile app by connecting it to a Mac
  running the Codex app. Codex runs from the connected host, so the same projects,
  files, credentials, plugins, skills, and configuration are available from your
  phone.

  See [Remote connections](/codex/remote-connections "/codex/remote-connections") for mobile setup, choosing
  a host, what comes from the connected machine, and SSH hosts. This launch also
  includes [Hooks](/codex/hooks "/codex/hooks") general availability,
  [Codex access tokens](/codex/enterprise/access-tokens "/codex/enterprise/access-tokens") for trusted automation,
  and [Enterprise admin setup](/codex/enterprise/admin-setup "/codex/enterprise/admin-setup") guidance.

---

## Codex app 26.506 (2026-05-08)

  ### New features

- Added an in-app trust review flow for hooks and kept Hooks settings reachable even before hooks are fully configured.

  ### Performance improvements and bug fixes

- Restored tooltip-wrapped dropdowns that could stop opening after the tooltip rewrite.
- Preserved in-progress message edits across thread switches.
- Fixed several desktop workflow regressions, including `Ctrl+V` paste in the Windows terminal, opening modified external links outside the in-app browser, and keeping feedback slash commands attached to the right thread.
- Improved loading and panel polish by showing model loading while a thread resumes, hiding unavailable model controls during load, and bundling summary-panel layout and hover fixes.
- Kept the Computer Use settings control visible even when uninstalled and disabled problematic extension hover panels.
- Additional performance improvements and bug fixes.

---

## Codex CLI 0.130.0 (2026-05-08)


  ### New Features

- Plugin details now show bundled hooks, and plugin sharing exposes link metadata plus discoverability controls. ([#21447](https://github.com/openai/codex/pull/21447 "https://github.com/openai/codex/pull/21447"), [#21495](https://github.com/openai/codex/pull/21495 "https://github.com/openai/codex/pull/21495"), [#21637](https://github.com/openai/codex/pull/21637 "https://github.com/openai/codex/pull/21637"))
- Added `codex remote-control` as a simpler entrypoint for starting a headless, remotely controllable app-server. ([#21424](https://github.com/openai/codex/pull/21424 "https://github.com/openai/codex/pull/21424"))
- App-server clients can page large threads with unloaded, summary, or full turn item views. ([#21566](https://github.com/openai/codex/pull/21566 "https://github.com/openai/codex/pull/21566"))
- Bedrock auth can now use AWS console-login credentials from `aws login` profiles. ([#21623](https://github.com/openai/codex/pull/21623 "https://github.com/openai/codex/pull/21623"))
- `view_image` can resolve files through the selected environment for multi-environment sessions. ([#21143](https://github.com/openai/codex/pull/21143 "https://github.com/openai/codex/pull/21143"))

  ### Bug Fixes

- Live app-server threads now pick up config changes without requiring a restart. ([#21187](https://github.com/openai/codex/pull/21187 "https://github.com/openai/codex/pull/21187"))
- Turn diffs stay accurate across apply-patch operations, including partial failures that still mutated files. ([#21180](https://github.com/openai/codex/pull/21180 "https://github.com/openai/codex/pull/21180"), [#21518](https://github.com/openai/codex/pull/21518 "https://github.com/openai/codex/pull/21518"))
- Thread summaries, renames, resume, and fork paths work better through `ThreadStore`, including threads without local rollout paths. ([#21264](https://github.com/openai/codex/pull/21264 "https://github.com/openai/codex/pull/21264"), [#21265](https://github.com/openai/codex/pull/21265 "https://github.com/openai/codex/pull/21265"), [#21266](https://github.com/openai/codex/pull/21266 "https://github.com/openai/codex/pull/21266"))
- Remote compaction now emits `response.processed` for v2 streams and avoids sending `service_tier` on API-key compact requests. ([#21642](https://github.com/openai/codex/pull/21642 "https://github.com/openai/codex/pull/21642"), [#21676](https://github.com/openai/codex/pull/21676 "https://github.com/openai/codex/pull/21676"))
- Windows sandbox setup now grants sandbox users access to the desktop runtime binary cache. ([#21564](https://github.com/openai/codex/pull/21564 "https://github.com/openai/codex/pull/21564"))
- Removed stale “research preview” wording from the `codex exec` startup banner. ([#21683](https://github.com/openai/codex/pull/21683 "https://github.com/openai/codex/pull/21683"))

  ### Documentation

- Fixed issue templates so CLI reports keep the intended guidance, labels apply correctly, and feature requests link to the right contributing docs. ([#21685](https://github.com/openai/codex/pull/21685 "https://github.com/openai/codex/pull/21685"), [#21686](https://github.com/openai/codex/pull/21686 "https://github.com/openai/codex/pull/21686"), [#21688](https://github.com/openai/codex/pull/21688 "https://github.com/openai/codex/pull/21688"))
- Updated install and tooling docs to consistently use `cargo install --locked`. ([#21592](https://github.com/openai/codex/pull/21592 "https://github.com/openai/codex/pull/21592"))

  ### Chores

- Added a faster Cargo profiling build profile and disabled empty doctest targets to speed up Rust development loops. ([#21574](https://github.com/openai/codex/pull/21574 "https://github.com/openai/codex/pull/21574"), [#21584](https://github.com/openai/codex/pull/21584 "https://github.com/openai/codex/pull/21584"))
- Hardened dependency and CI hygiene with fully qualified GitHub Action pins, a Dependabot cooldown, and a `cargo-shear` upgrade. ([#21436](https://github.com/openai/codex/pull/21436 "https://github.com/openai/codex/pull/21436"), [#21547](https://github.com/openai/codex/pull/21547 "https://github.com/openai/codex/pull/21547"), [#21599](https://github.com/openai/codex/pull/21599 "https://github.com/openai/codex/pull/21599"))
- Simplified internal surfaces by removing unused device-key APIs, extra skills roots, the remote thread-store implementation, and string-keyed MCP tool maps. ([#21487](https://github.com/openai/codex/pull/21487 "https://github.com/openai/codex/pull/21487"), [#21485](https://github.com/openai/codex/pull/21485 "https://github.com/openai/codex/pull/21485"), [#21596](https://github.com/openai/codex/pull/21596 "https://github.com/openai/codex/pull/21596"), [#21454](https://github.com/openai/codex/pull/21454 "https://github.com/openai/codex/pull/21454"))
- Added configurable OpenTelemetry trace metadata and richer review/feedback analytics for better debugging and triage. ([#21556](https://github.com/openai/codex/pull/21556 "https://github.com/openai/codex/pull/21556"), [#18747](https://github.com/openai/codex/pull/18747 "https://github.com/openai/codex/pull/18747"), [#21434](https://github.com/openai/codex/pull/21434 "https://github.com/openai/codex/pull/21434"), [#21498](https://github.com/openai/codex/pull/21498 "https://github.com/openai/codex/pull/21498"))

---

## Codex CLI 0.129.0 (2026-05-07)


  ### New Features

- The TUI now supports modal Vim editing in the composer, including `/vim`, default-mode config, and Vim-specific keymap contexts. ([#18595](https://github.com/openai/codex/pull/18595 "https://github.com/openai/codex/pull/18595"))
- TUI workflows are easier to resume and copy from with a redesigned resume/fork picker, raw scrollback mode, `/ide` context injection, and workspace-aware `/diff`. ([#20065](https://github.com/openai/codex/pull/20065 "https://github.com/openai/codex/pull/20065"), [#20819](https://github.com/openai/codex/pull/20819 "https://github.com/openai/codex/pull/20819"), [#20294](https://github.com/openai/codex/pull/20294 "https://github.com/openai/codex/pull/20294"), [#21001](https://github.com/openai/codex/pull/21001 "https://github.com/openai/codex/pull/21001"))
- The status line can show theme-aware colors plus optional PR and branch-change summaries, and `/keymap debug` helps inspect terminal key events. ([#19631](https://github.com/openai/codex/pull/19631 "https://github.com/openai/codex/pull/19631"), [#20892](https://github.com/openai/codex/pull/20892 "https://github.com/openai/codex/pull/20892"), [#20794](https://github.com/openai/codex/pull/20794 "https://github.com/openai/codex/pull/20794"))
- Plugin management now supports workspace sharing, share access controls, source filtering, local share path tracking, marketplace removal/upgrades, remote bundle sync, and admin-disabled status handling. ([#20278](https://github.com/openai/codex/pull/20278 "https://github.com/openai/codex/pull/20278"), [#21124](https://github.com/openai/codex/pull/21124 "https://github.com/openai/codex/pull/21124"), [#21419](https://github.com/openai/codex/pull/21419 "https://github.com/openai/codex/pull/21419"), [#20560](https://github.com/openai/codex/pull/20560 "https://github.com/openai/codex/pull/20560"), [#19843](https://github.com/openai/codex/pull/19843 "https://github.com/openai/codex/pull/19843"), [#20478](https://github.com/openai/codex/pull/20478 "https://github.com/openai/codex/pull/20478"), [#20268](https://github.com/openai/codex/pull/20268 "https://github.com/openai/codex/pull/20268"), [#20298](https://github.com/openai/codex/pull/20298 "https://github.com/openai/codex/pull/20298"))
- Hooks can be browsed and toggled from `/hooks`, can run before/after compaction, and can add `PreToolUse` context; Codex Apps auth and eligible MCP elicitations now surface through TUI/Guardian flows. ([#19882](https://github.com/openai/codex/pull/19882 "https://github.com/openai/codex/pull/19882"), [#19905](https://github.com/openai/codex/pull/19905 "https://github.com/openai/codex/pull/19905"), [#20692](https://github.com/openai/codex/pull/20692 "https://github.com/openai/codex/pull/20692"), [#19193](https://github.com/openai/codex/pull/19193 "https://github.com/openai/codex/pull/19193"), [#19431](https://github.com/openai/codex/pull/19431 "https://github.com/openai/codex/pull/19431"))
- Experimental goals are now discoverable, stay paused across resume unless the user opts back in, and show clearer validation and multi-day duration output. ([#20083](https://github.com/openai/codex/pull/20083 "https://github.com/openai/codex/pull/20083"), [#20790](https://github.com/openai/codex/pull/20790 "https://github.com/openai/codex/pull/20790"), [#20746](https://github.com/openai/codex/pull/20746 "https://github.com/openai/codex/pull/20746"), [#20558](https://github.com/openai/codex/pull/20558 "https://github.com/openai/codex/pull/20558"))

  ### Bug Fixes

- `/copy` works better in tmux, Alt+Enter and modified Delete/Backspace keys behave correctly, and Windows typing/paste latency was reduced. ([#20207](https://github.com/openai/codex/pull/20207 "https://github.com/openai/codex/pull/20207"), [#20535](https://github.com/openai/codex/pull/20535 "https://github.com/openai/codex/pull/20535"), [#21058](https://github.com/openai/codex/pull/21058 "https://github.com/openai/codex/pull/21058"), [#18914](https://github.com/openai/codex/pull/18914 "https://github.com/openai/codex/pull/18914"))
- Large paste markers and Ctrl+C-stashed drafts now survive clear/editor workflows without corrupting draft history. ([#21091](https://github.com/openai/codex/pull/21091 "https://github.com/openai/codex/pull/21091"), [#21190](https://github.com/openai/codex/pull/21190 "https://github.com/openai/codex/pull/21190"), [#21351](https://github.com/openai/codex/pull/21351 "https://github.com/openai/codex/pull/21351"), [#21397](https://github.com/openai/codex/pull/21397 "https://github.com/openai/codex/pull/21397"))
- TUI startup and accessibility were tightened by bounding terminal probes, clearing the first inline viewport render, and honoring `animations = false` for live rows. ([#20654](https://github.com/openai/codex/pull/20654 "https://github.com/openai/codex/pull/20654"), [#21450](https://github.com/openai/codex/pull/21450 "https://github.com/openai/codex/pull/21450"), [#20564](https://github.com/openai/codex/pull/20564 "https://github.com/openai/codex/pull/20564"))
- Linux sandbox startup is more reliable across older `bwrap`, slow mount probes, symlink-protected paths, and shared `/tmp` setups. ([#20628](https://github.com/openai/codex/pull/20628 "https://github.com/openai/codex/pull/20628"), [#20111](https://github.com/openai/codex/pull/20111 "https://github.com/openai/codex/pull/20111"), [#21127](https://github.com/openai/codex/pull/21127 "https://github.com/openai/codex/pull/21127"), [#21234](https://github.com/openai/codex/pull/21234 "https://github.com/openai/codex/pull/21234"))
- Windows sandbox and exec policy now handle named pipes, ConPTY teardown, PowerShell-wrapped allow rules, worktree `safe.directory`, and unsafe Git options more reliably. ([#20270](https://github.com/openai/codex/pull/20270 "https://github.com/openai/codex/pull/20270"), [#20685](https://github.com/openai/codex/pull/20685 "https://github.com/openai/codex/pull/20685"), [#20336](https://github.com/openai/codex/pull/20336 "https://github.com/openai/codex/pull/20336"), [#21409](https://github.com/openai/codex/pull/21409 "https://github.com/openai/codex/pull/21409"), [#21275](https://github.com/openai/codex/pull/21275 "https://github.com/openai/codex/pull/21275"))
- Fixed custom CA login behind TLS-inspecting proxies, Bedrock runtime endpoint reporting, dangerous project config keys, heredoc redirect approval matching, and unbounded MCP/hook output growth. (#20676, [#20275](https://github.com/openai/codex/pull/20275 "https://github.com/openai/codex/pull/20275"), [#20098](https://github.com/openai/codex/pull/20098 "https://github.com/openai/codex/pull/20098"), [#20113](https://github.com/openai/codex/pull/20113 "https://github.com/openai/codex/pull/20113"), [#20260](https://github.com/openai/codex/pull/20260 "https://github.com/openai/codex/pull/20260"), [#21069](https://github.com/openai/codex/pull/21069 "https://github.com/openai/codex/pull/21069"))

  ### Documentation

- Updated the embedded OpenAI Docs sample skill so API-key setup guidance stays aligned with other docs variants. ([#21263](https://github.com/openai/codex/pull/21263 "https://github.com/openai/codex/pull/21263"))
- Documented how generated git commit attribution is gated by `codex_git_commit` and configured in `config.toml`. ([#21379](https://github.com/openai/codex/pull/21379 "https://github.com/openai/codex/pull/21379"))
- Removed local-only planning/spec docs and redirected config docs toward the maintained external documentation surface. ([#20896](https://github.com/openai/codex/pull/20896 "https://github.com/openai/codex/pull/20896"))

  ### Chores

- Linux releases now build, publish, bundle, and verify a standalone `bwrap` fallback for npm and DotSlash installs. ([#21255](https://github.com/openai/codex/pull/21255 "https://github.com/openai/codex/pull/21255"), [#21256](https://github.com/openai/codex/pull/21256 "https://github.com/openai/codex/pull/21256"), [#21257](https://github.com/openai/codex/pull/21257 "https://github.com/openai/codex/pull/21257"), [#21312](https://github.com/openai/codex/pull/21312 "https://github.com/openai/codex/pull/21312"), [#21285](https://github.com/openai/codex/pull/21285 "https://github.com/openai/codex/pull/21285"))
- Vendored Bubblewrap was updated to 0.11.2, including upstream security changes around setuid support. ([#21389](https://github.com/openai/codex/pull/21389 "https://github.com/openai/codex/pull/21389"))
- Windows Bazel CI now uses faster cross-compilation for tests, clippy, and release-build checks, and Bazel now runs sharded Rust integration tests. ([#20585](https://github.com/openai/codex/pull/20585 "https://github.com/openai/codex/pull/20585"), [#20701](https://github.com/openai/codex/pull/20701 "https://github.com/openai/codex/pull/20701"), [#21057](https://github.com/openai/codex/pull/21057 "https://github.com/openai/codex/pull/21057"))
- App-server and protocol internals were split and slimmed down, including transport extraction, protocol module decomposition, thread/message history moves, and tool-handler cleanup. ([#20324](https://github.com/openai/codex/pull/20324 "https://github.com/openai/codex/pull/20324"), [#20325](https://github.com/openai/codex/pull/20325 "https://github.com/openai/codex/pull/20325"), [#20348](https://github.com/openai/codex/pull/20348 "https://github.com/openai/codex/pull/20348"), [#20545](https://github.com/openai/codex/pull/20545 "https://github.com/openai/codex/pull/20545"), [#21251](https://github.com/openai/codex/pull/21251 "https://github.com/openai/codex/pull/21251"), [#21278](https://github.com/openai/codex/pull/21278 "https://github.com/openai/codex/pull/21278"), [#21395](https://github.com/openai/codex/pull/21395 "https://github.com/openai/codex/pull/21395"))
- Analytics and diagnostics coverage expanded for tool lifecycles, goals, plugin skills, thread sources, service tiers, and PR issue labeling. ([#17089](https://github.com/openai/codex/pull/17089 "https://github.com/openai/codex/pull/17089"), [#17090](https://github.com/openai/codex/pull/17090 "https://github.com/openai/codex/pull/17090"), [#20799](https://github.com/openai/codex/pull/20799 "https://github.com/openai/codex/pull/20799"), [#20923](https://github.com/openai/codex/pull/20923 "https://github.com/openai/codex/pull/20923"), [#20949](https://github.com/openai/codex/pull/20949 "https://github.com/openai/codex/pull/20949"), [#20969](https://github.com/openai/codex/pull/20969 "https://github.com/openai/codex/pull/20969"), [#20893](https://github.com/openai/codex/pull/20893 "https://github.com/openai/codex/pull/20893"))



- #20676 Fix custom CA login behind TLS-inspecting proxies [@jgershen-oai](https://github.com/jgershen-oai "https://github.com/jgershen-oai")

---

## Create Codex access tokens (2026-05-05)

  ChatGPT Enterprise workspace owners and admins can allow permitted members to
  create Codex access tokens for trusted, non-interactive Codex local workflows.
  Members can use access tokens to run Codex from scripts, schedulers, and private
  CI runners with their ChatGPT workspace identity.

  Learn more in [Access tokens](/codex/enterprise/access-tokens "/codex/enterprise/access-tokens").

---

## Codex app 26.429 (2026-05-05)

  ### New features

- Added dictation cleanup plus a configurable dictation dictionary for names, file paths, and code symbols.
- Added zoom and download controls to the image lightbox.

  ### Performance improvements and bug fixes

- Improved voice and dictation error messages for microphone, connection, and quota failures.
- Fixed in-app browser comment markers so they stay aligned across scrolling, zoom, and responsive layout changes.
- Made pull request creation and recovery flows more reliable by preserving newly created pull request state, classifying more app-server failures as restart-required, and stopping exhausted remote reconnect loops.
- Additional performance improvements and bug fixes.

## April 2026

---

## Codex CLI 0.128.0 (2026-04-30)


  ### New Features

- Added persisted `/goal` workflows with app-server APIs, model tools, runtime continuation, and TUI controls for create, pause, resume, and clear. ([#18073](https://github.com/openai/codex/pull/18073 "https://github.com/openai/codex/pull/18073"), [#18074](https://github.com/openai/codex/pull/18074 "https://github.com/openai/codex/pull/18074"), [#18075](https://github.com/openai/codex/pull/18075 "https://github.com/openai/codex/pull/18075"), [#18076](https://github.com/openai/codex/pull/18076 "https://github.com/openai/codex/pull/18076"), [#18077](https://github.com/openai/codex/pull/18077 "https://github.com/openai/codex/pull/18077"), [#20082](https://github.com/openai/codex/pull/20082 "https://github.com/openai/codex/pull/20082"))
- Added `codex update`, configurable TUI keymaps, plan-mode nudges, action-required terminal titles, and active-turn `/statusline` and `/title` edits. ([#19933](https://github.com/openai/codex/pull/19933 "https://github.com/openai/codex/pull/19933"), [#18593](https://github.com/openai/codex/pull/18593 "https://github.com/openai/codex/pull/18593"), [#19901](https://github.com/openai/codex/pull/19901 "https://github.com/openai/codex/pull/19901"), [#18372](https://github.com/openai/codex/pull/18372 "https://github.com/openai/codex/pull/18372"), [#19917](https://github.com/openai/codex/pull/19917 "https://github.com/openai/codex/pull/19917"))
- Expanded permission profiles with built-in defaults, sandbox CLI profile selection, cwd controls, and active-profile metadata for clients. ([#19900](https://github.com/openai/codex/pull/19900 "https://github.com/openai/codex/pull/19900"), [#20117](https://github.com/openai/codex/pull/20117 "https://github.com/openai/codex/pull/20117"), [#20118](https://github.com/openai/codex/pull/20118 "https://github.com/openai/codex/pull/20118"), [#20095](https://github.com/openai/codex/pull/20095 "https://github.com/openai/codex/pull/20095"))
- Improved plugin workflows with marketplace installation, remote bundle caching, remote uninstall, plugin-bundled hooks, hook enablement state, and external-agent config import. ([#18704](https://github.com/openai/codex/pull/18704 "https://github.com/openai/codex/pull/18704"), [#19914](https://github.com/openai/codex/pull/19914 "https://github.com/openai/codex/pull/19914"), [#19456](https://github.com/openai/codex/pull/19456 "https://github.com/openai/codex/pull/19456"), [#19705](https://github.com/openai/codex/pull/19705 "https://github.com/openai/codex/pull/19705"), [#19840](https://github.com/openai/codex/pull/19840 "https://github.com/openai/codex/pull/19840"), [#19949](https://github.com/openai/codex/pull/19949 "https://github.com/openai/codex/pull/19949"))
- Added external agent session import, including background imports and imported-session title handling. ([#19895](https://github.com/openai/codex/pull/19895 "https://github.com/openai/codex/pull/19895"), [#20284](https://github.com/openai/codex/pull/20284 "https://github.com/openai/codex/pull/20284"), [#20261](https://github.com/openai/codex/pull/20261 "https://github.com/openai/codex/pull/20261"))
- Made MultiAgentV2 configuration more explicit with thread caps, wait-time controls, root/subagent hints, and v2-specific depth handling. ([#19360](https://github.com/openai/codex/pull/19360 "https://github.com/openai/codex/pull/19360"), [#19792](https://github.com/openai/codex/pull/19792 "https://github.com/openai/codex/pull/19792"), [#19805](https://github.com/openai/codex/pull/19805 "https://github.com/openai/codex/pull/19805"), [#20052](https://github.com/openai/codex/pull/20052 "https://github.com/openai/codex/pull/20052"), [#20180](https://github.com/openai/codex/pull/20180 "https://github.com/openai/codex/pull/20180"))

  ### Bug Fixes

- Fixed several resume and interruption issues, including stale interrupt hangs, persisted provider restoration, large remote resume responses, and slow filtered resume lists. ([#18392](https://github.com/openai/codex/pull/18392 "https://github.com/openai/codex/pull/18392"), [#19287](https://github.com/openai/codex/pull/19287 "https://github.com/openai/codex/pull/19287"), [#19920](https://github.com/openai/codex/pull/19920 "https://github.com/openai/codex/pull/19920"), [#19591](https://github.com/openai/codex/pull/19591 "https://github.com/openai/codex/pull/19591"))
- Improved TUI reliability around terminal resize reflow, markdown list spacing, slash-command popup layout, keyboard cleanup, shell-mode escape, and working status updates. ([#18575](https://github.com/openai/codex/pull/18575 "https://github.com/openai/codex/pull/18575"), [#19706](https://github.com/openai/codex/pull/19706 "https://github.com/openai/codex/pull/19706"), [#19511](https://github.com/openai/codex/pull/19511 "https://github.com/openai/codex/pull/19511"), [#19625](https://github.com/openai/codex/pull/19625 "https://github.com/openai/codex/pull/19625"), [#19986](https://github.com/openai/codex/pull/19986 "https://github.com/openai/codex/pull/19986"), [#19939](https://github.com/openai/codex/pull/19939 "https://github.com/openai/codex/pull/19939"))
- Hardened managed network behavior for deferred denials, proxy bypass defaults, resolved target checks, IPv6 host matching, and `git -C` approval handling. ([#19184](https://github.com/openai/codex/pull/19184 "https://github.com/openai/codex/pull/19184"), [#20002](https://github.com/openai/codex/pull/20002 "https://github.com/openai/codex/pull/20002"), [#19999](https://github.com/openai/codex/pull/19999 "https://github.com/openai/codex/pull/19999"), [#19995](https://github.com/openai/codex/pull/19995 "https://github.com/openai/codex/pull/19995"), [#20085](https://github.com/openai/codex/pull/20085 "https://github.com/openai/codex/pull/20085"))
- Fixed Windows sandbox and PTY edge cases, including pseudoconsole startup, elevated runner process handling, core shell environment inheritance, and named-pipe validation. ([#20042](https://github.com/openai/codex/pull/20042 "https://github.com/openai/codex/pull/20042"), [#19211](https://github.com/openai/codex/pull/19211 "https://github.com/openai/codex/pull/19211"), [#20089](https://github.com/openai/codex/pull/20089 "https://github.com/openai/codex/pull/20089"), [#19283](https://github.com/openai/codex/pull/19283 "https://github.com/openai/codex/pull/19283"))
- Fixed Bedrock model support for `apply_patch`, GPT-5.4 reasoning levels, and updated Bedrock GPT-5.4 endpoint/model metadata. ([#19416](https://github.com/openai/codex/pull/19416 "https://github.com/openai/codex/pull/19416"), [#19461](https://github.com/openai/codex/pull/19461 "https://github.com/openai/codex/pull/19461"), [#20109](https://github.com/openai/codex/pull/20109 "https://github.com/openai/codex/pull/20109"))
- Fixed MCP/plugin edge cases around stdio server cleanup, plugin MCP approval persistence, and custom MCP metadata isolation. ([#19753](https://github.com/openai/codex/pull/19753 "https://github.com/openai/codex/pull/19753"), [#19537](https://github.com/openai/codex/pull/19537 "https://github.com/openai/codex/pull/19537"), [#19836](https://github.com/openai/codex/pull/19836 "https://github.com/openai/codex/pull/19836"), [#19875](https://github.com/openai/codex/pull/19875 "https://github.com/openai/codex/pull/19875"))

  ### Documentation

- Updated the bundled OpenAI Docs skill for GPT-5.5, `gpt-image-2`, and clearer upgrade guidance. ([#19407](https://github.com/openai/codex/pull/19407 "https://github.com/openai/codex/pull/19407"), [#19443](https://github.com/openai/codex/pull/19443 "https://github.com/openai/codex/pull/19443"), [#19422](https://github.com/openai/codex/pull/19422 "https://github.com/openai/codex/pull/19422"))
- Clarified contributor-facing docs, including the PR template, Rust async trait guidance, and README wording. ([#19912](https://github.com/openai/codex/pull/19912 "https://github.com/openai/codex/pull/19912"), [#20242](https://github.com/openai/codex/pull/20242 "https://github.com/openai/codex/pull/20242"), [#19514](https://github.com/openai/codex/pull/19514 "https://github.com/openai/codex/pull/19514"))
- Added a checked-in `codex-core` public API listing and a ThreadManager sample crate. ([#20243](https://github.com/openai/codex/pull/20243 "https://github.com/openai/codex/pull/20243"), [#20141](https://github.com/openai/codex/pull/20141 "https://github.com/openai/codex/pull/20141"))

  ### Chores

- Published `codex-app-server` release artifacts, stopped publishing GNU Linux binaries, and increased release workflow timeouts. ([#19447](https://github.com/openai/codex/pull/19447 "https://github.com/openai/codex/pull/19447"), [#19445](https://github.com/openai/codex/pull/19445 "https://github.com/openai/codex/pull/19445"), [#20271](https://github.com/openai/codex/pull/20271 "https://github.com/openai/codex/pull/20271"), [#20343](https://github.com/openai/codex/pull/20343 "https://github.com/openai/codex/pull/20343"))
- Added Codex-pinned versioning for the Python app-server SDK package. ([#18996](https://github.com/openai/codex/pull/18996 "https://github.com/openai/codex/pull/18996"))
- Deprecated `--full-auto` while steering users toward explicit permission profiles and trust flows. ([#20133](https://github.com/openai/codex/pull/20133 "https://github.com/openai/codex/pull/20133"))
- Stabilized CI and release plumbing with Bazel setup migration, release smoke-test pinning, and updated workflow pins/timeouts. ([#19851](https://github.com/openai/codex/pull/19851 "https://github.com/openai/codex/pull/19851"), [#19854](https://github.com/openai/codex/pull/19854 "https://github.com/openai/codex/pull/19854"), [#19472](https://github.com/openai/codex/pull/19472 "https://github.com/openai/codex/pull/19472"), [#19609](https://github.com/openai/codex/pull/19609 "https://github.com/openai/codex/pull/19609"))

---

## Codex app 26.423 (2026-04-24)

  ### New features

- Added a tooltip on realtime delegation messages to clarify that Codex uses the surrounding voice conversation as context.

  ### Performance improvements and bug fixes

- Fixed search in long review files so next and previous results reliably jump to off-screen matches.
- Kept embedded MCP app panels from restarting or losing state during fullscreen changes and thread reloads.
- Fixed several desktop regressions, including tray crashes when the local connection is missing, duplicate macOS fullscreen menu entries, and broken global dictation hotkeys on older macOS versions.
- Additional performance improvements and bug fixes.

---

## Codex CLI 0.125.0 (2026-04-24)


  ### New Features

- App-server integrations now support Unix socket transport, pagination-friendly resume/fork, sticky environments, and remote thread config/store plumbing. ([#18255](https://github.com/openai/codex/pull/18255 "https://github.com/openai/codex/pull/18255"), [#18892](https://github.com/openai/codex/pull/18892 "https://github.com/openai/codex/pull/18892"), [#18897](https://github.com/openai/codex/pull/18897 "https://github.com/openai/codex/pull/18897"), [#18908](https://github.com/openai/codex/pull/18908 "https://github.com/openai/codex/pull/18908"), [#19008](https://github.com/openai/codex/pull/19008 "https://github.com/openai/codex/pull/19008"), [#19014](https://github.com/openai/codex/pull/19014 "https://github.com/openai/codex/pull/19014"))
- App-server plugin management can install remote plugins and upgrade configured marketplaces. ([#18917](https://github.com/openai/codex/pull/18917 "https://github.com/openai/codex/pull/18917"), [#19074](https://github.com/openai/codex/pull/19074 "https://github.com/openai/codex/pull/19074"))
- Permission profiles now round-trip across TUI sessions, user turns, MCP sandbox state, shell escalation, and app-server APIs. ([#18284](https://github.com/openai/codex/pull/18284 "https://github.com/openai/codex/pull/18284"), [#18285](https://github.com/openai/codex/pull/18285 "https://github.com/openai/codex/pull/18285"), [#18286](https://github.com/openai/codex/pull/18286 "https://github.com/openai/codex/pull/18286"), [#18287](https://github.com/openai/codex/pull/18287 "https://github.com/openai/codex/pull/18287"), [#19231](https://github.com/openai/codex/pull/19231 "https://github.com/openai/codex/pull/19231"))
- Model providers now own model discovery, with AWS/Bedrock account state exposed to app clients. ([#18950](https://github.com/openai/codex/pull/18950 "https://github.com/openai/codex/pull/18950"), [#19048](https://github.com/openai/codex/pull/19048 "https://github.com/openai/codex/pull/19048"))
- `codex exec --json` now reports reasoning-token usage for programmatic consumers. ([#19308](https://github.com/openai/codex/pull/19308 "https://github.com/openai/codex/pull/19308"))
- Rollout tracing now records tool, code-mode, session, and multi-agent relationships, with a debug reducer command for inspection. ([#18878](https://github.com/openai/codex/pull/18878 "https://github.com/openai/codex/pull/18878"), [#18879](https://github.com/openai/codex/pull/18879 "https://github.com/openai/codex/pull/18879"), [#18880](https://github.com/openai/codex/pull/18880 "https://github.com/openai/codex/pull/18880"))

  ### Bug Fixes

- Interrupting `/review` and exiting the TUI no longer leaves the interface wedged on delegate startup or unsubscribe. ([#18921](https://github.com/openai/codex/pull/18921 "https://github.com/openai/codex/pull/18921"))
- Exec-server no longer drops buffered output after process exit and now waits correctly for stream closure. ([#18946](https://github.com/openai/codex/pull/18946 "https://github.com/openai/codex/pull/18946"), [#19130](https://github.com/openai/codex/pull/19130 "https://github.com/openai/codex/pull/19130"))
- App-server now respects explicitly untrusted project config instead of auto-persisting trust. ([#18626](https://github.com/openai/codex/pull/18626 "https://github.com/openai/codex/pull/18626"))
- WebSocket app-server clients are less likely to disconnect during bursts of turn and tool-output notifications. ([#19246](https://github.com/openai/codex/pull/19246 "https://github.com/openai/codex/pull/19246"))
- Windows sandbox startup handles multiple CLI versions and installed app directories better, and background `Start-Process` calls avoid visible PowerShell windows. ([#19044](https://github.com/openai/codex/pull/19044 "https://github.com/openai/codex/pull/19044"), [#19180](https://github.com/openai/codex/pull/19180 "https://github.com/openai/codex/pull/19180"), [#19214](https://github.com/openai/codex/pull/19214 "https://github.com/openai/codex/pull/19214"))
- Config/schema handling now rejects conflicting MultiAgentV2 thread limits, resolves relative agent-role config paths, hides unsupported MCP bearer-token fields, and rejects invalid `js_repl` image MIME types. ([#19129](https://github.com/openai/codex/pull/19129 "https://github.com/openai/codex/pull/19129"), [#19261](https://github.com/openai/codex/pull/19261 "https://github.com/openai/codex/pull/19261"), [#19294](https://github.com/openai/codex/pull/19294 "https://github.com/openai/codex/pull/19294"), [#19292](https://github.com/openai/codex/pull/19292 "https://github.com/openai/codex/pull/19292"))

  ### Documentation

- App-server docs and generated schemas were refreshed for the new transport, thread, marketplace, sticky environment, and permission-profile APIs. ([#18255](https://github.com/openai/codex/pull/18255 "https://github.com/openai/codex/pull/18255"), [#18897](https://github.com/openai/codex/pull/18897 "https://github.com/openai/codex/pull/18897"), [#19014](https://github.com/openai/codex/pull/19014 "https://github.com/openai/codex/pull/19014"), [#19074](https://github.com/openai/codex/pull/19074 "https://github.com/openai/codex/pull/19074"), [#19231](https://github.com/openai/codex/pull/19231 "https://github.com/openai/codex/pull/19231"))
- Rollout-trace documentation now covers the debug trace reduction workflow. ([#18880](https://github.com/openai/codex/pull/18880 "https://github.com/openai/codex/pull/18880"))

  ### Chores

- Refreshed `models.json` and related core, app-server, SDK, and TUI fixtures for the latest model catalog and reasoning defaults. ([#19323](https://github.com/openai/codex/pull/19323 "https://github.com/openai/codex/pull/19323"))
- Windows Bazel CI now uses a stable PATH and shared query startup path for better cache reuse. ([#19161](https://github.com/openai/codex/pull/19161 "https://github.com/openai/codex/pull/19161"), [#19232](https://github.com/openai/codex/pull/19232 "https://github.com/openai/codex/pull/19232"))
- Plugin marketplace add/remove/startup-sync internals moved out of `codex-core`, and curated plugin cache versions now use short SHAs. ([#19099](https://github.com/openai/codex/pull/19099 "https://github.com/openai/codex/pull/19099"), [#19095](https://github.com/openai/codex/pull/19095 "https://github.com/openai/codex/pull/19095"))
- Reverted a macOS signing entitlement change after it caused alpha startup failures. ([#19167](https://github.com/openai/codex/pull/19167 "https://github.com/openai/codex/pull/19167"), [#19350](https://github.com/openai/codex/pull/19350 "https://github.com/openai/codex/pull/19350"))
- Stabilized flaky approval-popup and plugin MCP tool-discovery tests. ([#19178](https://github.com/openai/codex/pull/19178 "https://github.com/openai/codex/pull/19178"), [#19191](https://github.com/openai/codex/pull/19191 "https://github.com/openai/codex/pull/19191"))

---

## GPT-5.5 and Codex app updates (2026-04-23)

  [GPT-5.5 is now available in Codex](https://openai.com/index/introducing-gpt-5-5/ "https://openai.com/index/introducing-gpt-5-5/")
  as OpenAI’s newest frontier model for complex coding, computer use, knowledge
  work, and research workflows.

  #### GPT-5.5 in Codex

  GPT-5.5 is the recommended choice for most Codex tasks when it appears in your
  model picker. It’s especially useful for implementation, refactors, debugging,
  testing, validation, and knowledge-work artifacts.

  To switch to GPT-5.5:

- In the CLI, start a new thread with:

    ```
    codex --model gpt-5.5
    ```

    Or use `/model` during a session.
- In the IDE extension, choose GPT-5.5 from the model selector in the composer.
- In the Codex app, choose GPT-5.5 from the model selector in the composer.

  If you don’t see GPT-5.5 yet, update the CLI, IDE extension, or Codex app to
  the latest version. During the rollout, continue using GPT-5.4 if GPT-5.5 is
  not yet available.

  #### Browser use in the Codex app

  The Codex app can now let Codex operate the in-app browser for local
  development servers and file-backed pages. Ask Codex to use the browser when it
  needs to click through a rendered UI, reproduce a visual bug, or verify a local
  fix inside the app.

  Browser use runs through the bundled Browser plugin. In settings, you can
  manage the plugin and review allowed or blocked websites.

  #### Automatic approval reviews

  Codex can route eligible approval prompts through an automatic reviewer agent
  before the request runs. When configured, the Codex app shows an automatic
  review item with the review status and risk level, so you can see whether the
  reviewer approved, denied, stopped, or timed out before deciding.

---

## Codex CLI 0.124.0 (2026-04-23)


  ### New Features

- The TUI now has quick reasoning controls: `Alt+,` lowers reasoning, `Alt+.` raises it, and accepted model upgrades now reset reasoning to the new model’s default instead of carrying over stale settings. ([#18866](https://github.com/openai/codex/pull/18866 "https://github.com/openai/codex/pull/18866"), [#19085](https://github.com/openai/codex/pull/19085 "https://github.com/openai/codex/pull/19085"))
- App-server sessions can now manage multiple environments and choose an environment and working directory per turn, which makes multi-workspace and remote setups easier to target precisely. ([#18401](https://github.com/openai/codex/pull/18401 "https://github.com/openai/codex/pull/18401"), [#18416](https://github.com/openai/codex/pull/18416 "https://github.com/openai/codex/pull/18416"))
- Added first-class Amazon Bedrock support for OpenAI-compatible providers, including AWS SigV4 signing and AWS credential-based auth. ([#17820](https://github.com/openai/codex/pull/17820 "https://github.com/openai/codex/pull/17820"))
- Remote plugin marketplaces can now be listed and read directly, with more reliable detail lookups and larger result pages. ([#18452](https://github.com/openai/codex/pull/18452 "https://github.com/openai/codex/pull/18452"), [#19079](https://github.com/openai/codex/pull/19079 "https://github.com/openai/codex/pull/19079"))
- Hooks are now stable, can be configured inline in `config.toml` and managed `requirements.toml`, and can observe MCP tools as well as `apply_patch` and long-running Bash sessions. ([#18893](https://github.com/openai/codex/pull/18893 "https://github.com/openai/codex/pull/18893"), [#18385](https://github.com/openai/codex/pull/18385 "https://github.com/openai/codex/pull/18385"), [#18391](https://github.com/openai/codex/pull/18391 "https://github.com/openai/codex/pull/18391"), [#18888](https://github.com/openai/codex/pull/18888 "https://github.com/openai/codex/pull/18888"), [#19012](https://github.com/openai/codex/pull/19012 "https://github.com/openai/codex/pull/19012"))
- Eligible ChatGPT plans now default to the Fast service tier unless you explicitly opt out. ([#19053](https://github.com/openai/codex/pull/19053 "https://github.com/openai/codex/pull/19053"))

  ### Bug Fixes

- Preserved Cloudflare cookies across approved ChatGPT hosts, reducing auth breakage in HTTP-backed ChatGPT flows. ([#17783](https://github.com/openai/codex/pull/17783 "https://github.com/openai/codex/pull/17783"))
- Fixed remote app-server reliability issues so websocket events keep draining under load and shutdown no longer fails when the remote worker exits during cleanup. ([#18932](https://github.com/openai/codex/pull/18932 "https://github.com/openai/codex/pull/18932"), [#18936](https://github.com/openai/codex/pull/18936 "https://github.com/openai/codex/pull/18936"))
- Fixed permission-mode drift so `/permissions` changes survive side conversations and updated Full Access state is correctly reflected in MCP approval handling. ([#18924](https://github.com/openai/codex/pull/18924 "https://github.com/openai/codex/pull/18924"), [#19033](https://github.com/openai/codex/pull/19033 "https://github.com/openai/codex/pull/19033"))
- Fixed `wait_agent` so it returns promptly when mailbox work is already queued instead of waiting for a fresh notification or timing out. ([#18968](https://github.com/openai/codex/pull/18968 "https://github.com/openai/codex/pull/18968"))
- Fixed local stdio MCP launches for relative commands without an explicit `cwd`, bringing fallback path resolution in line with CLI behavior. ([#19031](https://github.com/openai/codex/pull/19031 "https://github.com/openai/codex/pull/19031"))
- Startup now fails less often on managed config edge cases: unknown feature requirements warn instead of aborting, and cloud-requirements errors are clearer about what failed. ([#19038](https://github.com/openai/codex/pull/19038 "https://github.com/openai/codex/pull/19038"), [#19078](https://github.com/openai/codex/pull/19078 "https://github.com/openai/codex/pull/19078"))

---

## Codex CLI 0.123.0 (2026-04-23)


  ### New Features

- Added a built-in `amazon-bedrock` model provider with configurable AWS profile support ([#18744](https://github.com/openai/codex/pull/18744 "https://github.com/openai/codex/pull/18744")).
- Added `/mcp verbose` for full MCP server diagnostics, resources, and resource templates while keeping plain `/mcp` fast ([#18610](https://github.com/openai/codex/pull/18610 "https://github.com/openai/codex/pull/18610")).
- Made plugin MCP loading accept both `mcpServers` and top-level server maps in `.mcp.json` ([#18780](https://github.com/openai/codex/pull/18780 "https://github.com/openai/codex/pull/18780")).
- Improved realtime handoffs so background agents receive transcript deltas and can explicitly stay silent when appropriate ([#18597](https://github.com/openai/codex/pull/18597 "https://github.com/openai/codex/pull/18597"), [#18761](https://github.com/openai/codex/pull/18761 "https://github.com/openai/codex/pull/18761"), [#18635](https://github.com/openai/codex/pull/18635 "https://github.com/openai/codex/pull/18635")).
- Added host-specific `remote_sandbox_config` requirements for remote environments ([#18763](https://github.com/openai/codex/pull/18763 "https://github.com/openai/codex/pull/18763")).
- Refreshed bundled model metadata, including the current `gpt-5.4` default ([#18586](https://github.com/openai/codex/pull/18586 "https://github.com/openai/codex/pull/18586"), [#18388](https://github.com/openai/codex/pull/18388 "https://github.com/openai/codex/pull/18388"), [#18719](https://github.com/openai/codex/pull/18719 "https://github.com/openai/codex/pull/18719")).

  ### Bug Fixes

- Fixed `/copy` after rollback so it copies the latest visible assistant response, not a pre-rollback response ([#18739](https://github.com/openai/codex/pull/18739 "https://github.com/openai/codex/pull/18739")).
- Queued normal follow-up text submitted while a manual shell command is running, preventing stuck `Working` states ([#18820](https://github.com/openai/codex/pull/18820 "https://github.com/openai/codex/pull/18820")).
- Fixed Unicode/dead-key input in VS Code WSL terminals by disabling the enhanced keyboard mode there ([#18741](https://github.com/openai/codex/pull/18741 "https://github.com/openai/codex/pull/18741")).
- Prevented stale proxy environment variables from being restored from shell snapshots ([#17271](https://github.com/openai/codex/pull/17271 "https://github.com/openai/codex/pull/17271")).
- Made `codex exec` inherit root-level shared flags such as sandbox and model options ([#18630](https://github.com/openai/codex/pull/18630 "https://github.com/openai/codex/pull/18630")).
- Removed leaked review prompts from TUI transcripts ([#18659](https://github.com/openai/codex/pull/18659 "https://github.com/openai/codex/pull/18659")).

  ### Documentation

- Added and tightened the Code Review skill instructions used by Codex-driven reviews ([#18746](https://github.com/openai/codex/pull/18746 "https://github.com/openai/codex/pull/18746"), [#18818](https://github.com/openai/codex/pull/18818 "https://github.com/openai/codex/pull/18818")).
- Documented intentional await-across-lock cases and enabled Clippy linting for them ([#18423](https://github.com/openai/codex/pull/18423 "https://github.com/openai/codex/pull/18423"), [#18698](https://github.com/openai/codex/pull/18698 "https://github.com/openai/codex/pull/18698")).
- Updated app-server protocol docs for threadless MCP resource reads and namespaced dynamic tools ([#18292](https://github.com/openai/codex/pull/18292 "https://github.com/openai/codex/pull/18292"), [#18413](https://github.com/openai/codex/pull/18413 "https://github.com/openai/codex/pull/18413")).

  ### Chores

- Fixed high-severity dependency alerts by pinning patched JS and Rust dependencies ([#18167](https://github.com/openai/codex/pull/18167 "https://github.com/openai/codex/pull/18167")).
- Reduced Rust dev build debug-info overhead while preserving useful backtraces ([#18844](https://github.com/openai/codex/pull/18844 "https://github.com/openai/codex/pull/18844")).
- Refreshed generated Python app-server SDK types from the current schema ([#18862](https://github.com/openai/codex/pull/18862 "https://github.com/openai/codex/pull/18862")).

---

## Codex app 26.417 (2026-04-20)

  ### New features

- Added local branch search and non-image file pasting in the composer.
- Added collapsible sidebar sections, tray usage-limit surfacing, and a command-palette theme switcher.

  ### Performance improvements and bug fixes

- Made review faster and more stable with better diff batching and preserved diff and search state.
- Fixed projectless cwd and permissions handling, default file opening, spreadsheet suggestions, and remote-control reconnect issues.
- Additional performance improvements and bug fixes.

---

## Codex CLI 0.122.0 (2026-04-20)


  ### New Features

- Standalone installs are more self-contained, and `codex app` now opens or installs Desktop correctly on Windows and Intel Macs ([#17022](https://github.com/openai/codex/pull/17022 "https://github.com/openai/codex/pull/17022"), [#18500](https://github.com/openai/codex/pull/18500 "https://github.com/openai/codex/pull/18500")).
- The TUI can open `/side` conversations for quick side questions, and queued input now supports slash commands and `!` shell prompts while work is running ([#18190](https://github.com/openai/codex/pull/18190 "https://github.com/openai/codex/pull/18190"), [#18542](https://github.com/openai/codex/pull/18542 "https://github.com/openai/codex/pull/18542")).
- Plan Mode can start implementation in a fresh context, with context-usage shown before deciding whether to carry the planning thread forward ([#17499](https://github.com/openai/codex/pull/17499 "https://github.com/openai/codex/pull/17499"), [#18573](https://github.com/openai/codex/pull/18573 "https://github.com/openai/codex/pull/18573")).
- Plugin workflows now include tabbed browsing, inline enable/disable toggles, marketplace removal, and remote, cross-repo, or local marketplace sources ([#18222](https://github.com/openai/codex/pull/18222 "https://github.com/openai/codex/pull/18222"), [#18395](https://github.com/openai/codex/pull/18395 "https://github.com/openai/codex/pull/18395"), [#17752](https://github.com/openai/codex/pull/17752 "https://github.com/openai/codex/pull/17752"), [#17751](https://github.com/openai/codex/pull/17751 "https://github.com/openai/codex/pull/17751"), [#17277](https://github.com/openai/codex/pull/17277 "https://github.com/openai/codex/pull/17277"), [#18017](https://github.com/openai/codex/pull/18017 "https://github.com/openai/codex/pull/18017"), [#18246](https://github.com/openai/codex/pull/18246 "https://github.com/openai/codex/pull/18246")).
- Filesystem permissions now support deny-read glob policies, managed deny-read requirements, platform sandbox enforcement, and isolated `codex exec` runs that ignore user config or rules ([#15979](https://github.com/openai/codex/pull/15979 "https://github.com/openai/codex/pull/15979"), [#17740](https://github.com/openai/codex/pull/17740 "https://github.com/openai/codex/pull/17740"), [#18096](https://github.com/openai/codex/pull/18096 "https://github.com/openai/codex/pull/18096"), [#18646](https://github.com/openai/codex/pull/18646 "https://github.com/openai/codex/pull/18646")).
- Tool discovery and image generation are now enabled by default, with higher-detail image handling and original-detail metadata support for MCP and `js_repl` image outputs ([#17854](https://github.com/openai/codex/pull/17854 "https://github.com/openai/codex/pull/17854"), [#17153](https://github.com/openai/codex/pull/17153 "https://github.com/openai/codex/pull/17153"), [#17714](https://github.com/openai/codex/pull/17714 "https://github.com/openai/codex/pull/17714"), [#18386](https://github.com/openai/codex/pull/18386 "https://github.com/openai/codex/pull/18386")).

  ### Bug Fixes

- App-server approvals, user-input prompts, and MCP elicitations now disappear from the TUI when another client resolves them, instead of leaving stale prompts behind ([#15134](https://github.com/openai/codex/pull/15134 "https://github.com/openai/codex/pull/15134")).
- Remote-control startup now tolerates missing ChatGPT auth, and MCP startup cancellation works again through app-server sessions ([#18117](https://github.com/openai/codex/pull/18117 "https://github.com/openai/codex/pull/18117"), [#18078](https://github.com/openai/codex/pull/18078 "https://github.com/openai/codex/pull/18078")).
- Resumed and forked app-server threads now replay token usage immediately so context/status UI starts with the restored state ([#18023](https://github.com/openai/codex/pull/18023 "https://github.com/openai/codex/pull/18023")).
- Security-sensitive flows were tightened: logout revokes managed ChatGPT tokens, project hooks and exec policies require trusted workspaces, and Windows sandbox setup avoids broad user-profile and SSH-root grants ([#17825](https://github.com/openai/codex/pull/17825 "https://github.com/openai/codex/pull/17825"), [#14718](https://github.com/openai/codex/pull/14718 "https://github.com/openai/codex/pull/14718"), [#18443](https://github.com/openai/codex/pull/18443 "https://github.com/openai/codex/pull/18443"), [#18493](https://github.com/openai/codex/pull/18493 "https://github.com/openai/codex/pull/18493")).
- Sandboxed `apply_patch` writes work correctly with split filesystem policies, and file watchers now notice files created after watching begins ([#18296](https://github.com/openai/codex/pull/18296 "https://github.com/openai/codex/pull/18296"), [#18492](https://github.com/openai/codex/pull/18492 "https://github.com/openai/codex/pull/18492")).
- Several TUI rough edges were fixed, including fatal skills-list failures, invalid resume hints, duplicate context statusline entries, `/model` menu loops, redundant memory notices, and terminal title quoting in iTerm2 ([#18061](https://github.com/openai/codex/pull/18061 "https://github.com/openai/codex/pull/18061"), [#18059](https://github.com/openai/codex/pull/18059 "https://github.com/openai/codex/pull/18059"), [#18054](https://github.com/openai/codex/pull/18054 "https://github.com/openai/codex/pull/18054"), [#18154](https://github.com/openai/codex/pull/18154 "https://github.com/openai/codex/pull/18154"), [#18580](https://github.com/openai/codex/pull/18580 "https://github.com/openai/codex/pull/18580"), [#18261](https://github.com/openai/codex/pull/18261 "https://github.com/openai/codex/pull/18261")).

  ### Documentation

- Added a security-boundaries reference to `SECURITY.md` for sandboxing, approvals, and network controls ([#17848](https://github.com/openai/codex/pull/17848 "https://github.com/openai/codex/pull/17848"), [#18004](https://github.com/openai/codex/pull/18004 "https://github.com/openai/codex/pull/18004")).
- Documented custom MCP server approval defaults and exec-server stdin behavior ([#17843](https://github.com/openai/codex/pull/17843 "https://github.com/openai/codex/pull/17843"), [#18086](https://github.com/openai/codex/pull/18086 "https://github.com/openai/codex/pull/18086")).
- Updated app-server docs for plugin API changes, marketplace removal, resume/fork token-usage replay, and warning notifications ([#17277](https://github.com/openai/codex/pull/17277 "https://github.com/openai/codex/pull/17277"), [#17751](https://github.com/openai/codex/pull/17751 "https://github.com/openai/codex/pull/17751"), [#18023](https://github.com/openai/codex/pull/18023 "https://github.com/openai/codex/pull/18023"), [#18298](https://github.com/openai/codex/pull/18298 "https://github.com/openai/codex/pull/18298")).
- Added a short guide for the responses API proxy ([#18604](https://github.com/openai/codex/pull/18604 "https://github.com/openai/codex/pull/18604")).

  ### Chores

- Split plugin and marketplace code into `codex-core-plugins`, moved more connector code into `connectors`, and continued breaking up the large core session/turn modules ([#18070](https://github.com/openai/codex/pull/18070 "https://github.com/openai/codex/pull/18070"), [#18158](https://github.com/openai/codex/pull/18158 "https://github.com/openai/codex/pull/18158"), [#18200](https://github.com/openai/codex/pull/18200 "https://github.com/openai/codex/pull/18200"), [#18206](https://github.com/openai/codex/pull/18206 "https://github.com/openai/codex/pull/18206"), [#18244](https://github.com/openai/codex/pull/18244 "https://github.com/openai/codex/pull/18244"), [#18249](https://github.com/openai/codex/pull/18249 "https://github.com/openai/codex/pull/18249")).
- Refactored config loading and `AGENTS.md` discovery behind narrower filesystem and manager abstractions ([#18209](https://github.com/openai/codex/pull/18209 "https://github.com/openai/codex/pull/18209"), [#18035](https://github.com/openai/codex/pull/18035 "https://github.com/openai/codex/pull/18035")).
- Stabilized Bazel and CI with flake fixes, native Rust test sharding, scoped repository caches, stronger Windows clippy coverage, and updated `rules_rs`/LLVM pins ([#17791](https://github.com/openai/codex/pull/17791 "https://github.com/openai/codex/pull/17791"), [#18082](https://github.com/openai/codex/pull/18082 "https://github.com/openai/codex/pull/18082"), [#18366](https://github.com/openai/codex/pull/18366 "https://github.com/openai/codex/pull/18366"), [#18350](https://github.com/openai/codex/pull/18350 "https://github.com/openai/codex/pull/18350"), [#18397](https://github.com/openai/codex/pull/18397 "https://github.com/openai/codex/pull/18397")).
- Added core CODEOWNERS and a smaller development build profile ([#18362](https://github.com/openai/codex/pull/18362 "https://github.com/openai/codex/pull/18362"), [#18612](https://github.com/openai/codex/pull/18612 "https://github.com/openai/codex/pull/18612")).
- Removed the stale core `models.json` and updated release preparation to refresh the active model catalog ([#18585](https://github.com/openai/codex/pull/18585 "https://github.com/openai/codex/pull/18585")).

---

## Codex can now help with more of your work 26.415 (2026-04-16)

  Codex is becoming a broader workspace for getting work done with AI. This
  update makes it easier to start work with less setup, verify what Codex is
  building, create richer outputs, and keep momentum across longer-running tasks.

  #### Verify more of your work

  The Codex app now includes an early [**in-app browser**](/codex/app/browser "/codex/app/browser"). You
  can open local or public pages that don’t require sign-in, comment directly on
  the rendered page, and ask Codex to address page-level feedback.

  ![Codex app showing a browser comment on a local web app preview](/images/codex/app/in-app-browser-light.webp) ![Codex app showing a browser comment on a local web app preview](/images/codex/app/in-app-browser-dark.webp)

  ![Codex app showing a browser comment on a local web app preview](/images/codex/app/in-app-browser-light.webp) ![Codex app showing a browser comment on a local web app preview](/images/codex/app/in-app-browser-dark.webp)



  [**Computer use**](/codex/app/computer-use "/codex/app/computer-use") lets Codex operate macOS apps by seeing,
  clicking, and typing, which helps with native app testing, simulator flows,
  low-risk app settings, and GUI-only bugs.

  The feature isn’t available in the European Economic Area, the United Kingdom, or
  Switzerland at launch.

  #### Start, follow, and steer work

  [**Chats**](/codex/app/features#projectless-threads "/codex/app/features#projectless-threads") are threads you can start
  without choosing a project folder first. They’re useful for research, writing,
  planning, analysis, source gathering, and tool-driven work that doesn’t begin in
  a codebase.

  For work that needs a later check-in,
  [**thread automations**](/codex/app/automations#thread-automations "/codex/app/automations#thread-automations") can wake up
  the same thread on a schedule while preserving the conversation context. Use
  them to check a long-running process, watch for updates, or continue a
  follow-up loop without starting from scratch.

  [**The task sidebar**](/codex/app/features#task-sidebar "/codex/app/features#task-sidebar") makes plans, sources,
  generated artifacts, and summaries easier to follow while Codex works.
  [**Context-aware suggestions**](/codex/app/settings#context-aware-suggestions "/codex/app/settings#context-aware-suggestions")
  can also help you pick up relevant follow-ups when you start or return to Codex.

  #### Stronger for software development

  Codex now brings more of the **pull request workflow** into the app. You can
  inspect [**GitHub pull requests**](/codex/app/review#pull-request-reviews "/codex/app/review#pull-request-reviews") in the
  sidebar, review comments in the diff, review changed files, then ask Codex to
  explain feedback, make changes, check them, and keep the review moving.

  #### Review richer outputs

  The [**artifact viewer**](/codex/app/features#artifact-viewer "/codex/app/features#artifact-viewer") can preview
  generated files such as PDF files, spreadsheets, documents, and presentations in
  the sidebar before you commit or share them. [**Memories**](/codex/memories "/codex/memories"),
  where available, can also carry useful context from past tasks into future
  threads, including stable preferences, project conventions, and recurring work
  patterns.

  #### Other features

- [Remote connections](/codex/remote-connections "/codex/remote-connections") - We are gradually rolling out SSH remote connections in alpha
- Support for [multiple terminals](/codex/app/features#integrated-terminal "/codex/app/features#integrated-terminal")
- macOS menu bar and [Windows system tray](/codex/app/windows "/codex/app/windows") support
- [Multi-window support](/codex/app/features#floating-pop-out-window "/codex/app/features#floating-pop-out-window")
- [Intel Mac support](/codex/app "/codex/app")
- [New plugins](/codex/plugins "/codex/plugins")
- Improved thread and tool rendering

---

## Codex CLI 0.121.0 (2026-04-15)


  ### New Features

- Added `codex marketplace add` and app-server support for installing plugin marketplaces from GitHub, git URLs, local directories, and direct `marketplace.json` URLs ([#17087](https://github.com/openai/codex/pull/17087 "https://github.com/openai/codex/pull/17087"), [#17717](https://github.com/openai/codex/pull/17717 "https://github.com/openai/codex/pull/17717"), [#17756](https://github.com/openai/codex/pull/17756 "https://github.com/openai/codex/pull/17756")).
- Added TUI prompt history improvements, including `Ctrl+R` reverse search and local recall for accepted slash commands ([#17550](https://github.com/openai/codex/pull/17550 "https://github.com/openai/codex/pull/17550"), [#17336](https://github.com/openai/codex/pull/17336 "https://github.com/openai/codex/pull/17336")).
- Added TUI and app-server controls for memory mode, memory reset/deletion, and memory-extension cleanup ([#17632](https://github.com/openai/codex/pull/17632 "https://github.com/openai/codex/pull/17632"), [#17626](https://github.com/openai/codex/pull/17626 "https://github.com/openai/codex/pull/17626"), [#17913](https://github.com/openai/codex/pull/17913 "https://github.com/openai/codex/pull/17913"), [#17937](https://github.com/openai/codex/pull/17937 "https://github.com/openai/codex/pull/17937"), [#17844](https://github.com/openai/codex/pull/17844 "https://github.com/openai/codex/pull/17844")).
- Expanded MCP/plugin support with MCP Apps tool calls, namespaced MCP registration, parallel-call opt-in, and sandbox-state metadata for MCP servers ([#17364](https://github.com/openai/codex/pull/17364 "https://github.com/openai/codex/pull/17364"), [#17404](https://github.com/openai/codex/pull/17404 "https://github.com/openai/codex/pull/17404"), [#17667](https://github.com/openai/codex/pull/17667 "https://github.com/openai/codex/pull/17667"), [#17763](https://github.com/openai/codex/pull/17763 "https://github.com/openai/codex/pull/17763")).
- Added realtime and app-server APIs for output modality, transcript completion events, raw turn item injection, and symlink-aware filesystem metadata ([#17701](https://github.com/openai/codex/pull/17701 "https://github.com/openai/codex/pull/17701"), [#17703](https://github.com/openai/codex/pull/17703 "https://github.com/openai/codex/pull/17703"), [#17719](https://github.com/openai/codex/pull/17719 "https://github.com/openai/codex/pull/17719")).
- Added a secure devcontainer profile with bubblewrap support, plus macOS sandbox allowlists for Unix sockets ([#10431](https://github.com/openai/codex/pull/10431 "https://github.com/openai/codex/pull/10431"), [#17547](https://github.com/openai/codex/pull/17547 "https://github.com/openai/codex/pull/17547"), [#17654](https://github.com/openai/codex/pull/17654 "https://github.com/openai/codex/pull/17654")).

  ### Bug Fixes

- Fixed macOS sandbox/proxy handling for private DNS and removed the `danger-full-access` denylist-only network mode ([#17370](https://github.com/openai/codex/pull/17370 "https://github.com/openai/codex/pull/17370"), [#17732](https://github.com/openai/codex/pull/17732 "https://github.com/openai/codex/pull/17732")).
- Fixed Windows cwd/session matching so `resume --last` and `thread/list` work when paths use verbatim prefixes ([#17414](https://github.com/openai/codex/pull/17414 "https://github.com/openai/codex/pull/17414")).
- Fixed rate-limit/account handling for `prolite` plans and made unknown WHAM plan values decodable ([#17419](https://github.com/openai/codex/pull/17419 "https://github.com/openai/codex/pull/17419")).
- Made Guardian timeouts distinct from policy denials, with timeout-specific guidance and visible TUI history entries ([#17381](https://github.com/openai/codex/pull/17381 "https://github.com/openai/codex/pull/17381"), [#17486](https://github.com/openai/codex/pull/17486 "https://github.com/openai/codex/pull/17486"), [#17521](https://github.com/openai/codex/pull/17521 "https://github.com/openai/codex/pull/17521"), [#17557](https://github.com/openai/codex/pull/17557 "https://github.com/openai/codex/pull/17557")).
- Stabilized app-server behavior by avoiding premature thread unloads, tolerating failed trust persistence on startup, and skipping broken symlinks in `fs/readDirectory` ([#17398](https://github.com/openai/codex/pull/17398 "https://github.com/openai/codex/pull/17398"), [#17595](https://github.com/openai/codex/pull/17595 "https://github.com/openai/codex/pull/17595"), [#17907](https://github.com/openai/codex/pull/17907 "https://github.com/openai/codex/pull/17907")).
- Fixed MCP/tool-call edge cases including flattened deferred tool names, elicitation timeout accounting, and empty namespace descriptions ([#17556](https://github.com/openai/codex/pull/17556 "https://github.com/openai/codex/pull/17556"), [#17566](https://github.com/openai/codex/pull/17566 "https://github.com/openai/codex/pull/17566"), [#17946](https://github.com/openai/codex/pull/17946 "https://github.com/openai/codex/pull/17946")).

  ### Documentation

- Documented the secure devcontainer profile and its bubblewrap requirements ([#10431](https://github.com/openai/codex/pull/10431 "https://github.com/openai/codex/pull/10431"), [#17547](https://github.com/openai/codex/pull/17547 "https://github.com/openai/codex/pull/17547")).
- Added TUI composer documentation for history search behavior ([#17550](https://github.com/openai/codex/pull/17550 "https://github.com/openai/codex/pull/17550")).
- Updated app-server docs for new MCP, marketplace, turn injection, memory reset, filesystem metadata, external-agent migration, and websocket token-hash APIs ([#17364](https://github.com/openai/codex/pull/17364 "https://github.com/openai/codex/pull/17364"), [#17717](https://github.com/openai/codex/pull/17717 "https://github.com/openai/codex/pull/17717"), [#17703](https://github.com/openai/codex/pull/17703 "https://github.com/openai/codex/pull/17703"), [#17913](https://github.com/openai/codex/pull/17913 "https://github.com/openai/codex/pull/17913"), [#17719](https://github.com/openai/codex/pull/17719 "https://github.com/openai/codex/pull/17719"), [#17855](https://github.com/openai/codex/pull/17855 "https://github.com/openai/codex/pull/17855"), [#17871](https://github.com/openai/codex/pull/17871 "https://github.com/openai/codex/pull/17871")).
- Documented WSL1 bubblewrap limitations and WSL2 behavior ([#17559](https://github.com/openai/codex/pull/17559 "https://github.com/openai/codex/pull/17559")).
- Added memory pipeline documentation for extension cleanup ([#17844](https://github.com/openai/codex/pull/17844 "https://github.com/openai/codex/pull/17844")).

  ### Chores

- Hardened supply-chain and CI inputs by pinning GitHub Actions, cargo installs, git dependencies, V8 checksums, and cargo-deny source allowlists ([#17471](https://github.com/openai/codex/pull/17471 "https://github.com/openai/codex/pull/17471")).
- Added Bazel release-build verification so release-only Rust code is compiled in PR CI ([#17704](https://github.com/openai/codex/pull/17704 "https://github.com/openai/codex/pull/17704"), [#17705](https://github.com/openai/codex/pull/17705 "https://github.com/openai/codex/pull/17705")).
- Introduced the `codex-thread-store` crate/interface and moved local thread listing behind it ([#17659](https://github.com/openai/codex/pull/17659 "https://github.com/openai/codex/pull/17659"), [#17824](https://github.com/openai/codex/pull/17824 "https://github.com/openai/codex/pull/17824")).
- Required reviewed pnpm dependency build scripts for workspace installs ([#17558](https://github.com/openai/codex/pull/17558 "https://github.com/openai/codex/pull/17558")).
- Reduced Rust maintenance surface with broader absolute-path types and removal of unused helper APIs ([#17407](https://github.com/openai/codex/pull/17407 "https://github.com/openai/codex/pull/17407"), [#17792](https://github.com/openai/codex/pull/17792 "https://github.com/openai/codex/pull/17792"), [#17146](https://github.com/openai/codex/pull/17146 "https://github.com/openai/codex/pull/17146")).

---

## Codex app 26.410 (2026-04-12)

  ### New features

- Added command-menu file search, including `Cmd+P` routing into workspace file search.
- Added rich previews in the sidebar file viewer for images, PDFs, and Markdown.
- Added terminal tabs per thread, a selected-text Ask Codex overlay, and a Help menu feedback entry.

  ### Performance improvements and bug fixes

- Improved review diff whitespace handling and search highlighting.
- Fixed in-app browser address bar and external-open issues, plus several file viewer and side-panel bugs.
- Additional performance improvements and bug fixes.

---

## Codex app 26.409 (2026-04-10)

  ### New features

- Added Windows Store updater support.
- Expanded pull request workflows with an activity timeline, PR-page commenting, and push choices in the push modal.
- Added workspace file tabs in the thread side panel, drag-and-drop tab reordering, run action editing, and a logout confirmation dialog.

  ### Performance improvements and bug fixes

- Improved pull request board performance and comment flyouts.
- Improved update and navigation resilience, and fixed projectless visibility, unread-state, and pinned-row edge cases.
- Additional performance improvements and bug fixes.

---

## Codex app 26.406 (2026-04-09)

  ### New features

- Added collapsible inline review comments and inline or detached review modes.
- Added a Git summary and Sources section in the thread side panel.
- Added a New Quick Chat command and local video embeds in the app.

  ### Performance improvements and bug fixes

- Preserved thread scroll position per conversation and unread state across windows.
- Improved review refresh reliability, and fixed dictation loss, right-panel reset, and GitHub reconnect messaging.
- Additional performance improvements and bug fixes.

---

## Codex model availability update (2026-04-07)

  We’re updating model availability for users who sign in with ChatGPT. Starting
  April 7, the model picker no longer shows `gpt-5.2-codex`,
  `gpt-5.1-codex-mini`, `gpt-5.1-codex-max`, `gpt-5.1-codex`, `gpt-5.1`, or
  `gpt-5`. On April 14, we’ll remove those models from Codex for ChatGPT sign-in.

  Users can still choose from `gpt-5.4`, `gpt-5.4-mini`, `gpt-5.3-codex`, and
  `gpt-5.2`. ChatGPT Pro users can also choose `gpt-5.3-codex-spark`.

  To use another API-supported model in Codex, sign in with an API key or
  configure a model provider.

---

## Codex app 26.325, 26.331, 26.401 (2026-04-01)

  ### New features

- Added workspace settings to the app.
- Added “Don’t ask again” handling and polish for custom MCP approval panels.
- Added native Windows updater support, including MSIX support, plus a Windows system tray menu so Codex can stay resident after the last window closes.
- Added app and file `@` mentions in the automation composer, surfaced subagent diff stats in the composer, and added artifact cards for generated file citations.
- Added a Quick Chat app-menu shortcut, a review file tree open menu, early heartbeat automation affordances in threads, and image support for remote connections.

  ### Performance improvements and bug fixes

- Fixed review panel scroll jumps and PR status actions while a conversation is still running.
- Fixed several multi-window issues, plus `@`-mention results, duplicate project labeling, Windows `runGit` behavior, and revert, unstage, and stage-all actions.
- Improved remote-thread and sidebar polish, Windows update recovery, unsupported-version guidance, and overall thread search speed.
- Fixed sticky review issues such as diff hunk expansion, header overlap, archive-thread crashes, and window-zoom shell sizing.
- Additional performance improvements and bug fixes.

## March 2026

---

## Build and install plugins in Codex (2026-03-25)

  Codex now supports **plugins**: installable bundles that package skills, app
  integrations, and MCP server configuration for reusable workflows.

  Plugins are available in the Codex app, CLI, and IDE extensions.

  You can install curated plugins from the plugin directory, or scaffold a local
  plugin with `@plugin-creator` and test it with workspace-scoped or home-scoped
  marketplaces.

  Learn more in the [plugins documentation](/codex/plugins "/codex/plugins").

  ![](/images/codex/plugins/directory.png)

  #### Plugin structure

  Every plugin is a folder with a required `.codex-plugin/plugin.json` manifest
  and optional supporting files:

  ```
  my-plugin/
    .codex-plugin/
      plugin.json   # Required: plugin manifest
    skills/         # Optional: packaged skills
    .app.json       # Optional: app or connector mappings
    .mcp.json       # Optional: MCP server configuration
    assets/         # Optional: icons, logos, screenshots
  ```

  #### Install plugins per-user or per-repo

  You can install plugins for just yourself with
  `~/.agents/plugins/marketplace.json` and `~/.codex/plugins/`, or for everyone
  on a project with `.agents/plugins/marketplace.json` and a repo-local plugin
  directory such as `./plugins/`.

  #### Curated plugins and local development

  Codex surfaces curated public plugins in the plugin directory. Codex also ships
  with the built-in `@plugin-creator` skill to help you scaffold a plugin, add a
  local marketplace entry, and test it before sharing it with teammates.

---

## Codex app 26.324 (2026-03-25)

  ### New features

- Redesigned the skills and plugins browse and manage pages.
- Added per-window zoom and a clearer edited-files state in review.
- Added automation titles and icons in the sidebar, plus bundled Raycast themes.

  ### Performance improvements and bug fixes

- Kept loaded threads and projects visible during reconnects and made navigation feel faster.
- Fixed archive freezes, markdown wrapping, hotkey-window regressions, and several permissions, terminal, and worktree issues.
- Additional performance improvements and bug fixes.

---

## Codex app 26.323 (2026-03-24)

  ### New features

- Added search for past Codex app threads, including a sidebar shortcut and keyboard shortcuts for jumping to recent threads.
- Added a one-click option to archive all local threads in a project.
- Synced key settings between the Codex app and the VS Code extension, and added a settings entry point in the extension.

  ### Performance improvements and bug fixes

- Additional performance improvements and bug fixes.

---

## Codex app 26.320 (2026-03-20)

  ### New features

- Added Floating Composer v2.
- Added terminal shortcuts for jumping by word and line.
- Improved plugin discovery surfaces and file-path rendering for saved images.

  ### Performance improvements and bug fixes

- Fixed sidebar crashes when subagent turn items are missing.
- Fixed pop-out thread routing and preserved local paths for composer image attachments.
- Additional performance improvements and bug fixes.

---

## Codex app 26.318, 26.319 (2026-03-19)

  ### New features

- Added skills to the `@` menu so you can insert them from the composer alongside other mentions.
- `Cmd/Ctrl+F` now starts with your current text selection, which makes searching reviews and diffs faster, alongside broader review navigation improvements such as a refreshed file tree and percentage-based file tree resizing.
- Added a branded loading shimmer while the app starts.

  ### Performance improvements and bug fixes

- Improved collapsed diff summaries in review.
- Fixed slash-command focus and composer alignment issues, and polished plugin cards and step details.
- Additional performance improvements and bug fixes.

---

## Codex app 26.317 (2026-03-18)

  ### New features

- You can now fork a conversation from an earlier message, not just the latest turn.
- Added slash commands for switching models and reasoning levels, and made slash commands work in the middle of a draft prompt.
- Added notifications for plan mode questions so it’s easier to notice when Codex needs input.

  ### Performance improvements and bug fixes

- Fixed thread handoff and subagent navigation issues across worktrees and the VS Code extension.
- Additional performance improvements and bug fixes.

---

## Introducing GPT-5.4 mini in Codex (2026-03-17)

  GPT-5.4 mini is now available in Codex as a fast, efficient model for lighter
  coding tasks and subagents.

  It improves over GPT-5 mini across coding, reasoning, image understanding, and
  tool use while running more than 2x faster. In Codex, GPT-5.4 mini uses 30% as
  much of your included limits as GPT-5.4, so comparable tasks can last about
  3.3x longer before you hit those limits.

  GPT-5.4 mini is available in the Codex app, the CLI, the IDE extension, and
  Codex on the web. GPT-5.4 mini is also available in the API.

  Use GPT-5.4 mini for codebase exploration, large-file review, processing
  supporting documents, and other less reasoning-intensive subagent work. For
  more complex planning, coordination, and final judgment, start with GPT-5.4.

  To switch to GPT-5.4 mini:

- In the CLI, start a new thread with:

    ```
    codex --model gpt-5.4-mini
    ```

    Or use `/model` during a session.
- In the IDE extension, choose GPT-5.4 mini from the model selector in the
    composer.
- In the Codex app, choose GPT-5.4 mini from the model selector in the
    composer.

  If you don’t see GPT-5.4 mini yet, update the CLI, IDE extension, or Codex app
  to the latest version.

---

## Codex app 26.313 (2026-03-16)

  ### New features

- Added back and forward buttons in the header so you can move between recent screens more quickly.
- Added an **Open in Finder**, **Open in Explorer**, or **Open in File Manager** action from thread menus to jump straight to a thread’s project folder.

  ### Performance improvements and bug fixes

- Improved resume and thread error toasts with clearer details when something goes wrong.
- Additional performance improvements and bug fixes.

---

## Codex app 26.312 (2026-03-12)

  ### Themes

  Change the Codex app appearance in **Settings** by choosing a base theme,
  adjusting accent, background, and foreground colors, and changing the UI and
  code fonts. You can also share your custom theme with friends.

  ![Codex app theme settings showing custom themes, color controls, and font settings](/images/codex/app/themes-side-by-side.webp) ![Codex app theme settings showing custom themes, color controls, and font settings](/images/codex/app/themes-side-by-side.webp)

  ![Codex app theme settings showing custom themes, color controls, and font settings](/images/codex/app/themes-side-by-side.webp) ![Codex app theme settings showing custom themes, color controls, and font settings](/images/codex/app/themes-side-by-side.webp)



  ### Revamped Automations

  You can now choose whether automations run locally or on a worktree, define
  custom reasoning levels and models, and use templates to find inspiration for
  new automations.

  ![Automations settings showing local and worktree options alongside scheduling controls](/images/codex/app/codex-automations-light.webp) ![Automations settings showing local and worktree options alongside scheduling controls](/images/codex/app/codex-automations-dark.webp)

  ![Automations settings showing local and worktree options alongside scheduling controls](/images/codex/app/codex-automations-light.webp) ![Automations settings showing local and worktree options alongside scheduling controls](/images/codex/app/codex-automations-dark.webp)



  ### Performance improvements and bug fixes

  Various bug fixes and performance improvements.

---

## Codex app 26.311 (2026-03-11)

  ### New features

- Codex can now read the integrated terminal for the current thread, so it can check the status of a running development server or refer back to failed build output while it works with you.

  ### Performance improvements and bug fixes

- Additional performance improvements and bug fixes.

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
