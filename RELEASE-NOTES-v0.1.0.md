# GoldenKube CLI v0.1.0

First public release. Hands-on practice for the performance-based Kubernetes and Linux certifications
on your own machine: a real kubeadm cluster (Istio mesh for ICA, a plain Ubuntu VM for LFCS) in local
Multipass VMs, exam-style tasks, deterministic local grading, progress in your goldenkube.dev account.

## Install
- macOS and Linux: `curl --proto '=https' --tlsv1.2 -sSf https://goldenkube.dev/install.sh | sh`
- Linux packages: the `.deb` / `.rpm` below (`sudo dpkg -i …` / `sudo rpm -i …`)
- Multipass is required: `brew install --cask multipass` (macOS) or `sudo snap install multipass` (Linux)
- Then: `goldenkube doctor`, `goldenkube setup`, `goldenkube login`, `goldenkube list cka`

Full steps: https://goldenkube.dev/cli/install

## What is in the box
- 137 scenarios: CKA (37), CKAD (20), CKS (20), ICA (20), LFCS (20), CNPE (20); timed mock exams per exam
- Kubernetes 1.37 (CKA/CKAD) and 1.35 (CKS/ICA/CNPE), Istio 1.29, Ubuntu 24.04 for LFCS
- `goldenkube license` (EULA, accepted once on first use), `goldenkube upgrade`, daily release check

## Status, honestly
- CKA, CKAD and CKS scenarios were verified on live clusters on macOS (Apple Silicon).
- ICA, LFCS and CNPE scenarios are published as **preview**: their task text and graders are complete, but
  they have not yet been run end to end on a VM. Report problems with `goldenkube diagnostics --bundle`.
- Linux (amd64/arm64): the same engine; verified on a Linux host before this release.
- macOS binaries are not Apple-signed or notarized in this release. Install with the script (curl downloads
  carry no quarantine flag); a browser-downloaded archive will be blocked by Gatekeeper.

## Verify
- `goldenkube_0.1.0_checksums.txt` lists the SHA-256 of every asset
- `goldenkube_0.1.0_checksums.txt.minisig` is its minisign signature; public key: https://goldenkube.dev/cli/release-key.pub
- `minisign -Vm goldenkube_0.1.0_checksums.txt -P <public key>` then `sha256sum -c --ignore-missing goldenkube_0.1.0_checksums.txt`

## Legal
EULA (https://goldenkube.dev/cli/license), privacy notice and third-party notices ship inside every archive
and are kept in this repository. GoldenKube is not affiliated with CNCF or The Linux Foundation.
