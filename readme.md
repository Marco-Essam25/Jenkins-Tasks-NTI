# CI/CD & Jenkins Study Guide

---

## 01) What is CI/CD?

**CI/CD** stands for **Continuous Integration / Continuous Delivery (or Deployment)**.

| Term | Meaning |
|------|---------|
| **CI** (Continuous Integration) | Developers frequently merge code into a shared repo. Each merge triggers automated builds & tests to catch bugs early. |
| **CD** (Continuous Delivery) | Automatically prepares code for release to production after CI passes. A human still approves the final deploy. |
| **CD** (Continuous Deployment) | Every passing build is automatically deployed to production with no manual approval. |

**Goal:** Shorten the feedback loop, reduce manual errors, and ship software faster and more reliably.

---

## 02) Three Popular CI/CD Tools

| # | Tool | Notes |
|---|------|-------|
| 1 | **Jenkins** | Open-source, self-hosted, highly extensible via plugins |
| 2 | **GitHub Actions** | Built into GitHub, YAML-based, cloud-native |
| 3 | **GitLab CI/CD** | Built into GitLab, powerful pipeline system, supports self-hosted |

---

## 03) What is a Jenkins Pipeline?

A **Jenkins Pipeline** is a suite of plugins that lets you define your entire build/test/deploy process as **code** (called a `Jenkinsfile`). It models the software delivery process as a series of **stages** (e.g., Build → Test → Deploy).

Key benefits:
- **Pipeline-as-Code** — stored in your repo alongside your source code
- **Durable** — survives Jenkins restarts
- **Pausable** — can wait for human input
- **Extensible** — supports parallel stages, loops, conditions, and shared libraries

---

## 04) What Language is Jenkins Based On?

Jenkins is built on **Java**. It runs on the JVM and requires a Java runtime (JDK 11 or 17+).

---

## 05) What Scripting Language is Jenkins Pipeline Syntax Based On?

Jenkins Pipeline syntax is based on **Groovy** — a JVM-based scripting language. Both pipeline types (Declarative and Scripted) use Groovy under the hood.

---

## 06) Ways to Write a Pipeline in Jenkins

There are **two** ways:

### A) Declarative Pipeline (recommended)
Structured, opinionated syntax with a defined schema. Easier to read and write.

```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
    }
}
```

### B) Scripted Pipeline
Full Groovy code — more flexible but more complex. Uses `node {}` blocks.

```groovy
node {
    stage('Build') {
        echo 'Building...'
    }
}
```

| | Declarative | Scripted |
|--|-------------|---------|
| Syntax | Structured / opinionated | Full Groovy |
| Validation | Built-in schema validation | None |
| Use case | Most pipelines | Complex custom logic |

