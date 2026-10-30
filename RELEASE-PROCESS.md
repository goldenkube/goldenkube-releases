# Release process (public summary)

What every GoldenKube CLI release goes through before it appears here. The build itself runs from the
private source repository; this repository only ever receives built artifacts and these documents.

1. Build: reproducible Go builds for darwin/arm64, darwin/amd64, linux/amd64, linux/arm64 (`-trimpath`,
   stripped), plus `.deb` and `.rpm` packages for Linux and an SPDX SBOM per archive.
2. Checksums: `goldenkube_<version>_checksums.txt` with the SHA-256 of every asset.
3. Signature: the checksums file is signed with minisign (Ed25519) using the GoldenKube release key;
   public key in SECURITY.md and at https://goldenkube.dev/cli/release-key.pub. `goldenkube upgrade`
   and the install script verify this signature before installing anything.
4. Legal files: EULA.md, PRIVACY-NOTICE.md and THIRD-PARTY-NOTICES.md (generated from the exact
   dependency graph of the build) are packaged in every archive and kept in this repository.
5. Publish: a draft GitHub release is created with all assets and reviewed by hand; the release pointer
   https://goldenkube.dev/cli/latest.json is updated only after every asset is downloadable, which is
   what makes installed CLIs announce the new version.
6. macOS code signing and notarization, and the Homebrew Cask, are added once the Apple Developer
   enrollment is complete; until then macOS installs go through the install script.

Rollback: a bad release is unpublished and the pointer is moved back; `goldenkube upgrade` then offers
the previous version again.
