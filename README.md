# goldenkube-releases

Public release artifacts for the GoldenKube CLI (https://goldenkube.dev): signed binaries and
checksums via GitHub Releases (macOS signed + notarized; Linux amd64/arm64 archives and packages verified by sha256). This repository never contains source code.

> Status: pre-release scaffolding. No release has been published yet.

Install (once released): macOS `brew install --cask goldenkube/tap/goldenkube`; Linux `curl -fsSL https://goldenkube.dev/install.sh | sh` or the `.deb`/`.rpm` attached to the release (unsigned archives; verify with `goldenkube_<version>_checksums.txt`).

| File | Purpose |
|---|---|
| `EULA.md` | End user license agreement |
| `THIRD-PARTY-NOTICES.md` | Licenses of the Go modules in the binary (go-licenses v1.6.0; regenerated at release time) |
| `PRIVACY-NOTICE.md` | What the CLI sends and never sends |
| `RELEASE-PROCESS.md` | Build, sign, notarize, publish checklist |

GoldenKube is proprietary software; see the EULA.
