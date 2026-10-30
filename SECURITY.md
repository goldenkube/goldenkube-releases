# Security policy

## Reporting a vulnerability
Email **security@goldenkube.dev** (also reachable via hello@goldenkube.dev). Please include the CLI
version (`goldenkube version`), your OS, and steps to reproduce. You will get an acknowledgement
within 3 working days. Do not open a public issue for a security problem.

Machine-readable contact: https://goldenkube.dev/.well-known/security.txt

## Scope
- The `goldenkube` CLI and its release artifacts in this repository
- The website and API at goldenkube.dev

Practice clusters run inside local virtual machines on your own computer; the CLI never has
access to any other cluster of yours.

## Verifying a release
Every release carries:
- `goldenkube_<version>_checksums.txt`: SHA-256 of every archive and package
- `goldenkube_<version>_checksums.txt.minisig`: a [minisign](https://jedisct1.github.io/minisign/)
  signature of that file, made with the GoldenKube release key

Release public key (also at https://goldenkube.dev/cli/release-key.pub):

```
RWSTRT/BBW6baL71uc+1ShS2d5isAHTDR/hbUugYIDFXLXb9h0lal+8y
```

Verify by hand:

```
minisign -Vm goldenkube_<version>_checksums.txt -P RWSTRT/BBW6baL71uc+1ShS2d5isAHTDR/hbUugYIDFXLXb9h0lal+8y
sha256sum -c --ignore-missing goldenkube_<version>_checksums.txt
```

`goldenkube.dev/install.sh` verifies the signature when `minisign` is installed and always
verifies the SHA-256; `goldenkube upgrade` verifies the signature itself (the public key is built
into the CLI). macOS builds are not yet Apple-signed or notarized (install with the script; a browser download would be stopped by Gatekeeper); that is planned once the Apple Developer enrollment completes.

## Supported versions
Only the latest release receives fixes. `goldenkube upgrade --check` reports whether you are on it.
