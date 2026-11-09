# BitPull (bitpull.cloud)

**Share code knowledge and computing power with AI tools.** BitPull is a desktop app and command-line tool for developers. With it you can:

- **Publish signed, AI-readable code repositories.** Claude Code, Codex, Cursor and other AI tools search them through MCP.
- **Lend idle CPU, memory and open AI models** (text, vision, images, speech, music) and earn credits. Lending is off until you turn it on, with daily, weekly and monthly limits.
- **Use the community network:** run jobs in sandboxes on other people's computers, encrypted on the way, and ask open models.
- **My network:** computers you add run your own jobs first, for free. They can also run one larger model together, from the dashboard, and offer it to others for credits.
- **Chat and local APIs:** a chat page for every model, and OpenAI, Claude Messages and Ollama compatible endpoints on this computer for your other tools.
- **Projects:** a code editor on a folder you authorise, with agents that edit it: file tree, tabs, search, Git panel (push only with your click), Problems, outline, local history, inline edits, `@file` references, diffs you keep or undo piece by piece, Stop and Undo. Ask always, accept edits or auto: in auto commands run on your computer in the project folder within automatic limits; with community models, and for publishing or risky commands, every command waits for your click.
- **Quick commands (from 0.1.32):** in Projects and the chat, `/` opens commands (`/compact`, `/review`, `/init`, `/btw`, `/model`…) and your own custom commands from `.bitpull/skills/<name>/SKILL.md` or `~/.bitpull/skills/`; `!command` runs in the project's folder and the agent answers about it; `@` for files, `?` for keyboard shortcuts, remappable in `~/.bitpull/keybindings.json` (Ctrl+X then Ctrl+S sends the queue now). The agent follows `BITPULL.md`, `AGENTS.md` or `CLAUDE.md`. Drag a folder onto the app's window to open it in Projects.
- **Terminal:** a real terminal in the projects view of the desktop app, off until you turn it on. The npm package leaves out its native component to stay small.
- **Costs less:** models run on computers people already own. No monthly fee with pay as you go, or plans from €4.50 a month, VAT included.

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
- `search_repos`, `read_manifest`, `fetch_files`: code shared by BitPull users, and public GitHub repositories BitPull offers (permissive or GPL licence), read straight from GitHub at a fixed commit
- `ask_open_model`, `use_open_model`, `list_open_models`
- `ask_group_model`, `list_group_models`: the model run by the person's own group of computers
- `bitpull_groups`, `bitpull_start_group`, `bitpull_stop_group`, `bitpull_share_group` and the others named `bitpull_*`: every item of the app's control panel
- `run_job`, `job_status`, `my_balance`
- `bitpull_file_limits`, `save_job_files`: large files of any kind, encrypted here and sent directly; results are saved in a folder you authorised and then deleted from BitPull's store
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
bitpull run busybox --file big.bin=./big.bin --out ./results -- sh -c "gzip -c big.bin > out/big.bin.gz"
```

From a phone, open https://bitpull.cloud/app: after turning on "Use from your phone" in the app on your computer and scanning its code, the phone shows that computer's Projects, terminal, chat and settings, encrypted end to end. Everything runs on the computer. Terminals opened from the phone keep running on the computer for an hour after the phone goes away, and chat answers are saved by the computer.

Shared groups: several people (classmates, friends) put some of their computers together to run large open models. Anyone can create one and invite others with a code; each person offers only their own computers. Models are free inside the group; traffic is always paid in credits. A group can also lend to people outside it, and its members share half of what it earns. Use a group only with people you trust: its computers process the members' questions.

Large files have no fixed limit: the command says how much one job can carry right now. Splitting big work into several jobs gives the same result, faster. After a job, its data is deleted from the computer that ran it as soon as the result is delivered, and encrypted copies in transit within 24 hours at most.

## Privacy and safety

- BitPull reads only the folders you authorise and publishes only what you publish.
- Jobs travel encrypted and BitPull's server cannot read them. The computer that runs a job reads its content to do the work: for private data, use only your own computers. On your computer they run in sandboxes without internet access or access to your files. More at https://bitpull.cloud/security
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
