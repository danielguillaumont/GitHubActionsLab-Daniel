# GitHubActionsLab-Daniel
# GitHub Actions Dependent Jobs Lab

## Overview

This repository demonstrates how **GitHub Actions workflows can run multiple jobs with dependencies**.
The workflow is triggered whenever code is pushed to the **main branch** and executes a sequence of jobs that depend on each other.

The goal of this lab is to understand how to control the **execution order of jobs** using the `needs` keyword in GitHub Actions.

---

## Workflow Description

The workflow contains **three jobs**:

1. **Build Job**

   * Runs first
   * Simulates a build process

2. **Test Job**

   * Runs only after the build job completes successfully
   * Simulates running tests

3. **Deploy Job**

   * Runs after the test job finishes
   * Simulates deploying an application

The dependency chain is implemented using:

```
needs: build
needs: test
```

This ensures the jobs run in the following order:

```
Build → Test → Deploy
```

---

## Workflow Trigger

The workflow runs automatically when code is pushed to the **main branch**.

```
on:
  push:
    branches:
      - main
```

---

## Repository Structure

```
.github/
 └── workflows/
     └── dependent-jobs.yml
```

The workflow file located in `.github/workflows` defines the jobs and their dependencies.

---

## Example Output

When the workflow runs in GitHub Actions, the jobs execute sequentially:

```
Build job running...
Test job running...
Deploy job running...
```

Each job runs on a **GitHub-hosted Ubuntu runner**.

---

## Purpose of the Lab

This project demonstrates:

* Creating GitHub Actions workflows
* Structuring multiple jobs
* Managing job execution order
* Using the `needs` dependency feature
* Understanding CI/CD workflow automation

---

## Author

Daniel Guillaumont
Sheridan College – Software Development & Network Engineering
