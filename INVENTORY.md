# Tooling inventory

> Snapshot: 2026-11-09 · Primary workstation: Intel MacBook Pro · Scope: local tools, workflows, and related GitHub projects.

This inventory is organized by how much a tool helps an AI agent act independently, followed by tools and workflows that primarily help the user. Packaged or ambiguous application assets are collected at the end.

## 1. Tools that help AI agents act

### Computer, browser, and operating-system control

| Tool | What it does | Evidence / status |
|---|---|---|
| **Desktop Commander** | Local MCP for filesystem access, terminal commands, process inspection, and file editing. | Local MCP active. |
| **Arena Bridge** — `vernikr/arena-bridge` | MCP/CLI bridge for working with the computer: files, shell, Chrome, mouse and keyboard, and process control. Supports confirmation for mutating actions. | CLI installed globally via npm (`0.20.6`); source repository exists. |
| **browser-agent** — `vernikr-personal/browser-agent` | VPS service that controls a real Chrome instance through X11, DOM access, screenshots, mouse, and keyboard. | VPS service recorded in the setup; repository exists. |
| **agent-browser** | Browser automation CLI/MCP using Chrome DevTools Protocol; can attach to an existing Chrome session and return compact accessibility snapshots. | Local CLI 0.41.2 and config directory present; included in OpenCode MCP configuration. |
| **browser-agent-mcp** — `vernikr-personal/browser-agent-mcp` | MCP adapter that exposes browser-agent capabilities to agents. | Source repository exists; runtime status not independently verified in this audit. |
| **TinyFish MCP** | Cloud web search, page extraction, browser automation, and monitoring. TinyResearch adds multi-step Deep Research reports with claim-level citations; TinySet builds structured datasets from public web pages. | Configured in Cursor; Search and Fetch are free (30 requests/min and 500/hour; 150 URLs/min and 1,000/day). TinyResearch is available through MCP/API/CLI/SDK; Deep reports cost $2 and Max $3 per completed report. New accounts receive $8 in starter wallet credit; existing-account balance depends on the account. Public web only. |
| **Figma MCP integrations** | Give agents access to Figma context. | Framelink configured in Cursor; Figma Remote configured in VS Code; Claude Code integration found but requires authorization. |
| **Codex Node REPL** | Persistent Node execution environment for tool-assisted coding and analysis. | Enabled in Codex. |
| **Codex Computer Use** | Computer interaction capability in Codex. | Present in configuration, disabled. |

### Research, search, and information retrieval

| Tool | What it does | Evidence / status |
|---|---|---|
| **research-workspace** — `vernikr/research-workspace` | Agentic research system combining Freebuff, HyperResearch, and browser-agent. Includes the `rw` orchestrator, 19 Skills, 16 specialized agents, staged search and investigation, contradiction tracking, synthesis, critics, citation checks, and resumable runs. | Source repository inspected; repository documentation describes the workflow. |
| **HyperResearch** | Research CLI used for broad search and structured investigation. | Installed through uv (`0.12.0`). |
| **Exa Search / Exa Contents** | Skills for web search and extracting page contents. | Local Skills found in `~/.agents/skills/`; Exa connector also available in ChatGPT. |
| **Parallel MCP 2.0** | Unified web search, page extraction, grounded decisions, and multi-step cited research through one hosted MCP endpoint. | Configured globally in OpenCode and in the tooling-inventory Freebuff project. Free `web_search`, `web_fetch`, and `web_decisions`; `web_research` requires Parallel sign-in and is billed. OmniRush currently blocks remote MCP servers, so it cannot run there. |
| **TinyFish** | Cloud browser for web exploration and extraction. | Cursor MCP configuration found; see the computer-control section. |
| **biblio-mcp** — `vernikr-personal/biblio-mcp` | MCP for searching books and academic publications and retrieving available files. | Source repository exists; local runtime not confirmed. |
| **Gemini CLI / MCP** — `vernikr/gemini` | Personal Gemini CLI/MCP for text and document analysis, file workflows, and TTS. | CLI installed through uv (`0.28.0`); source repository exists. MCP config files were found but were empty at audit time. |
| **gemini-router** — `vernikr/gemini-router` | VPS API router for Gemini, including key pools, quota handling, model fallback, and request logging. | VPS service recorded in the setup; repository exists. |
| **survey-relay-bot** — `vernikr/survey-relay-bot` | Telegram-based questionnaire service for agents: REST, MCP, and SDK interfaces; conditional questions and text, choice, number, date, file, contact, and location inputs. | Source repository inspected; deployment status not confirmed here. |
| **yt-transcript-api** — `vernikr/yt-transcript-api` | Retrieves YouTube transcripts. | Source repository exists. |
| **yt-summary** — `vernikr/yt-summary` | Summarizes YouTube content. | Source repository exists. |
| **Gladia MCP** — `vernikr/gladia-mock-test` | Audio/video transcription through Gladia; can extract scene frames using PySceneDetect and ffmpeg. | MCP implementation found in the repository; related Quick Action is installed locally. |

