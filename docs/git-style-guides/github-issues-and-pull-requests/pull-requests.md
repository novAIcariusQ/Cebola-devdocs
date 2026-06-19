---
title: Pull requests
parent: Github issues and pull requests
nav_order: 3
---

# Pull requests
{: .no_toc }

## Table Of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Title and tense

For those recommendations visit [this page](../).


## Branch naming

Branch name must be structured as follows:
> [\<type\>](../../commits/#types)/[\<optional scope\>](../../commits/#scopes)/\<**optional name**\>

**Optional name** is the [description part of the title](../../commits/#description) shortened to about one or two words for pull request. You can use it even then a scope isn't specified.

Examples:
  - `feat/merchant/shop_status` - type/scope/name
  - `feat/customer/stripe` - type/scope/name
  - `feat/comment` - type/name
  - `cl/grafana` - type/name
  - `docs/merchant` - type/scope


## Description

Description contains a concise description of changes made by pull request.

It's mostly enough to just put an *unordered list with all commits made by the change*. For that you can use `gihub-cli`.

---

### How to create a pull request from command line?

If you've already installed `github-cli` and run `gh auth login`, then run the following from your local branch:
```text
gh pr create
```

This will create a pull request and if you press `e` then it prompts you to edit it's description it will open the **editor** you set with `git config core.editor <editor>` and will have an *unordered list with all commit messages from your local branch* as it's content. (It surrounds all list items with asterisks (\*\*) for some reason, I recommend you to remove them.)


## Delevopment

When creating a pull request, you **must** specify which issues your pull request closes, if any.


## After your pull request is ready

If your pull request is ready for review, *assign a reviewer* and wait.
