# GoldenKube CLI v0.1.2


### Fixed
- `goldenkube start` on a machine whose previous run is completed or failed now offers to destroy that run and continue
  (on a terminal); the non-interactive hint says `goldenkube destroy && goldenkube start <id>` instead of suggesting `submit`.
- Progress lines are no longer printed twice when a step is reported as both an event and a log line (`cloning`, `sizing`,
  `purging`).

### Changed
- `goldenkube task --hints` ends with a reminder that node commands in hints (crictl, journalctl, systemctl, etcdctl, files
  under /etc/kubernetes) assume a root shell (`sudo -i`), as on the real exam.
- The cluster/task lines after `start` and the `goldenkube shell` banner say that goldenkube runs on your own machine (second
  terminal), not inside the node, and how to get root on the node.

Install or upgrade: `curl --proto '=https' --tlsv1.2 -sSf https://goldenkube.dev/install.sh | sh`, or `goldenkube upgrade` on an
existing install. Checksums are signed with minisign (public key: https://goldenkube.dev/cli/release-key.pub).