### Agent-development and code-quality tools

| Tool | What it does | Evidence / status |
|---|---|---|
| **OmniRush** | AI coding-agent application and workflow environment. | App installed; CLI installed globally via npm (`2.7.4`). Built-in Skills are listed in section 5. |
| **Serena Agent** | Code-aware agent tooling for navigating and working with codebases. | Installed through uv (`1.7.1.dev0`). |
| **Semgrep** | Static analysis and security scanning. | CLI installed through uv. |
| **Ruff** | Fast Python linting and formatting. | CLI installed through uv. |
| **ty** | Fast Python type checker and language server from Astral. | Installed globally with `uv tool install ty`; `ty check` available. |
| **Playwright** | Browser automation and browser testing. | Installed through uv. |
| **Size Report** — `vernikr-personal/size-report` | CLI for examining project size and structure. | Source repository exists; local CLI installation not confirmed. |
| **CodeScene CLI Skills** — `vernikr/codescene-cli-agent-skills` | Six Skills that help agents use CodeScene CLI. | Source repository exists. |

### Local command-line utilities useful to agents

**Installed through npm / uv**

- npm global: `arena-bridge` 0.20.6, `omnirush` 2.7.4.
- uv: `gemini` 0.28.0, `hyperresearch` 0.12.0, `serena-agent` 1.7.1.dev0, `semgrep`, `ruff`, `playwright`, `yt-dlp`, `rembg`, `mdict`.

**MacPorts utilities**

- Search and navigation: `rg`, `fd`, `fzf`, `ast-grep`, `bat`, `eza`, `zoxide`.
- Structured data and scripting: `jq`, `yq`, `just`, `direnv`, `parallel`.
- Git and CI: `gh`, `glab`, `act`, `actionlint`, `gitleaks`, `lychee`.
- Code analysis and performance: `hyperfine`, `cloc`, `scc`, `mergiraf`, `osv-scanner`, `syft`.
- Media and documents: `ffmpeg`, `ocrmypdf`, `pandoc`, ImageMagick, Poppler.
- Infrastructure and local models: `cloudflared`, `llama.cpp`.
- Other development tools present: `pnpm`, `bun`, `deno`, `fnm`, `go`, `git`, `tmux`, `shellcheck`, `swiftlint`, `wget`, `tree`, `trash`.

This is a curated list of relevant utilities, not a complete dump of every MacPorts package or transitive dependency.

## 1A. Free or free-quota alternatives worth evaluating\n\nThese are candidates from the 2026-11-09 review, not all installed. Free access and limits are recorded explicitly.\n\n| Tool | Potential improvement | Free access and trade-offs |\n|---|---|---|\n| [Cua Driver](https://github.com/trycua/cua) | Native macOS app control through MCP while keeping the target window in the background; useful to compare with Arena Bridge/Peekaboo. | MIT; supports macOS Intel x86_64. Requires Accessibility and Screen Recording permissions; some drag-and-drop actions need foreground interaction. Not installed. |\n| [Toolport](https://toolport.app/) | Local MCP gateway to configure servers once for multiple agent clients, with tool-change checks. | Free MIT desktop app, no account, 45 supported agents on one machine. Cross-device sync and hosted team features are paid; self-hosted Teams server is free up to 10 users. Not installed. |\n| [OpenAlex API](https://help.openalex.org/access/pricing/) | Specialized scholarly search, author/work metadata, citations, and DOI/reference resolution. | $1 API usage/day with a free key, no payment method; $0.10/day without a key. API rate limits apply; not a full-text repository. Not installed. |\n| [Groq API](https://console.groq.com/docs/rate-limits) | Extra inference provider and Whisper STT fallback for `gemini-router`. | Free tier includes selected models such as GPT-OSS-120B and Qwen3.8-27B; model-specific limits include 30 RPM, 1,000 RPD, 8K TPM and 200K TPD for these models. Limits vary by model/account. Not installed. |\n| [Figbridge](https://github.com/rudraptpsingh/figbridge) | Local Figma-to-agent MCP with design inspection, token/component mapping, import, linting, and visual-diff workflows. | MIT, local, no account or Dev seat; 54 tools advertised. Young project; requires its Figma plugin and local bridge. Not installed. |\n\n## 2. Tools and workflows primarily for the user

### Custom macOS Quick Actions

These ten Quick Actions were classified as personal workflows rather than bundled application assets.

