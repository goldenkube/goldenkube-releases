# Release Process

Checklist for publishing a GoldenKube CLI release. Nothing here is automated yet; no public release
has been made. Version below is `X.Y.Z`; tag is `vX.Y.Z`.

## Prerequisites (not yet in place)
- [ ] Apple Developer Program membership, "Developer ID Application" certificate in the build keychain
- [ ] `notarytool` credentials stored (`xcrun notarytool store-credentials`) - never in a repo
- [x] `EULA.md` and `PRIVACY-NOTICE.md` filled in (2026-10-28; decisions delegated by the owner; not reviewed by a lawyer)

## Steps
1. [ ] In `goldenkube-cli`, tag `vX.Y.Z` on a green main; all tests and scenario self-tests pass.
2. [ ] Build darwin arm64 and darwin amd64 binaries (`GOOS=darwin GOARCH=<arch>`), version stamped.
3. [ ] Codesign each binary: `codesign --force --options runtime --timestamp --sign "Developer ID Application: <name> (<team>)" goldenkube`
4. [ ] Notarize: zip the signed binary, `xcrun notarytool submit <zip> --keychain-profile <profile> --wait`; confirm status Accepted.
5. [ ] No staple: Apple documents that tickets for standalone binaries cannot be stapled (https://developer.apple.com/documentation/security/customizing-the-notarization-workflow); Gatekeeper looks the ticket up online on first run. Verify with `codesign -vvvv -R="notarized" --check-notarization goldenkube` (fatal) and treat `spctl --assess --type execute` as advisory; then run a quarantined download on a clean Mac.
6. [ ] Package: `goldenkube_X.Y.Z_darwin_arm64.tar.gz` and `goldenkube_X.Y.Z_darwin_amd64.tar.gz`, each with `goldenkube` at the archive root (matches Cask `binary "goldenkube"`) and `completions/goldenkube.{bash,zsh,fish}` (matches the Cask completion stanzas).
7. [ ] Checksums: `shasum -a 256 *.tar.gz > checksums.txt`.
8. [ ] Regenerate `THIRD-PARTY-NOTICES.md` (see that file); include `EULA.md` and `PRIVACY-NOTICE.md`.
9. [ ] Create GitHub Release `vX.Y.Z` in `goldenkube/goldenkube-releases` with the two tarballs, `checksums.txt`, and notices.
10. [ ] In `goldenkube/homebrew-tap`, update `Casks/goldenkube.rb`: `version`, both `sha256` values; commit.
11. [ ] `brew style --cask` and `brew audit --cask --strict --online goldenkube/tap/goldenkube` (tap locally via `brew tap goldenkube/tap <path>`; `brew trust` it) - must be clean.
12. [ ] Test on a clean Mac: `brew install --cask goldenkube/tap/goldenkube`, `goldenkube --version`, `goldenkube doctor`; then publish an older test version and run `brew upgrade --cask goldenkube`; then `brew uninstall --cask --zap goldenkube`.
13. [ ] Push the Cask change only after steps 9-12 pass. Record the release in `goldenkube-helpers/PROGRESS.md`.

## Rollback
Delete/yank the GitHub Release and revert the Cask commit; users on a bad version upgrade once the fixed version is published.


## Automation status (2026-10-28)
The private CLI repo now carries the scripted flow (`make snapshot / release-dry / release / notices / cask`, `scripts/release/*`, `docs/RELEASE.md`). This document remains the human checklist; the scripts implement it. Signing/notarization still need the owner's Developer ID certificate and notary profile.
