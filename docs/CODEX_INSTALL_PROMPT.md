# Paste This Into Codex

Open the Codex app, start a new local session, and paste this prompt:

```text
Please install Apple Threat Watch for Codex from this prompt-only repository:

https://github.com/Yelsmeky/apple-threat-watch-codex

Important trust boundary:
- This repository should contain only Markdown documentation and prompts, not executable scripts, binaries, LaunchAgent plists, malware samples, packages, or installers.
- First inspect the repository and confirm that it is prompt-only.
- Do not run any repository-provided code. If executable code or binary artifacts are present, stop and report that the repository is not prompt-only.

Requirements:
- Install into ~/AppleThreatWatch unless I specify another path.
- Generate any needed local scripts, config files, and LaunchAgent plist yourself from the plan language in this repository.
- Before writing files or loading a LaunchAgent, show me the generated plan, local file paths, and exact commands you intend to run.
- Configure a per-user LaunchAgent that runs daily at 7:30 AM local time and catches up on next wake using StartCalendarInterval.
- Keep the workflow read-only: no cleanup, quarantine, deletions, unloads except for replacing this exact LaunchAgent during install/update, resets, installs beyond local generated files, settings changes, or remediation.
- The generated wrapper should wait 15 minutes, check whether today's case folder already exists, and skip if it does.
- The generated wrapper should run codex exec with web search enabled and the hardened prompt in prompts/apple-threat-watch.prompt.md.
- Ask me which local project/tooling directories should be monitored for package-manager changes.
- Generate an optional local file-change watchdog that debounces filesystem changes, snapshots package-manager manifest/lockfile state, and triggers a targeted threat-register recheck only when relevant dependency files changed.
- Verify the generated LaunchAgent plist with plutil.
- Run the generated wrapper smoke test with no grace period.
- Show me the installed paths, status command, manual run command, generated files, and uninstall command.
```

Optional custom install path:

```text
Install into ~/Documents/AppleThreatWatch instead of ~/AppleThreatWatch.
```