| Quick Action | Purpose | Related source |
|---|---|---|
| **Compress for Telegram** | Compresses video to HEVC and audio to AAC for Telegram. | `vernikr/compress-for-telegram`; helper: `encode_hevc.sh`. |
| **Clear Telegram json** | Cleans exported Telegram JSON. | `vernikr/clear-telegram-json`; helper: `clear_tg.sh`. |
| **Download Pinterest Video** | Downloads video from the active Chrome tab with yt-dlp. | Local Quick Action. |
| **Download Subtitles** | Downloads YouTube subtitles, with speech-recognition fallback. | `vernikr/yt-subs`; helper: `yt-subs.sh`. |
| **Download Subtitles and Comments** | Exports subtitles, comments, and YouTube metadata. | `vernikr/yt-subs`; helper: `yt_subs_comments.sh`. |
| **Extract audio** | Extracts audio from video to M4A. | Local Quick Action. |
| **Gladia Transcribe** | Transcribes media through Gladia and opens the resulting PDF. | `vernikr/gladia-mock-test`. |
| **Save Current Frame** | Saves the current frame from QuickTime. | Local Quick Action. |
| **Save as JPG** | Saves an image from the clipboard as JPG. | Local Quick Action. |
| **tt** | Converts CSV to a formatted Excel workbook using a template. | Local Quick Action. |

### Other personal projects and workflows

- **Edge TTS Quick Action** — `vernikr-personal/edge-tts-quick-action`: setup instructions for a macOS Quick Action using Edge TTS. The repository contained a README; the installed Quick Action itself was not found in the 14-action inventory.
- **tldr-digest** — `vernikr/tldr-digest`: consolidates TLDR General, Design, Tech, and AI digests into a ranked, practical summary.
- **tg-summary-ci** — `vernikr-personal/tg-summary-ci`: Swift CLI for summarizing Telegram exports.
- **tg2docx** — `vernikr/tg2docx`: Swift CLI for converting Telegram exports to DOCX.
- **finder-github-upload** — `vernikr/finder-github-upload`: Finder integration for uploading files to GitHub.
- **moex-tool** — `vernikr/moex-tool`: command-line entry point for MOEX-related workflows.
- **moex-spread-lab** — `vernikr/moex-spread-lab`: CLI for analyzing exchange spreads.
- **omnirush-gui** — `vernikr/omnirush-gui`: personal OmniRush fork with additional Skills, practices, and OpenCode agent configurations.
- **Maccy** — `vernikr/Maccy`: personal fork of the clipboard manager.
- **foo** — `vernikr/foo`: archive containing copies of older projects and experiments; may include duplicates.

These entries document related GitHub projects. Their presence here does not mean every project is installed or currently maintained.

### Installed applications

**AI and agent tools:** Claude, Codex, Cursor, Antigravity, Freebuff, ChatGPT, GitHub Copilot, OmniRush, ZCode, WorkBuddy AI, AutoClaw, Arena Bridge.

**Design:** Figma, SF Symbols, Numbers Creator Studio.

**Development and databases:** VS Code, Xcode, Docker, DBngin, TablePlus, Modern CSV, iTerm.

**Knowledge and productivity:** Obsidian, Pages, FBReader, GoldenDict-ng, Maccy.

**Browsers, networking, and security:** Chrome, Edge, Yandex Browser, Tor Browser, Iron, AdGuard VPN, AmneziaWG, Clash Verge, Outline, V2Box, AnyDesk, CryptoPro ECP, Rutoken for macOS.

**Media and archives:** IINA, VLC, Subler, Max, QLMarkdown, QuickLook Video, calibre, The Unarchiver, Unzip - RAR ZIP 7Z Unarchiver, Transmission.

**System and other applications:** App Cleaner 8, App Cleaner 9, CleanMyMac 5, GrandPerspective, Purge, QuickShade, RuSwitcher, Scroll Reverser, Turbo Boost Switcher, Discord, Microsoft Teams, Telegram, Zoom, Steam, Banquet for Fools, Factorio, Walk in the Parquet, Pure Web, cptools.

### ChatGPT-connected services

The following integrations were available in ChatGPT during the audit: GitHub, Dropbox, Box, Exa, Gmail, and Desktop Commander. Availability depends on the current account and connection permissions.

## 3. Related GitHub repositories

The projects below are included as source references and are not automatically considered installed applications.

