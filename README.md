# Self-Hosted GitHub Actions Runner Setup

## Overview
This repository documents the setup of a self-hosted GitHub Actions runner on my local Windows PC, along with a test workflow to verify that the runner works properly.

## Steps Taken
1. Created a new repository on GitHub (`vigilant-system`).
2. Navigated to **Settings → Actions → Runners**.
3. Added a new **self-hosted runner** (Windows, x64).
4. Followed GitHub’s setup instructions:
   - Downloaded the runner package.
   - Extracted it to `C:\actions-runner`.
   - Configured it using the provided token.
   - Started the runner with:
     ```bash
     run.cmd
     ```
5. Verified that the runner shows as **Idle** in GitHub.

## Test Workflow
I created a simple test pipeline (`.github/workflows/test.yml`) to confirm the runner executes jobs.

```yaml
name: Self-Hosted Runner Test

on: [push]

jobs:
  test:
    runs-on: self-hosted
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4
      - name: Run test command
        run: echo "Runner is working successfully on self-hosted environment!"
