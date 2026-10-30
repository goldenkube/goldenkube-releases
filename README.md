# goldenkube-releases

Public release artifacts for the GoldenKube CLI (https://goldenkube.dev): signed binaries and
checksums via GitHub Releases: macOS (Apple Silicon, Intel) and Linux (amd64, arm64) archives, Linux .deb/.rpm packages, SHA-256 checksums signed with minisign. macOS binaries are not Apple-signed or notarized yet. This repository never contains source code.

> Current release: v0.1.0 (2026-10-30). Assets, checksums and the minisign signature are on the Releases page.

Install (once released), macOS and Linux: `curl --proto '=https' --tlsv1.2 -sSf https://goldenkube.dev/install.sh | sh`; Linux alternatively the `.deb`/`.rpm` attached to the release. Verify with `goldenkube_<version>_checksums.txt` and its `.minisig` (see SECURITY.md).

| File | Purpose |
|---|---|
| `EULA.md` | End user license agreement |
| `THIRD-PARTY-NOTICES.md` | Licenses of the Go modules in the binary (go-licenses v1.6.0; regenerated at release time) |
| `PRIVACY-NOTICE.md` | What the CLI sends and never sends |
| `RELEASE-PROCESS.md` | Build, sign, publish process (public summary) |

GoldenKube is proprietary software; see the EULA.

## Trademarks and affiliation
GoldenKube is an independent project of ITEXPERT24 LTD (registered in England and Wales, company number 17110917,
registered office 71-75 Shelton Street, Covent Garden, London, WC2H 9JQ, United Kingdom) and is not affiliated with, endorsed by, or sponsored by
the Cloud Native Computing Foundation or The Linux Foundation. Kubernetes®, the certification names (CKA, CKAD, CKS,
KCNA, KCSA, LFCS, ICA, CNPE and others) and all related marks are trademarks of The Linux Foundation and its projects
and are used here only to describe what the practice material covers.

## Reporting a problem
Bugs: email hello@goldenkube.dev with the output of `goldenkube diagnostics --bundle` (paths and versions only; tokens
are redacted). Security issues: see SECURITY.md. Export note: the binary uses only standard TLS from the Go standard
library; no proprietary cryptography.

