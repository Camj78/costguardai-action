# CostGuardAI GitHub Action

Block unsafe and expensive AI prompts before they reach production.

## Usage

```yaml
- uses: Camj78/costguardai-action@v1
  with:
    fail-on-risk: 70
```

Add this step to any workflow that runs on pull requests. The action fails if the CostGuardAI Safety Score drops below the threshold.

## Inputs

| Input          | Required | Default | Description                                                      |
| -------------- | -------- | ------- | ---------------------------------------------------------------- |
| `fail-on-risk` | No       | `70`    | Fail the workflow if Safety Score falls below this value (0–100) |

## Example workflow

```yaml
name: CostGuardAI
on: [pull_request]

jobs:
  costguard:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: Camj78/costguardai-action@v1
        with:
          fail-on-risk: 70
```

## How it works

Runs the CostGuardAI CLI via `npx @camj78/costguardai@latest ci`.