| Repository | Purpose |
|---|---|
| `vernikr/arena-bridge` | Computer-control MCP/CLI bridge. |
| `vernikr-personal/browser-agent` | Browser automation service. |
| `vernikr-personal/browser-agent-mcp` | MCP adapter for browser-agent. |
| `vernikr/research-workspace` | Agentic research workflow, agents, and Skills. |
| `vernikr-personal/biblio-mcp` | Book and academic-publication search MCP. |
| `vernikr/gemini` | Gemini CLI/MCP implementation. |
| `vernikr/gemini-router` | Gemini API routing service. |
| `vernikr/survey-relay-bot` | Telegram questionnaire service with REST/MCP/SDK. |
| `vernikr/gladia-mock-test` | Gladia transcription MCP and related Quick Action. |
| `vernikr/yt-transcript-api` | YouTube transcript retrieval. |
| `vernikr/yt-summary` | YouTube summarization. |
| `vernikr/compress-for-telegram` | Telegram media compression workflow. |
| `vernikr/clear-telegram-json` | Telegram JSON cleanup workflow. |
| `vernikr/yt-subs` | YouTube subtitles and comments export. |
| `vernikr/tldr-digest` | Consolidated news digest. |
| `vernikr/omnirush-gui` | OmniRush fork and agent configuration. |
| `vernikr/Maccy` | Clipboard manager fork. |
| `vernikr/moex-tool` | MOEX command-line workflow. |
| `vernikr/moex-spread-lab` | Exchange spread analysis CLI. |
| `vernikr-personal/size-report` | Project size and structure CLI. |
| `vernikr-personal/tg-summary-ci` | Telegram export summarization CLI. |
| `vernikr/tg2docx` | Telegram export to DOCX. |
| `vernikr/finder-github-upload` | Finder-to-GitHub upload integration. |
| `vernikr/codescene-cli-agent-skills` | CodeScene CLI Skills. |
| `vernikr-personal/edge-tts-quick-action` | Edge TTS Quick Action instructions. |
| `vernikr/foo` | Archive of copies and experiments. |

## 4. MCP and configuration notes

- **Confirmed active locally:** Desktop Commander.\n- **Parallel MCP 2.0:** OpenCode global configuration added; OAuth/connection still needs confirmation in the app. Freebuff project configuration is in `.agents/mcp.json` and requires the first-load trust approval. OmniRush configuration is present but its current policy blocks remote MCP servers, so Parallel cannot run there.\n- **Python typing:** `ty` installed globally through uv.
- **Configured in IDEs:** TinyFish and Framelink Figma in Cursor; Figma Remote in VS Code; Parallel MCP 2.0 in OpenCode and this Freebuff project.
- **Requires authorization:** Figma integration in Claude Code.
- **Enabled:** Codex Node REPL.
- **Disabled:** Codex Computer Use.
- **Not operationally confirmed:** Freebuff Bridge local registration; Gemini MCP config files were empty; biblio-mcp and browser-agent-mcp runtime availability.
- **ChatGPT integrations:** GitHub, Dropbox, Box, Exa, Gmail, Desktop Commander.

Configuration presence is evidence of setup intent, not proof that an endpoint is reachable or that credentials still work.

## 5. Bundled and ambiguous application assets

These assets are kept at the end because they appear to ship with, or integrate closely with, an application. Some classifications are inferred from their location and naming.

### GitHub Copilot Skills — likely bundled

Found under the GitHub Copilot application support directory:

- `agent-merge`
- `github-agent-onboarding`
- `automation-group-creator`
- `impeccable`
- `codespace-browser-preview`
- `latex`
- `create-canvas`
- `agentfinder`
- `automation-creator`
- `af`
- `pr-stack`
- `regular-project-onboarding`
- `orchestrate`
- `connector-finder`

### Codex system Skills — bundled

Found under `~/.codex/skills/.system/`:

- `imagegen`
- `openai-docs`
- `review-agent`
- `skill-creator`
- `skill-installer`

### OmniRush Skills — likely bundled

Found under `~/.config/omnirush/`:

- `agent-swarm`
- `project-build`
- `project-debug`
- `project-feature`
- `project-handoff`
- `project-performance`
- `project-refactor`
- `project-review`
- `project-setup`
- `project-test`

### Claude / ZCode Quick Actions — likely application integrations

- `Claude - ask`: sends selected text to a new Claude chat.
- `Claude - codeHere`: opens the selected folder in Claude Code.
- `Claude - send`: sends files or folders to Claude Cowork.
- `Open in ZCode`: opens a folder in ZCode.

Their presence in the macOS Services directory does not conclusively establish whether they were installed by the application or added separately. They are placed here as the most reasonable classification.

---

## Audit limitations

- This is a point-in-time inventory, not a live health check.
- The primary Intel MacBook Pro was audited. A second connected computer was not included.
- Browser extensions, every background process, all remote hosts, and every application's runtime behavior were not exhaustively tested.
- Some GitHub repositories were inspected, while others are listed as references based on the inventory gathered during the audit.
- Version numbers are included only where they were captured.
- No API keys, tokens, private endpoints, or other secrets are included.
