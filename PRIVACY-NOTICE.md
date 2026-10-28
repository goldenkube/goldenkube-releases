# GoldenKube CLI Privacy Notice

Last updated: 2026-10-28 - Controller: ITEXPERT24 LTD (England and Wales), hello@goldenkube.dev

This notice covers the `goldenkube` command-line tool. The website goldenkube.dev has its own
privacy page (https://goldenkube.dev/privacy).

## What the CLI sends to goldenkube.dev
All requests go over HTTPS to goldenkube.dev and carry a `User-Agent` of the form
`goldenkube-cli/<version> (<os>/<arch>)`, for example `goldenkube-cli/1.0.0 (darwin/arm64)`.

- **Sign-in** (`goldenkube login`, OAuth device flow): the CLI's client id, the requested scopes
  and the API audience; later, the refresh token to renew access. You approve the sign-in in your
  browser. Access and refresh tokens are stored in the macOS Keychain on your machine.
- **Starting a practice run:** scenario id and version, CLI version, start time. For a mock exam
  also: exam id, number of tasks, the drawn scenario ids and versions, and the draw seed.
- **Run progress:** "provisioning started", "ready" or "provisioning failed" with a timestamp. When
  provisioning or setup fails, a short error message is included; Kubernetes bootstrap tokens and
  keys are removed from it before sending, but it can contain local VM names or private IP addresses.
- **Submissions:** for each check its id, pass or fail, points and a failure category (for example
  `mismatch` or `missing`); total and maximum points, pass or fail, time taken, grader version, a
  random submission id and the time of grading.
- **Finishing:** final status (completed, failed, timed out, abandoned), time, duration, and for a
  mock exam the time the exam clock was paused.

When you are offline these items are queued on your machine and sent later in the same form.
`goldenkube doctor` also makes one request without your token to check that goldenkube.dev is
reachable. Your IP address is visible to our hosting provider with every request.

Purpose: sign you in, record and show your progress across devices, and keep the scenario catalog
current. Legal basis: performance of the contract with you (the EULA).

## What the CLI never sends
- Your cluster's contents, kubeconfigs, SSH keys or cluster credentials
- Terminal or shell history, files from your computer, environment variables

Practice clusters run entirely in virtual machines on your machine and grading runs locally.

## Service providers
- Cloudflare: hosting (Workers), database (D1), email sending and routing, bot protection (Turnstile)
- GitHub: release downloads; sign-in when you choose "Sign in with GitHub"
- Google: sign-in when you choose "Sign in with Google"

## Retention
- Account data and CLI run records are kept until you delete your account.
- Request logs of the service are kept by Cloudflare Workers Logs for 7 days (Workers Paid plan,
  https://developers.cloudflare.com/workers/observability/logs/workers-logs/).

## Your rights
You can access, export, correct and delete your data:
- **Export:** goldenkube.dev Settings -> Data & privacy -> Export my progress downloads a JSON file
  that includes your CLI runs, run events, submissions and mock exams.
- **Correct:** change your display name in Settings; for anything else, email us.
- **Devices:** Settings -> Connected devices lists the CLI sessions signed in to your account and
  lets you disconnect them; `goldenkube logout` asks the server to disconnect the current one and
  removes its tokens from the Keychain.
- **Delete:** Settings -> Security -> Delete account. A confirmation link is emailed to you; opening it deletes
  your account, your study data and your CLI run records.
- Or email hello@goldenkube.dev. You can also complain to your data protection authority (in the
  UK, the Information Commissioner's Office).

## Local data
The CLI stores configuration, run state, caches and logs under
`~/Library/Application Support/goldenkube`, `~/Library/Caches/goldenkube` and
`~/Library/Logs/goldenkube`. `brew uninstall --cask --zap goldenkube` removes these folders. It does
not remove the Keychain entry (run `goldenkube logout` first) or practice VMs (run
`goldenkube destroy` first).
