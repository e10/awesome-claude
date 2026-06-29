# Awesome Claude Skills [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of open-source **Claude / AI-agent skills** you can drop into your
> coding agent (Claude Code, Cursor, Codex, Copilot, and friends) to build better
> apps faster.

Every project below is open source and **takes PR contributions** — so if you build
something great, send it back upstream. New skills are welcome here too; see
[Contributing](#contributing).

## Contents

- [What is a skill?](#what-is-a-skill)
- [Frontend & Design](#frontend--design)
- [Document & Content](#document--content)
- [Data & Analytics](#data--analytics)
- [Dev, Testing & Tooling](#dev-testing--tooling)
- [App Frameworks](#app-frameworks)
- [Integrations & Automation](#integrations--automation)
- [Research & Writing](#research--writing)
- [Contributing](#contributing)

## What is a skill?

A **skill** is a portable bundle of instructions, rules, and sometimes commands that
teaches an AI coding agent how to do something well — design a polished UI, edit a
document, query a database, or automate a SaaS app. You install a skill into your agent
and it improves the agent's output for that task, no fine-tuning required.

## Frontend & Design

Skills that give your agent taste — so AI-generated UIs stop looking generic and start
looking intentional.

- **[taste-skill](https://github.com/Leonxlnx/taste-skill)** — *"The Anti-Slop
  Frontend Framework for AI Agents."* Steers coding agents away from generic, repetitive
  UI toward polished typography, spacing, motion, and layout. Ships aesthetic variants
  (soft, brutalist, minimalist), adjustable parameters, and image-to-code workflows.
  Framework-agnostic (React, Vue, Svelte). Install with `npx skills add`.

- **[impeccable](https://github.com/pbakaus/impeccable)** — *"The design language that
  makes your AI harness better at design."* Adds 23 design commands
  (`/impeccable audit`, `/impeccable polish`, `/impeccable critique`, …) plus 44
  deterministic detector rules that catch anti-patterns (overused fonts, purple
  gradients, nested cards, poor contrast) without API calls. Works across Cursor, Claude
  Code, Copilot, Gemini CLI, and more. Install with `npx impeccable install`.

- **[Skills for Design Engineers](https://github.com/emilkowalski/skill)** — Design and
  animation guidelines from Emil Kowalski. Codifies the details agents usually get wrong
  (easing, animation review). Includes `emil-design-eng` and `review-animations`.
  Install with `npx skills@latest add emilkowalski/skills`.

- **[artifacts-builder](https://github.com/anthropics/skills)** — Anthropic's suite of
  tools for creating elaborate, multi-component HTML artifacts for claude.ai — handy for
  building rich interactive previews and prototypes.

- **[Canvas Design](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/canvas-design)**
  — Creates visual art and layouts as PNG/PDF using core design principles. Good for
  social graphics, covers, and quick visual assets.

- **[Theme Factory](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/theme-factory)**
  — Applies professional, cohesive font and color themes to artifacts and documents in
  one step.

## Document & Content

Skills that read, write, and transform real-world documents.

- **[markitdown](https://github.com/microsoft/markitdown)** — Microsoft's lightweight
  Python utility for converting files to Markdown for LLM pipelines. Handles PDF, Word,
  PowerPoint, Excel, images, audio, HTML, EPub, ZIP, and YouTube URLs — preserving
  headings, lists, tables, and links. CLI (`markitdown file.pdf > out.md`) or Python API.

- **[docx](https://github.com/anthropics/skills)** — Anthropic's skill to create, edit,
  and analyze Word documents with tracked changes, comments, and formatting.

- **[pdf](https://github.com/anthropics/skills)** — Extract text, tables, and metadata
  from PDFs, and merge or annotate them.

- **[pptx](https://github.com/anthropics/skills)** — Read, generate, and adjust
  PowerPoint slides, layouts, and templates.

## Data & Analytics

Skills for working with structured data.

- **[xlsx](https://github.com/anthropics/skills)** — Spreadsheet manipulation: formulas,
  charts, and data transformations in Excel.

- **[postgres](https://github.com/ComposioHQ/awesome-claude-skills)** — Execute safe,
  read-only SQL queries against PostgreSQL databases — let the agent explore your data
  without write access.

- **[CSV Data Summarizer](https://github.com/ComposioHQ/awesome-claude-skills)** —
  Auto-analyzes CSV files and generates insights with visualizations.

## Dev, Testing & Tooling

Skills that help you ship and verify code.

- **[MCP Builder](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/mcp-builder)**
  — Guides the agent through building MCP servers to integrate external APIs — the
  standard way to give Claude new capabilities.

- **[Skill Creator](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/skill-creator)**
  — Guidance for authoring effective Claude skills of your own. A good starting point
  before contributing back here.

- **[Webapp Testing](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/webapp-testing)**
  — Tests local web apps with Playwright, capturing screenshots to validate behavior.

- **[Playwright Browser Automation](https://github.com/ComposioHQ/awesome-claude-skills)**
  — Model-invoked Playwright automation for testing and validating web applications.

- **[Changelog Generator](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/changelog-generator)**
  — Auto-generates user-facing release notes from your git commit history.

## App Frameworks

Frameworks for building whole applications around an agent.

- **[agent-native](https://github.com/BuilderIO/agent-native)** — *"A framework for
  building agent-native applications."* Unified primitives — actions, state, identity,
  tools, observability — so one action you define works across every surface: web UI,
  agent requests, HTTP API, CLI, and MCP. Ships templates for content management,
  analytics dashboards, and design prototyping, with full code ownership.

## Integrations & Automation

Skills that connect your agent to the apps your product already uses.

- **[Connect](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/connect)**
  — Links Claude to 500+ apps (email, issues, Slack, and more) so it can take real
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
2. Add it to the most fitting category above, following the existing format:
   a bold linked name, a one-line description (quote the project's own tagline where you
   can), and a sentence on what it does and how to install it.
3. Keep the tone neutral and entries concise.
4. Open a pull request.

Found a skill that doesn't fit an existing category? Propose a new one in your PR.

---

Many skills above are curated from the excellent
[ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills)
and [anthropics/skills](https://github.com/anthropics/skills) collections.
