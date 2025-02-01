# GitHub Actions Workflow Project

This repository contains a reusable GitHub Actions workflow that can be integrated into your own repositories to
automate the CI/CD pipeline for your project.

---

## Quarkus Maven GraalVM17 / Temurin21 for deployment on Google Kubernetes Engine (GKE)

### Step

1. Set the new version of the pom.xml
2. Commit and push the updated pom.xml
3. Perform static code analysis with SonarCloud
4. Build and push the Docker image to Docker Hub
5. Deploy the Docker image from Docker Hub to Google Kubernetes Engine (GKE)

### Secrets to set on the repository

| Type       | Key                        | Value                                                                                                        |
|------------|----------------------------|--------------------------------------------------------------------------------------------------------------|
| Github     | GIT_HUB_EMAIL              | GitHub account email                                                                                         |
| Github     | GIT_HUB_NAME               | GitHub account username                                                                                      |
| Github     | GIT_HUB_TOKEN              | Github personal access token </br> GitHub settings -> Developer settings -> Personal access tokens -> Tokens |
| SonarCloud | SONAR_HOST_URL             | SonarCloud Url </br> https://sonarcloud.io/                                                                  |
| SonarCloud | SONAR_ORGANIZATION         | Name of the organization </br> Administration -> Organization Settings                                       |
| SonarCloud | SONAR_PROJECT_KEY          | Project Key of the project created </br> Project -> Administration -> Update Key -> Project Key              |
| SonarCloud | SONAR_TOKEN                | Authentication token </br> My Account -> Security -> Generate Tokens                                         |
| Docker Hub | DOCKER_HUB_USERNAME        | Docker Hub Username                                                                                          |
| Docker Hub | DOCKER_HUB_TOKEN           | Authentication token </br> Account settings -> Personal access tokens -> Generate new token                  |
| Docker Hub | DOCKER_HUB_REPOSITORY_NAME | Name of the repository created on Docker Hub                                                                 |
| GKE        | GKE_SA_KEY                 | Authentication Json </br> IAM & Admin -> Service Accounts                                                    |
| GKE        | GKE_PROJECT                | Project name on Google Cloud                                                                                 |
| GKE        | GKE_CLUSTER                | Cluster name on Kubernetes Engine                                                                            |
| GKE        | GKE_ZONE                   | Cluster zone on Kubernetes Engine                                                                            |
| GKE        | GKE_DEPLOYMENT_NAME        | Deployment name on Kubernetes Engine </br> deployment.yaml -> metadata -> name                               |
| GKE        | GKE_NAMESPACE              | Namespace name on Kubernetes Engine </br> deployment.yaml -> metadata -> namespace                           |

### How to Use in Main Branch

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

### How to Use with other branch

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
```

---

## Quarkus Maven Temurin21

### Step

1. Set the new version of the pom.xml
2. Commit and push the updated pom.xml
3. Perform static code analysis with SonarCloud
4. Build and push the Docker image to Docker Hub


### Secrets to set on the repository

| Type       | Key                        | Value                                                                                                        |
|------------|----------------------------|--------------------------------------------------------------------------------------------------------------|
| Github     | GIT_HUB_EMAIL              | GitHub account email                                                                                         |
| Github     | GIT_HUB_NAME               | GitHub account username                                                                                      |
| Github     | GIT_HUB_TOKEN              | Github personal access token </br> GitHub settings -> Developer settings -> Personal access tokens -> Tokens |
| SonarCloud | SONAR_HOST_URL             | SonarCloud Url </br> https://sonarcloud.io/                                                                  |
| SonarCloud | SONAR_ORGANIZATION         | Name of the organization </br> Administration -> Organization Settings                                       |
| SonarCloud | SONAR_PROJECT_KEY          | Project Key of the project created </br> Project -> Administration -> Update Key -> Project Key              |
| SonarCloud | SONAR_TOKEN                | Authentication token </br> My Account -> Security -> Generate Tokens                                         |
| Docker Hub | DOCKER_HUB_USERNAME        | Docker Hub Username                                                                                          |
| Docker Hub | DOCKER_HUB_TOKEN           | Authentication token </br> Account settings -> Personal access tokens -> Generate new token                  |
| Docker Hub | DOCKER_HUB_REPOSITORY_NAME | Name of the repository created on Docker Hub                                                                 |

### How to Use in Main Branch

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

### How to Use with other branch

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
```
---