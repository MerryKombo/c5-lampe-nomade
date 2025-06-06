# GitHub Action: Build and Commit Wireviz Output on PR Creation

## Overview

This document describes a GitHub Action workflow that automatically builds the PNG, SVG, and HTML output files from a Wireviz definition (`lampe-wireviz.yml`) whenever a pull request (PR) is created. The workflow also commits and pushes these generated files back to the PR branch.

---

## Workflow Steps

1. **Trigger:** The workflow runs on every pull request that modifies `lampe-wireviz.yml`.
2. **Checkout:** The PR branch is checked out.
3. **Set up Python:** Python is installed on the runner.
4. **Install Wireviz:** Wireviz is installed using `pip`.
5. **Run Wireviz:** The command `wireviz lampe-wireviz.yml` is executed to generate all output files.
6. **Commit and Push:** The generated files are added, committed, and pushed to the current PR branch.

---

## GitHub Actions Workflow YAML

```yaml
name: Build and Commit Wireviz Output

on:
  pull_request:
    paths:
      - 'lampe-wireviz.yml'

jobs:
  build-wireviz:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - name: Checkout PR branch
        uses: actions/checkout@v4
        with:
          persist-credentials: true

      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.x'

      - name: Install Wireviz
        run: pip install wireviz

      - name: Generate output files with Wireviz
        run: wireviz lampe-wireviz.yml

      - name: Commit and push generated files
        run: |
          git config --global user.name "github-actions[bot]"
          git config --global user.email "github-actions[bot]@users.noreply.github.com"
          git add .
          git diff --cached --quiet || git commit -m "Auto-generate Wireviz output files"
          git push
```

---

## Notes

- **Permissions:** The workflow requires `contents: write` permissions to push changes to the PR branch.
- **Wireviz Output:** Ensure that `lampe-wireviz.yml` is present in the repository root or update the workflow path accordingly.
- **Commit Behavior:** The workflow will only commit and push if there are changes in the generated files.

---

## Usage

1. Copy the above workflow YAML into `.github/workflows/build-wireviz.yml` in your repository.
2. Ensure `lampe-wireviz.yml` is present and correctly configured.
3. When a PR is created or updated that changes `lampe-wireviz.yml`, the workflow will run, generate the output files, and commit them to the PR branch automatically.
