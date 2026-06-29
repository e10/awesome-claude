# n10-link — link shortener skill

A Claude / AI-agent skill that shortens and manages short links through
[**n10**](https://n10.in), a link-shortener platform. Ask your agent to "shorten
this URL" and it creates a short link on your n10 account, with an optional
custom slug — over MCP (preferred) or the n10 REST API.

## What it does

- **Shorten** a long URL into a short link (`n10.in/launch`), with optional
  custom slug and domain.
- **List** your recent links and their click counts.
- **Look up** a single link by id or slug.
- **Delete** a link.

## How it works

The skill drives the **n10 MCP server** (`https://n10.in/api/mcp`), a stateless
streamable-HTTP Model Context Protocol endpoint built into the n10 app. It
exposes four tools — `shorten_link`, `list_links`, `get_link`, `delete_link` —
all authenticated with your n10 API key. When MCP isn't configured, the skill
falls back to the equivalent n10 REST API (`/api/v1/links`) via `curl`.

## Requirements

- A **TinTorch Account** API key (`tt_live_…`). n10 delegates identity and keys
  to TinTorch — the single source of keys for the suite — so create one at
  **account.tintorch.com → Developer → API keys** with the `read` and/or `write`
  scope (`write` is needed to shorten or delete links).
- Optionally your n10 **host**. The default is `https://n10.in`; for a
  self-hosted n10, set `N10_BASE_URL` to your own origin. The same TinTorch key
  works against any n10 host (n10 verifies it against TinTorch).

## Install

1. Copy the `n10-link/` folder into your agent's skills directory
   (e.g. `~/.claude/skills/n10-link/` or your project's `.claude/skills/`).
2. Connect the MCP server (one-time):

   ```bash
   claude mcp add --transport http n10 https://n10.in/api/mcp \
     --header "Authorization: Bearer tt_live_xxx"
   ```

   …or copy `mcp.json` into your project's `.mcp.json` and fill in your key.
3. Ask your agent: *"Shorten https://example.com/very/long/path with slug
   launch."*

## Files

| File | Purpose |
| --- | --- |
| `SKILL.md` | The skill itself — instructions, tools, rules, fallbacks. |
| `mcp.json` | Drop-in MCP server config template. |
| `README.md` | This file. |

## Links

- App & dashboard: <https://n10.in>
- Source / issues: <https://github.com/qanuj/n10>
- API & MCP docs: <https://n10.in/docs/api>

Open source and accepts contributions.
