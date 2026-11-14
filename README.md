# DevOps Engineering Lab

A lightweight GitHub Actions lab for practicing repository hygiene, scheduled validation, workflow execution and safe automation.

## What this repository currently does

The repository contains a scheduled GitHub Actions workflow that:

- Runs daily and can also be started manually with `workflow_dispatch`.
- Checks that the repository contains a `README.md`.
- Uses read-only repository permissions (`contents: read`).
- Applies a five-minute job timeout and a concurrency group to avoid overlapping runs.
- Explicitly avoids provisioning or modifying cloud infrastructure.

Workflow: [Daily DevOps Repository Checks](.github/workflows/daily-maintenance.yml)

## Run the workflow

1. Open the **Actions** tab.
2. Select **Daily DevOps Repository Checks**.
3. Choose **Run workflow** to trigger a manual execution.
4. Open the run to inspect its job and step logs.

The scheduled workflow runs daily at 12:17 UTC (17:47 India Standard Time).

## Current scope and limitations

This is a small automation exercise, not a full CI/CD platform or infrastructure monitoring system. The current check validates only the presence of the repository README; it does not run application tests, scan dependencies, deploy workloads or inspect AWS resources.

## Planned improvements

- Add Markdown and repository metadata validation.
- Add project-specific linting and test jobs when application code is introduced.
- Publish workflow status and clear failure diagnostics.
- Add reusable workflow patterns and documented examples.
- Keep permissions minimal and avoid cloud credentials unless a future workflow genuinely requires them.

## Safety

No AWS resources are created by the current workflow. Do not commit credentials, access tokens, private keys or other secrets. Any future workflow that needs external access must use narrowly scoped GitHub Actions permissions and repository secrets or OIDC where appropriate.

## Maintainer

[Amit Madakatti](https://github.com/amit-cloudops-ai) · [LinkedIn](https://www.linkedin.com/in/amitops)
