# GoldenKube CLI v0.1.1

Maintenance release, one day after v0.1.0. No behaviour change for labs or grading.

- `goldenkube license --status` now notes when the licence text was revised within the same version (wording only; no
  re-acceptance). The EULA 1.0 text is pinned to its version in the test suite.
- Help text links to https://goldenkube.dev/cli (the old /docs/cli address redirects there).
- Privacy notice: the EU representative is listed with postal address and email only.
- Internal: unused code removed; the release preflight now runs gofmt, vet, staticcheck and the unit tests before every
  build.

Install or upgrade: `curl --proto '=https' --tlsv1.2 -sSf https://goldenkube.dev/install.sh | sh`, or `goldenkube upgrade`
on an existing install. Checksums are signed with minisign (public key: https://goldenkube.dev/cli/release-key.pub).
macOS binaries are not Apple-signed; install with the script. CKA, CKAD and CKS labs are available; ICA, LFCS and CNPE
labs are in preview.
