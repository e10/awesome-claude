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
- [App Frameworks](#app-frameworks)
- [Document & Content Tooling](#document--content-tooling)
- [Contributing](#contributing)

## What is a skill?

A **skill** is a portable bundle of instructions, rules, and sometimes commands that
teaches an AI coding agent how to do something well — design a polished UI, animate an
element correctly, convert a document, or wire up an application. You install a skill
into your agent and it improves the agent's output for that task, no fine-tuning
required.

## Frontend & Design

Skills that give your agent taste — so AI-generated UIs stop looking generic and start
looking intentional.

- **[taste-skill](https://github.com/Leonxlnx/taste-skill)** — *"The Anti-Slop
  Frontend Framework for AI Agents."* A collection of portable skills that steer coding
  agents away from generic, repetitive UI and toward polished typography, spacing,
  motion, and layout. Ships multiple aesthetic variants (soft, brutalist, minimalist),
  adjustable parameters (variance, motion, density), and image-to-code workflows.
  Framework-agnostic (React, Vue, Svelte). Install with `npx skills add`.

- **[impeccable](https://github.com/pbakaus/impeccable)** — *"The design language that
  makes your AI harness better at design."* Adds 23 design commands
  (`/impeccable audit`, `/impeccable polish`, `/impeccable critique`, …) plus 44
  deterministic detector rules that catch common anti-patterns (overused fonts, purple
  gradients, nested cards, poor contrast) without API calls. Start with
  `/impeccable init` to capture brand, colors, typography, and voice. Works across
  Cursor, Claude Code, Copilot, Gemini CLI, and more. Install with `npx impeccable install`.

- **[Skills for Design Engineers](https://github.com/emilkowalski/skill)** — Design and
  animation guidelines from Emil Kowalski. Codifies the details agents usually get wrong
  (easing functions, animation review criteria) into reusable rules. Includes
  `emil-design-eng` (core design and animation advice) and `review-animations` (strict
  animation review). Install with `npx skills@latest add emilkowalski/skills`.

## App Frameworks

Skills and frameworks for building whole applications around an agent.

- **[agent-native](https://github.com/BuilderIO/agent-native)** — *"A framework for
  building agent-native applications."* Provides unified primitives — actions, state,
  identity, tools, and observability — so a single action you define works across every
  surface: web UI, agent requests, HTTP API, CLI, and MCP. Ships templates for content
  management, analytics dashboards, and design prototyping, with full code ownership.

## Document & Content Tooling

Skills that prepare real-world data for your agent to work with.

- **[markitdown](https://github.com/microsoft/markitdown)** — Microsoft's lightweight
  Python utility for converting files to Markdown for LLM pipelines. Handles PDF, Word,
  PowerPoint, Excel, images, audio, HTML, EPub, ZIP, and even YouTube URLs — preserving
  headings, lists, tables, and links so the output is token-efficient and LLM-friendly.
  Use it via CLI (`markitdown file.pdf > out.md`) or the Python API.

## Contributing

Contributions are welcome! To add a skill:

1. Make sure the project is open source and accepts PR contributions.
2. Add it to the most fitting category above, following the existing format:
   a bold linked name, a one-line description (quote the project's own tagline where you
   can), and a sentence on what it does and how to install it.
3. Keep the list alphabetical-ish within a category and the tone neutral.
4. Open a pull request.

Found a skill that doesn't fit an existing category? Propose a new one in your PR.
