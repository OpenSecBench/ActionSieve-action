# ActionSieve GitHub Action

Scan your CI/CD pipeline definitions for injection vulnerabilities, supply
chain risks, and misconfigurations.

This is the GitHub Action wrapper for
[ActionSieve](https://github.com/OpenSecBench/ActionSieve), a multi-platform
CI/CD pipeline security scanner.

## Usage

```yaml
- uses: OpenSecBench/ActionSieve-action@v1
  with:
    patterns: path/to/patterns
```

### With GitHub Code Scanning (SARIF)

```yaml
name: Pipeline Security
on:
  push:
    branches: [main]
  pull_request:

permissions:
  security-events: write

jobs:
  scan:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: OpenSecBench/ActionSieve-action@v1
        with:
          patterns: patterns/
          format: sarif
          upload-sarif: "true"
```

### With fail threshold

```yaml
- uses: OpenSecBench/ActionSieve-action@v1
  with:
    patterns: patterns/
    fail-on: high
```

### Pin a specific version

```yaml
- uses: OpenSecBench/ActionSieve-action@v1
  with:
    version: "0.1.0"
    patterns: patterns/
```

## Inputs

| Input | Description | Default |
|-------|-------------|---------|
| `path` | Path to scan | `.` |
| `version` | ActionSieve version (`0.1.0` or `latest`) | `latest` |
| `format` | Output format (`json`, `yaml`, `sarif`, `markdown`, `ocsf`) | `sarif` |
| `platform` | Force platform (auto-detected by default) | |
| `profile` | Environment profile (preset name or path) | |
| `patterns` | Path to pattern catalog | |
| `fail-on` | Fail threshold (`info`, `low`, `medium`, `high`, `critical`) | |
| `show-suppressed` | Include suppressed findings | `false` |
| `online` | Enable online checks (SHA pin verification) | `false` |
| `token` | GitHub token for online checks | `${{ github.token }}` |
| `upload-sarif` | Upload SARIF to Code Scanning | `true` |
| `python-version` | Python version | `3.12` |
| `extra-args` | Additional CLI arguments | |

## Outputs

| Output | Description |
|--------|-------------|
| `findings-count` | Number of findings |
| `exit-code` | Scanner exit code |

## Patterns

ActionSieve requires a pattern catalog to detect vulnerabilities. Patterns
are YAML files that define what to look for. You can:

- Use the community patterns from
  [actionsieve-corpus](https://github.com/OpenSecBench/ActionSieve-corpus)
- Write your own patterns for internal rules
- Combine both

## Other CI platforms

For GitLab CI, Azure Pipelines, and other platforms, see the
[examples](examples/) directory or install ActionSieve directly:

```bash
pip install actionsieve
actionsieve scan --patterns path/to/patterns .
```

## License

MIT
