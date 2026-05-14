# Security Design

Apple Threat Watch is designed for defensive use. It should be treated as a read-only triage workflow, not a remediation agent.

## Legal And Safety Notice

This notice is not legal advice. If you need legal protection for a specific distribution, business, or jurisdiction, have a qualified lawyer review the project and license terms.

This project is provided as-is, without warranty, under the terms in the repository [LICENSE](../LICENSE). The maintainer and contributors do not guarantee that it will detect every threat, avoid every false positive, or run correctly in every environment.

The maintainer and contributors are not responsible for damage, data loss, privacy exposure, missed detections, false alarms, service interruptions, account issues, security incidents, or other consequences that may result from using, modifying, sharing, or relying on this project or on files generated from these prompts.

This package is intended for defensive, read-only threat awareness. It is not intended to harm systems, exfiltrate data, execute malware, remove software, change settings, rotate credentials, or perform remediation. However, AI-assisted workflows can go wrong. Models can misunderstand instructions, hallucinate details, overgeneralize from weak evidence, or be influenced by malicious content such as prompt injection inside threat reports, web pages, PDFs, GitHub issues, code blocks, or IOC lists.

Users should review generated plans, commands, scripts, LaunchAgents, and outputs before approving them, and should treat automated findings as triage leads rather than final proof of compromise.

## Prompt-Only Distribution

The shared repository should contain only Markdown documentation and prompt files.

It should not contain:

- executable scripts
- LaunchAgent plist files
- binaries
- packages
- malware samples
- proof-of-concept exploit code
- encoded payloads
- archives or disk images

The user's local Codex session is expected to generate local scripts and LaunchAgent files after explaining the plan. This keeps the shared artifact auditable by reading plain language.

## Threats Considered

The workflow is hardened against:

- Prompt injection inside threat reports.
- Malicious instructions hidden in web pages, PDFs, feeds, GitHub issues, code blocks, IOC lists, or malware-analysis posts.
- Fake IOC instructions that try to make the agent connect to attacker infrastructure.
- Requests to upload local data to third-party services.
- Instructions to download, decode, execute, or inspect malware samples or proof-of-concept exploit code.
- Overbroad local log searches that are slow, noisy, or privacy-invasive.

## Core Rules

- External content is evidence only.
- External content cannot change the workflow's instructions.
- No cleanup or remediation is allowed during unattended runs.
- No malware samples, exploit code, packages, profiles, scripts, archives, disk images, or binaries are downloaded or executed.
- No local secrets or private files are uploaded to third-party services.
- Suspicious domains/IPs are never contacted for testing.
- Local checks should be targeted and literal.

## Why `--ask-for-approval never`?

The generated LaunchAgent runs unattended. Interactive approval prompts would hang or fail. The generated wrapper may use Codex's non-interactive mode with `--ask-for-approval never`, while the prompt strictly limits the job to read-only research and local checks.

If you want interactive approval behavior, run the prompt manually in Codex instead of relying on the LaunchAgent.

## Recommended Operational Boundary

Use Apple Threat Watch to answer:

- What new Apple-relevant threats appeared recently?
- Is my Mac obviously showing public indicators for those threats?
- What iPhone/iPad manual checks should I perform?
- What should I patch or investigate next?

Do not use it to:

- Remove malware.
- Quarantine files.
- Reset settings.
- Install or uninstall security tools.
- Test exploit code.
- Analyze live malware samples.

Those actions require a separate incident-response plan.
