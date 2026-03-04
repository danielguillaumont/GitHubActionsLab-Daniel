# GitHubActionsLab-Daniel

GitHub Actions CI/CD Workflow Lab

## Overview

This repository demonstrates how GitHub Actions workflows can automate tasks using multiple jobs and different operating systems. The purpose of this lab is to understand how workflows are triggered, how job dependencies work, and how jobs can run in parallel on different platforms.

Two workflows are implemented in this repository:

1. **Dependent Jobs Workflow** – Demonstrates sequential job execution using dependencies.
2. **Multi-Platform Workflow** – Demonstrates running multiple independent jobs simultaneously on different operating systems.

These workflows are located in the `.github/workflows` directory.

---

# Workflow 1 – Dependent Jobs

The first workflow demonstrates how to control the order in which jobs run using the `needs` keyword.

### Trigger

The workflow runs automatically when code is pushed to the **main branch**.

```
on:
  push:
    branches:
      - main
```

### Jobs

The workflow contains three jobs that run in sequence:

1. **Build Job**

   * Runs first
   * Simulates a build process

2. **Test Job**

   * Runs after the build job completes
   * Simulates running tests

3. **Deploy Job**

   * Runs after the test job completes
   * Simulates deployment

### Dependency Structure

```
build → test → deploy
```

This execution order is enforced using:

```
needs: build
needs: test
```

This ensures that each job waits for the previous job to complete successfully before starting.

---

# Workflow 2 – Multi-Platform Testing

The second workflow demonstrates how GitHub Actions can run jobs simultaneously across multiple operating systems.

### Trigger

The workflow runs when code is pushed to the **main branch**.

```
on:
  push:
    branches:
      - main
```

### Jobs

Three independent jobs are created, each running on a different operating system:

* **ubuntu-job**
* **windows-job**
* **macos-job**

Each job performs the following steps:

1. Checks out the repository using `actions/checkout@v4`
2. Displays operating system information
3. Executes an OS-specific command
4. Creates a simple file and prints its contents

Example commands used:

**Linux / macOS**

```
uname -a
```

**Windows**

```
systeminfo
```

Since no dependencies are defined, all jobs run **in parallel**.

---

# Repository Structure

```
GitHubActionsLab-Daniel
│
README.md
│
.github
   └── workflows
        dependent-jobs.yml
        multi-platform.yml
```

---

# Screenshots

### Dependent Jobs Workflow

This screenshot shows the sequential execution of jobs.

```
build → test → deploy
```

### Multi-Platform Workflow

This screenshot shows three independent jobs running on different operating systems.

```
ubuntu-job
macos-job
windows-job
```

---

# Purpose of the Lab

This lab demonstrates the following GitHub Actions concepts:

* Creating workflows
* Defining multiple jobs
* Managing job dependencies
* Running jobs in parallel
* Using different operating systems in CI/CD pipelines

---

# Author

**Daniel Guillaumont**
Sheridan College
Software Development & Network Engineering
