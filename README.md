# GitHub Actions Workflow Project

This repository contains a reusable GitHub Actions workflow that can be integrated into your own repositories to automate the CI/CD pipeline for your project.

## How to Use in Main Branch

To use this workflow in your repository, follow these steps:

1. **Create a new YAML file** in your `.github/workflows` directory (e.g., `main.yaml`).
   
2. **Copy the following configuration** into your workflow file:

```yaml
name: Main Branch Workflow

on:
  push: # Trigger the workflow on push events
    branches:
      - main  # Run the workflow only when there's a push to the 'main' branch

permissions:
  contents: write # Allows to write to the repository

jobs:
  use-shared-workflow:
    uses: ilMatty98/workflow/.github/workflows/{file_name}.yaml@master
    secrets: inherit  # To inherit secrets from the repository
```

## How to Use with other branch

To use this workflow in your repository, follow these steps:

1. **Create a new YAML file** in your `.github/workflows` directory (e.g., `pull_request.yaml`).
   
2. **Copy the following configuration** into your workflow file:

```yaml
name: Pull Request Workflow

on:
  pull_request: # Trigger the workflow on pull requests
    branches:
      - main  # Run the workflow only if the pull request is targeted to the 'main' branch
    types:
      - opened  # Run the workflow when a pull request is opened
      - synchronize  # Run the workflow when a pull request is updated

permissions:
  contents: write # Allows to write to the repository

jobs:
  use-shared-workflow:
    uses: ilMatty98/workflow/.github/workflows/{file_name}.yaml@master
    secrets: inherit  # To inherit secrets from the repository


