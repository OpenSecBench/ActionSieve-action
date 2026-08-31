# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability, please report it via
[GitHub's private vulnerability reporting](https://github.com/OpenSecBench/ActionSieve-action/security/advisories/new).
**Do not open a public issue.**

You should receive an acknowledgment within 48 hours.

## Scope

This repo contains a GitHub Action wrapper — a composite action that
installs and runs [ActionSieve](https://github.com/OpenSecBench/ActionSieve).
For vulnerabilities in the scanner itself, report to the
[main repo](https://github.com/OpenSecBench/ActionSieve/security/advisories/new).

Security-relevant areas in this action:

- **Input handling** — all inputs are passed via environment variables,
  never interpolated directly into shell commands
- **Action pinning** — all `uses:` references are pinned to SHA
- **SARIF upload** — results go only to the calling repo's Code Scanning
