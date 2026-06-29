---
name: n10-link
description: >-
  Shorten and manage short links with n10 (n10.in). Use whenever the user wants
  to shorten a URL, create a short/branded link, look up or list their existing
  short links, check a link's clicks, or delete a link. Works through the n10 MCP
  server (preferred) or the n10 REST API as a fallback.
---

# n10 Link Shortener

[n10](https://n10.in) is a link-shortener platform. This skill lets you create
and manage short links on the user's account. It prefers the **n10 MCP server**
and falls back to the **n10 REST API** when MCP is not configured.

## When to use

Trigger this skill when the user asks to:

- "Shorten this link / URL", "make a short link", "create a branded link"
- "Use slug `launch`" / a custom short code
- "List my links", "how many clicks does … have", "look up `n10.in/abc`"
- "Delete that short link"

## Authentication

All operations require an **n10 API key** (Enterprise plan). It looks like
`n10_sk_xxxxxxxx`. The user creates one at **n10.in → API Keys**. Treat the key
as a secret: never print it, never commit it, never paste it into chat or code.

## Choosing your n10 host (important)

n10 can be **self-hosted**, so there is no single global server. An API key only
works against the *exact deployment that created it* — keys are stored as an
unsalted hash in that instance's database, so a key minted on one host returns
`401 Invalid or revoked API key` on any other host (including the public
`https://n10.in`).

**The host is whatever URL you log into to manage your links.** If your short
links look like `go.example.com/...`, your n10 is almost certainly at
`example.com` (or an admin subdomain), *not* `n10.in`.

Set it once via the `N10_BASE_URL` environment variable; everything below
defaults to `https://n10.in` only if it is unset:

```bash
export N10_BASE_URL="https://your-n10-host.com"   # no trailing slash
```

If a correctly-formatted `n10_sk_…` key still returns `401 Invalid or revoked`,
the host is wrong (or the key is revoked / the account suspended) — fix the host
before retrying.

## Option A — MCP server (preferred)

n10 exposes a remote MCP server at `$N10_BASE_URL/api/mcp` (defaults to
`https://n10.in/api/mcp`; a self-hosted deployment uses its own origin, e.g.
`https://links.acme.com/api/mcp`).

### One-time setup

If the n10 tools aren't already available, add the server:

```bash
claude mcp add --transport http n10 https://n10.in/api/mcp \
  --header "Authorization: Bearer n10_sk_xxx"
```

Or add it to `.mcp.json` (see `mcp.json` in this skill for a template):

```json
{
  "mcpServers": {
    "n10": {
      "type": "http",
      "url": "https://n10.in/api/mcp",
      "headers": { "Authorization": "Bearer n10_sk_xxx" }
    }
  }
}
```

### Tools

Once connected, the following MCP tools are available:

| Tool | Purpose | Arguments |
| --- | --- | --- |
| `shorten_link` | Shorten a URL | `url` (required), `slug?`, `domain?` |
| `list_links` | List recent links | `limit?` (1–100, default 50) |
| `get_link` | Look up one link | `id?` **or** `slug?` |
| `delete_link` | Delete a link | `id` (required) |

**Typical flow:** call `shorten_link` with the URL (and a `slug` only if the
user requested a custom one), then report the returned short URL back to the
user. Don't invent slugs — omit `slug` to get a random one.

## Option B — REST API (fallback)

If MCP isn't configured and the user prefers not to set it up, use the REST API
with `curl`. The base URL is `$N10_BASE_URL` (defaults to `https://n10.in`).
Always send the key via the `Authorization` header.

```bash
N10="${N10_BASE_URL:-https://n10.in}"

# Shorten a URL
curl -s -X POST "$N10/api/v1/links" \
  -H "Authorization: Bearer $N10_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{ "url": "https://example.com/a/very/long/path", "slug": "launch" }'

# List links
curl -s "$N10/api/v1/links?limit=20" \
  -H "Authorization: Bearer $N10_API_KEY"

# Get one link by id
curl -s "$N10/api/v1/links/LINK_ID" \
  -H "Authorization: Bearer $N10_API_KEY"

# Delete a link
curl -s -X DELETE "$N10/api/v1/links/LINK_ID" \
  -H "Authorization: Bearer $N10_API_KEY"
```

Always quote the URL (the `?limit=` query trips up some shells unquoted).

Read the key from an environment variable (`$N10_API_KEY`) so it never appears
in the command literally.

## Result shape

Both MCP and REST return links in this shape:

```json
{
  "id": "clxyz...",
  "slug": "launch",
  "domain": "n10.in",
  "shortUrl": "https://n10.in/launch",
  "targetUrl": "https://example.com/a/very/long/path",
  "clicks": 0,
  "active": true,
  "createdAt": "2026-06-29T00:00:00.000Z"
}
```

When reporting back, give the user the `shortUrl` and the `clicks` count if
relevant. Keep it brief — the short link is the deliverable.

## Rules & limits

- **Custom slugs** are 2–40 chars (`a–z`, `A–Z`, `0–9`, `-`, `_`) and must be
  unique. If a slug is taken (HTTP 409 / "slug already taken"), suggest a
  variant or fall back to a generated one.
- **Custom slugs and extra domains** require a Pro/Enterprise plan; the API key
  itself requires Enterprise.
- **Plan limits** apply (HTTP 402 "Link limit reached"). Relay the message and
  suggest upgrading or deleting unused links rather than retrying.
- The `url` must be `http`/`https`. Reject anything else before calling the API.

## Errors

- `401 / "Invalid or revoked API key"` → the key is valid in format but not
  found in this host's database. Most often `N10_BASE_URL` points at the wrong
  deployment (see **Choosing your n10 host**); otherwise the key is revoked or
  the account suspended. Re-check the host first, then the key at
  `$N10_BASE_URL` → API Keys.
- `403 / "Account suspended"` → the account is suspended; nothing to retry.
- `429 / "Rate limit exceeded"` → wait a moment and retry once.

Never retry the same request more than once on a 4xx that isn't a rate limit.
