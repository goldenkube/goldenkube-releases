# GoldenKube CLI Privacy Notice

> **DRAFT - pending owner and legal review. Not in force.** The data list below describes the
> intended design and must be verified against the shipped CLI before release.

Last updated: [date] - Controller: [Licensor legal entity name], [contact email]

## What the CLI sends to goldenkube.dev
- Account identifier, via the OAuth/device-grant access token used to authenticate requests
- Scenario ID and scenario version you start or submit
- Run timestamps (start, submit, finish)
- Grading results (per-task pass/fail and score) for your submissions
- CLI version
- Operating system and CPU architecture (for example darwin/arm64)

Purpose: sign you in, sync progress across devices, and keep the scenario catalog current.

## What the CLI never sends
- Terminal or shell history
- Files from your computer
- Raw environment variables
- Kubeconfigs, SSH keys, or cluster credentials

Practice clusters run entirely on your machine; cluster contents stay local and grading runs locally.

## Retention, sharing, and your rights
- Retention: [period to be defined]
- Sharing: service providers needed to run the service (hosting on Cloudflare) [list to be confirmed]
- Your rights (access, correction, deletion, export) and how to exercise them: [to be defined by counsel]
- Account deletion removes synced progress: [to be confirmed]

## Local data
The CLI stores configuration, caches, and logs under `~/Library/Application Support/goldenkube`,
`~/Library/Caches/goldenkube`, and `~/Library/Logs/goldenkube`. `brew uninstall --cask --zap goldenkube`
removes them.
