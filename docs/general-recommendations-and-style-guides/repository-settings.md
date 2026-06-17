---
title: Repository settings
parent: General recommendations and style guides
nav_order: 3
---

# Repository settings
{: .no_toc }

## Table Of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## General settings

In the 'Code' tab:
- Edit repository details:
  - Disable Releases and Packages
  - Add Description and Website if needed

In the 'Settings' tab:
- Branch name must be `main`
- [ ] Wikis
- [x] Automatically delete head branches


## Default branch policy

Create a new **ruleset** calles "Default branch policy". It must be **active** and have `Default` branch as **targeted**.

### For big repositories that require reviews

Examples: site backend, site frontend, other critical repositories.

- [ ] Restrict creations
- [ ] Restrict updates
- [x] Restrict deletions
- [ ] Requite linear history
- [x] Require deployments to succeed **(IF YOU NEED THIS)**
- [ ] Require signed commits
- [x] Require a pull request before merging
    - Required approvals: 1
    - [x] Dissmiss state pull request when new commits are pushed
    - [ ] Require review from specific teams
    - [ ] Require review from Code Owners
    - [x] Require approval of the most recent reviewable push
    - [ ] Require conversation resolution before merging
- [x] Require status checks to pass **(THEN YOU HAVE CI/CD TESTS)**
    - [ ] Require branches to be up to date before merging
    - [x] Do not require status checks on creation
- [x] Block force pushes
- [ ] Require code scanning results
- [ ] Require code quality results
- [ ] Automatically request Copilot code review

---

### For small repositories that not require reviews

Examples: docs repositories.

For such repositories rulest is optional, but good to have.

- [ ] Restrict creations
- [ ] Restrict updates
- [x] Restrict deletions
- [ ] Requite linear history
- [ ] Require deployments to succeed
- [ ] Require signed commits
- [ ] Require a pull request before merging
- [ ] Require status checks to pass
- [x] Block force pushes
- [ ] Require code scanning results
- [ ] Require code quality results
- [ ] Automatically request Copilot code review


## Post configuration setup

- Open 'Projects' tab and *link repo to the project*
- [Add labels to the repository](../github-issues-and-pull-requests/#how-to-copy-labels-from-one-repo-to-another)
