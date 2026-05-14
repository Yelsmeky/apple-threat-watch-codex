# Paste This Into Codex

Open the Codex app, start a new local session, and paste this prompt:

```text
Please install Apple Threat Watch for Codex from this prompt-only repository:

https://github.com/Yelsmeky/apple-threat-watch-codex

If I do not already have Codex installed:
- Recommend the Codex app first when it is available for my platform, especially on macOS or Windows.
- Tell me to download the Codex app from the official OpenAI Codex page: https://openai.com/codex/
- Explain that the Codex app gives a visual local session where I can review the plan, choose components, and approve or reject local configuration.
- Also explain the Codex CLI option for terminal, Linux, headless, or unattended workflows.
- For the CLI, use the current OpenAI install command: `npm install -g @openai/codex`.
- Tell me to verify the CLI with `codex --version` and `codex --help`.
- Explain that scheduled local components such as LaunchAgents or dependency drift watchdogs may need the CLI because they run `codex exec` unattended after I approve the design.

Important trust boundary:
- This repository should contain only Markdown documentation and prompts, not executable scripts, binaries, LaunchAgent plists, malware samples, packages, or installers.
- First inspect the repository and confirm that it is prompt-only.
- Do not run any repository-provided code. If executable code or binary artifacts are present, stop and report that the repository is not prompt-only.

Legal and safety caveat to explain before installation:
- This caveat is not legal advice.
- This project is provided as-is, without warranty, under the repository LICENSE.
- The maintainer and contributors are not responsible for damage, data loss, privacy exposure, missed detections, false alarms, service interruptions, account issues, security incidents, or other consequences from using, modifying, sharing, or relying on this project or on files generated from these prompts.
- This package is designed for defensive, read-only threat awareness and is not designed to harm systems, exfiltrate data, execute malware, remove software, change settings, rotate credentials, or perform remediation.
- Even so, AI can make mistakes, hallucinate, misunderstand local context, or be influenced by malicious prompt injection inside threat reports, web pages, PDFs, issues, code blocks, IOC lists, or other external content.
- Tell me to review generated plans, commands, scripts, LaunchAgents, and outputs before approving them.
- Treat automated findings as triage leads, not final proof of compromise.

Before installation, guide me through choices:
- Ask whether I want a Simple, Detailed, or Expert explanation.
- Simple means plain-English purpose, what will run, and what I need to approve.
- Detailed means include file locations, schedules, logs, rollback, and privacy/security notes.
- Expert means include launchd behavior, command-line details, sandboxing, state files, trigger logic, and failure modes.

Then explain the installable components and ask which ones I want:
- Manual threat watch: creates a local workspace and prompt for on-demand checks only.
- Daily scheduled threat watch: runs the threat-watch prompt every day.
- Wake-aware LaunchAgent: uses a per-user macOS LaunchAgent with StartCalendarInterval so missed daily runs can happen after wake.
- Dependency drift watchdog: watches my chosen project/tooling roots for package manifest and lockfile changes, then rechecks tracked package-manager threats after installs or updates.
- iPhone/iPad checklist only: produces manual inspection guidance for iOS/iPadOS threats without trying to inspect the device internals from macOS.

For each component, explain:
- What it does.
- Why it is beneficial.
- What files it would create.
- What permissions or approvals it needs.
- What runs automatically, if anything.
- What logs/state it keeps.
- How to check status.
- How to uninstall or roll back.

Requirements:
- Install into ~/AppleThreatWatch unless I specify another path.
- Generate any needed local scripts, config files, and LaunchAgent plist yourself from the plan language in this repository.
- Before writing files or loading a LaunchAgent, show me the generated plan, local file paths, and exact commands you intend to run.
- Show me how this installation connects to the Codex app and/or Codex CLI, depending on which interface I choose.
- Only configure a per-user LaunchAgent if I choose a scheduled or watcher component.
- If I choose the daily schedule, configure it to run daily at 7:30 AM local time and catch up on next wake using StartCalendarInterval.
- Keep the workflow read-only: no cleanup, quarantine, deletions, unloads except for replacing this exact LaunchAgent during install/update, resets, installs beyond local generated files, settings changes, or remediation.
- The generated wrapper should wait 15 minutes, check whether today's case folder already exists, and skip if it does.
- The generated wrapper should run codex exec with web search enabled and the hardened prompt in prompts/apple-threat-watch.prompt.md.
- If I choose the dependency drift watchdog, ask me which local project/tooling directories should be monitored for package-manager changes.
- If I choose the dependency drift watchdog, generate a local file-change watchdog that debounces filesystem changes, snapshots package-manager manifest/lockfile state, and triggers a targeted threat-register recheck only when relevant dependency files changed.
- Verify the generated LaunchAgent plist with plutil.
- Run smoke tests for only the components I approve.
- Show me the installed paths, status command, manual run command, generated files, and uninstall command.
```

Optional custom install path:

```text
Install into ~/Documents/AppleThreatWatch instead of ~/AppleThreatWatch.
```
