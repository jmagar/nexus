---
type: Workflow
title: OpenWiki documentation update workflow
description: Explains how this repository regenerates OpenWiki documentation via scheduled or manual GitHub Actions execution.
tags: [openwiki, ci, github-actions, documentation]
timestamp: 2026-07-21T09:01:20Z
resource: .github/workflows/openwiki-update.yml
---

# OpenWiki documentation update workflow

This page documents the workflow in [`.github/workflows/openwiki-update.yml`](../.github/workflows/openwiki-update.yml).

## Execution model

- Triggered by both `workflow_dispatch` and a daily cron schedule (`0 8 * * *`).
- A single `update` job runs on `ubuntu-latest`.
- Steps currently:
  - Checkout repository (`actions/checkout@v4`).
  - Set up Node.js 22 (`actions/setup-node@v4`).
  - Install OpenWiki globally (`npm install --global openwiki`).
  - Run `openwiki code --update --print`.

## OpenAI provider configuration

The current workflow passes the following environment to the OpenWiki step:

- `OPENWIKI_PROVIDER: openrouter`
- `OPENROUTER_API_KEY`
- `OPENWIKI_MODEL_ID: z-ai/glm-5.2`
- LangSmith tracing settings:
  - `LANGSMITH_API_KEY`
  - `LANGCHAIN_PROJECT: openwiki`
  - `LANGCHAIN_TRACING_V2: true`

## Pull-request publishing

The workflow creates an update PR using `peter-evans/create-pull-request@22a9089034f40e5a961c8808d113e2c98fb63676` and includes:

- `openwiki`
- `AGENTS.md`
- `CLAUDE.md`
- `.github/workflows/openwiki-update.yml`

This ensures repository instruction and workflow files are refreshed alongside generated documentation.

## Notable change from previous revision

Compared with the previous committed version, the update command switched to `openwiki code --update --print` with OpenRouter credentials, while removing Tailscale networking/provisioning and openai-compatible preflight logic.

## Backwards links

- The workflow is the execution source for the repository wiki entrypoint documented in [quickstart](./quickstart.md).
