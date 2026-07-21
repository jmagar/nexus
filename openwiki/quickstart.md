---
type: Quickstart
title: OpenWiki quickstart
description: Entry point for this repository's generated OpenWiki documentation, focused on the recurring documentation update pipeline and its generated outputs.
tags: [openwiki, documentation]
timestamp: 2026-07-21T09:01:20Z
---

# OpenWiki quickstart

This repository's wiki is minimal and currently documents only its **OpenWiki automation surface**. Start here, then follow the links below for the canonical details.

## What this wiki covers

- [OpenWiki update workflow](./openwiki-update-workflow.md): the authoritative guide for how repository documentation is regenerated.
- Repo instruction files surfaced by the workflow: [`AGENTS.md`](../AGENTS.md), [`CLAUDE.md`](../CLAUDE.md).
- This file is the single entrypoint for future updates until more source domains are added.

## Current documentation status

The working tree currently has a modified `.github/workflows/openwiki-update.yml` from commit `24418bce8af9b818cc32fcba6d95808a55e61bc7`, and this page reflects that changed execution path.

## For future updates

When the workflow file changes again, prefer a surgical update:

1. Confirm the changed source files with `git status --short` and `git show`.
2. Update only the affected concept pages under `/openwiki`.
3. Keep changes focused; avoid source-map or formatting-only edits unless evidence requires it.
4. Ensure any temporary planning file is removed before finishing.

## Backlog

- **Source code + runtime domain docs**: no application runtime source directories were found in the repository root tree (`/.github`, `/openwiki`, `/skills`, `AGENTS.md`, `CLAUDE.md` only).
  Source anchor: repository root discovery from `ls /`.
  Reason: there is nothing beyond workflow, instruction, and tooling-configuration files to document yet.
