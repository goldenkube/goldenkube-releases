# Third-Party Notices (TEMPLATE)

> **TEMPLATE - not yet generated.** This file is regenerated for every release from the exact Go
> module set compiled into that release's binaries. Do not hand-edit a released copy.

GoldenKube includes software from the third parties listed below, used under their respective licenses.

## How this file is generated (at release time)

From the private `goldenkube-cli` repository, at the release tag:

```sh
go install github.com/google/go-licenses@latest   # pin a version in the release pipeline
GOOS=darwin GOARCH=arm64 go-licenses report ./cmd/goldenkube \
  --template third-party.tpl > THIRD-PARTY-NOTICES.md
# repeat for GOARCH=amd64 and diff; the module sets should match or both be listed
go-licenses check ./cmd/goldenkube --disallowed_types=forbidden,restricted
```

`third-party.tpl` renders, for each module: name, version, license name, and the full license text
(including copyright notices). Release is blocked if `go-licenses check` reports a forbidden or
unknown license. Non-Go components bundled in the artifact (if any) are added by hand.

## Entry format

### <module path> <version>
- License: <SPDX id>
- Source: <URL>

```
<full license text>
```

## Entries

_None yet - generated at release time._

## Tools used but not bundled
Multipass, Kubernetes (kubeadm/kubelet/kubectl), Cilium, and related tools are installed or
downloaded separately into the user's local VMs under their own licenses and are not redistributed
in the GoldenKube binary.
