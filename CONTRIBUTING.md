# Contributing

This repo contains the GitHub Action wrapper for
[ActionSieve](https://github.com/OpenSecBench/ActionSieve).

## What goes where

- **Scanner bugs/features** → [OpenSecBench/ActionSieve](https://github.com/OpenSecBench/ActionSieve/issues)
- **Detection patterns** → [OpenSecBench/ActionSieve-corpus](https://github.com/OpenSecBench/ActionSieve-corpus)
- **Action wrapper issues** → this repo

## Guidelines

- All `uses:` references must be pinned to SHA
- Inputs must be passed via environment variables, never interpolated
  directly into `run:` blocks
- Test changes against a real workflow before submitting
