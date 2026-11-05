# BitPull (bitpull.cloud)

**Share code knowledge and computing power with AI tools.** BitPull is a desktop app and command-line tool for developers. With it you can:

- **Publish signed, AI-readable code repositories.** Claude Code, Codex, Cursor and other AI tools search them through MCP.
- **Lend idle CPU, memory and open AI models** (text, vision, images, speech, music) and earn credits. Lending is off until you turn it on, with daily, weekly and monthly limits.
- **Use the community network:** run jobs in sandboxes on other people's computers, encrypted on the way, and ask open models.
- **My network:** computers you add run your own jobs first, for free. They can also run one larger model together, from the dashboard.

Not affiliated with other products named BitPull. Website: https://bitpull.cloud · Guide for AI assistants: https://bitpull.cloud/llms.txt · Install data with SHA-256: https://bitpull.cloud/install.json

## Install

| System | Command |
|---|---|
| macOS / Linux | `curl -fsSL https://bitpull.cloud/install.sh \| sh` |
| Windows (PowerShell) | `powershell -ExecutionPolicy Bypass -c "irm https://bitpull.cloud/install.ps1 \| iex"` |
| Only the command line and MCP server (Node.js 20+) | `npx -y bitpull doctor` |

The install scripts verify the SHA-256 of the download before installing it, install for the current user and add the `bitpull` command. Installers are also available at https://bitpull.cloud/download

## Use it from your AI tool (MCP)

```json
{ "mcpServers": { "bitpull": { "command": "npx", "args": ["-y", "bitpull", "mcp"] } } }
```

You can also connect it from the app, or with `bitpull connect claude-code|codex|cursor|windsurf|gemini|vscode|claude-desktop`.

Then ask your assistant to log in. The `bitpull_login` tool shows a link and a code, and **you** approve it on the website: the assistant never sees your password.

The tools include:
- `search_repos`, `read_manifest`, `fetch_files`
- `ask_open_model`, `use_open_model`, `list_open_models`
- `run_job`, `job_status`, `my_balance`
- `bitpull_login`, `bitpull_logout`, `bitpull_setup_status`, `bitpull_set_lending_rules`, `bitpull_set_ai_limits`, `bitpull_install`, `bitpull_download_model`

## Command line

```
bitpull login --device     log in by approving a code on the website (--via github|google)
bitpull logout             log this computer out, e.g. to log in with another account
bitpull doctor             what this computer has, required vs optional, and how to add the rest (--json)
bitpull status             login, lending state, what this computer offers now
bitpull install lemonade   images, speech and music engine (also: docker, ollama --run)
bitpull pull qwen3.5:4b    download an open model to lend
bitpull set enabled=on idleMinutes=0 maxCpus=2 keepAwake=on waitMinutes=15
bitpull limits day.requests=50
bitpull ask "…"            ask an open model on the network
bitpull run python:3.12-slim -- python -c "print(1)"
bitpull network            your computers (add/remove <computer> changes your network)
bitpull run python:3.12-slim --mine -- python -c "print(1)"
```

## Privacy and safety

- BitPull reads only the folders you authorise and publishes only what you publish.
- Jobs travel encrypted and BitPull's server cannot read them. On your computer they run in sandboxes without internet access or access to your files.
- The computer that runs a job must decrypt it to do the work. For private data use `--mine`: the job never leaves the computers of your network.
- The local dashboard and API listen only on 127.0.0.1 and require a secret token.
- Requests to proprietary models offered by the platform (Claude, GPT, Gemini…) pass through BitPull's server to the provider: they are **not** end-to-end encrypted.

Terms: https://bitpull.cloud/legal/terms · Privacy: https://bitpull.cloud/legal/privacy

## Downloads in this repository

This repository hosts the signed release builds of the BitPull desktop app; the source code is private. Get the latest version from the [Releases](https://github.com/SamuealPK/bitpull-releases/releases/latest) page, from https://bitpull.cloud/download or with the install scripts above.

- **macOS:** open the `.dmg` and drag BitPull to Applications. The first time, right-click the app and choose Open (the install script avoids this step).
- **Windows:** run the `-setup.exe` installer. If SmartScreen appears, choose More info → Run anyway.
- **Linux:** install the `.deb` or `.rpm`, or make the `.AppImage` executable and run it.

Every file's SHA-256 is listed on the release page and in https://bitpull.cloud/install.json.
