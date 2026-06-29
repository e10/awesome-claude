# Awesome Claude Skills [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A tight, curated shortlist of open-source **Claude / AI-agent skills** you can drop
> into your coding agent (Claude Code, Cursor, Codex, Copilot, and friends) to build
> better apps faster.

Every project below is open source and **takes PR contributions**. New skills are
welcome here too; see [Contributing](#contributing).

## Contents

- [What is a skill?](#what-is-a-skill)
- [Frontend & Design](#frontend--design)
- [Documents & Data](#documents--data)
- [Dev & Tooling](#dev--tooling)
- [App Frameworks](#app-frameworks)
- [Integrations](#integrations)
- [Contributing](#contributing)

## What is a skill?

A **skill** is a portable bundle of instructions, rules, and sometimes commands that
teaches an AI coding agent how to do something well. You install it into your agent and
its output for that task gets better — no fine-tuning required.

## Frontend & Design

- **[taste-skill](https://github.com/Leonxlnx/taste-skill)** — *"The Anti-Slop Frontend
  Framework for AI Agents."* Steers agents toward polished typography, spacing, motion,
  and layout. Framework-agnostic. `npx skills add`.

- **[impeccable](https://github.com/pbakaus/impeccable)** — *"The design language that
  makes your AI harness better at design."* Design commands plus deterministic detectors
  for common anti-patterns. `npx impeccable install`.

## Documents & Data

- **[markitdown](https://github.com/microsoft/markitdown)** — Microsoft's utility for
  converting PDF, Office, images, audio, HTML, and more into clean, LLM-friendly
  Markdown. CLI or Python API.

- **[Anthropic document skills](https://github.com/anthropics/skills)** — Official
  `docx`, `pdf`, `pptx`, and `xlsx` skills to create, edit, and analyze Office files
  with formatting, formulas, and charts.

## Dev & Tooling

- **[MCP Builder](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/mcp-builder)**
  — Guides the agent through building MCP servers to give Claude new capabilities.

- **[Webapp Testing](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/webapp-testing)**
  — Tests local web apps with Playwright, capturing screenshots to validate behavior.

## App Frameworks

- **[agent-native](https://github.com/BuilderIO/agent-native)** — *"A framework for
  building agent-native applications."* Define an action once; it works across web UI,
  API, CLI, and MCP. Ships templates with full code ownership.

## Integrations

- **[Connect](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/connect)**
  — Links Claude to 500+ apps (email, Slack, issues, and more) so it can take real
  actions across your stack.

- **[GitHub Automation](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/github-automation)**
  — Automate issues, PRs, repos, branches, and Actions.

- **[Slack Automation](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/slack-automation)**
  — Automate messages, channels, search, reactions, and threads.

- **[Stripe Automation](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/stripe-automation)**
  — Automate charges, customers, products, and subscriptions — useful for monetizing an app.

- **[Notion Automation](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/notion-automation)**
  — Automate pages, databases, blocks, comments, and search.

- **[n10-link](https://github.com/e10/awesome-claude/tree/main/n10-link)** — Shorten
  and manage short links with [n10](https://n10.in) right from your agent: create a
  short link (with optional custom slug), list links and click counts, look one up,
  or delete it. Drives the n10 MCP server (`shorten_link`, `list_links`, `get_link`,
  `delete_link`) with a REST `curl` fallback. Connect with
  `claude mcp add --transport http n10 https://n10.in/api/mcp --header "Authorization: Bearer n10_sk_xxx"`.

## Research & Writing

- **[recursive-research](https://github.com/ComposioHQ/awesome-claude-skills)** —
  Recursive, multi-level research across any domain with source tiering for credibility.

- **[Content Research Writer](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/content-research-writer)**
  — Researches a topic, adds citations, and sharpens hooks to produce publish-ready content.

## Contributing

Contributions are welcome! To add a skill:

1. Make sure the project is open source and accepts PR contributions.
2. Add it to the most fitting category with a bold linked name and a one-line
   description (quote the project's own tagline where you can).
3. Keep it concise — this is a shortlist, so only the genuinely useful.
4. Open a pull request.

---

Curated from [anthropics/skills](https://github.com/anthropics/skills) and
[ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills).
