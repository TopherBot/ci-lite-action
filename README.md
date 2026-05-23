# ci‑lite‑action

A **tiny** GitHub Action that makes sure your repository contains the two most important files for open‑source projects:

- `README.md`
- `LICENSE`

If either file is missing the action fails the workflow, emitting a clear error message.

## Usage

Add a workflow file (e.g. `.github/workflows/validate-docs.yml`) that invokes the action:

```yaml
name: Docs Validation
on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  validate-docs:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: ./
```

The `uses: ./` line tells GitHub to run the action defined in this repository.

## Why a tiny action?

- **Zero dependencies** – pure Bash script, no Docker or Node runtime.
- **Instant feedback** – fails in seconds, keeping CI fast.
- **Extensible** – you can add more checks (e.g., `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`) by editing `action.yml`.

## Contributing

Feel free to open a PR to add more documentation checks or improve the error messages. All contributions should pass the existing workflow.

## License

This project is released under the MIT License – see the `LICENSE` file.
