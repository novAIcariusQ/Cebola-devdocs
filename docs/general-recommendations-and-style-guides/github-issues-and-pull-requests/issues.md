---
title: Issues
parent: Github issues and pull requests
nav_order: 2
---

# Issues
{: .no_toc }

## Table Of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Title and tense

For those recoomendations visit [this page](../).


## Description

The description contains a concise description of an issue.

- For issues with sub-issues, you must summarise everything you need to do to close them all
- For a complex issue that requires several tasks, enumerate each task in a numbered list
- If you can't write a description, that fully describes what and how needs to be done, then add `question` lable


## Project fields

### Priority

Priority goes from highest(P0) to lowest (P4).

- P0 - usually bugs and other security stuff, that needs to be done as fast as possible
- P1 - usually issues that blocks other issues and architecture related, that needs to be done so you can work on other things
- P2 - normal issue priority
- P3 - for less important tasks
- P4 - for not important tasks, can wait

### Size

Size usually depends on scale and complexity of the project and, for example, for some projects XL issues can done in 2 days and for the others in 2 weeks. So that's up to you to pick up best size for the issue. Goes from super large (XL) to super small (XS).

### Estimate

Estimate is the ammount of tasks you need to do. One big task - estimate of 1, one small task - estimate of 1, 5 tasks in one issue - estimate of 5.

- Parent issues, that exist just to tie together and summarise all of it's sub-issues, but itself doesn't have any specific tasks, should have estimate 0

Example of an issue with esimate of 3:
<img src="../../../../assets/images/issues_estimate3_example.png">

Example of an issue with estimate of 0 (just summarises sub-issues):
<img src="../../../../assets/images/issues_estimate0_example.png">


## Relationships

Relationships define connections of an issue with other issues: if it is a parrent, or a child, or blocked by, or blocking some issue. You **must** use them then you can, because they make work much easier.

To switch repository for relationship, click back arrow on the window:
<img src="../../../../assets/images/issues_relationships.png">

### Blocked by/Blocking

If you can't work on an issue, without some other issue being closed, mark it as blocked by that issue.

### Child/Parent

- If you have a complex issue, that requires multiple different changes, then create sub-issues for that issue
- If you have one task that requires to make changes across different repositories, then create sub-issues of this issue in different repositories


## Additional information

If you started working on an issue, please move it to "In progress" column and assign it on yourself.
