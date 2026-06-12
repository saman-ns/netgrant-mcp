# NetGrant — Canadian funding, inside your AI

NetGrant is a **free, public MCP server** (and web app) for searching **1,300+ live
Canadian funding opportunities** — grants, tax credits, wage subsidies, accelerators,
pitch competitions, loans, and events. Ask Claude, Cursor, or any MCP client to find,
compare, and check eligibility for Canadian funding without leaving the conversation.

- **MCP endpoint:** `https://mcp.netgrant.ca/mcp` (Streamable HTTP, no auth, no API key)
- **Web app:** https://app.netgrant.ca (same data, search UI, no login)
- **Site:** https://netgrant.ca

> This repository is **documentation only**. NetGrant is a hosted, closed-source
> public service — there is no source code here and none to self-host. Point your
> MCP client at the endpoint above and you're done.

---

## Add it to your client

**Claude Desktop / Cursor / Cline / Continue** — add to your MCP config
(`claude_desktop_config.json`, `.cursor/mcp.json`, etc.):

```json
{
  "mcpServers": {
    "netgrant": {
      "type": "http",
      "url": "https://mcp.netgrant.ca/mcp"
    }
  }
}
```

**Claude Code (CLI):**

```bash
claude mcp add --transport http netgrant https://mcp.netgrant.ca/mcp
```

**Claude.ai (web):** Settings → Connectors → Add custom connector → paste
`https://mcp.netgrant.ca/mcp`.

No account, no key, no rate-limit signup. Restart your client and the tools appear.

---

## Tools

| Tool | What it does |
|------|--------------|
| `search_opportunities` | Full-text search across the catalog with optional `region`, `category`, `deadline_within_days`, `min_funding` / `max_funding`, `is_rolling`, and `exclude_expired` filters. Returns ranked matches. |
| `get_opportunity_details` | Fetch the full record for one opportunity by id — eligibility, body, amounts, deadline, source link. |
| `compare_opportunities` | Fetch 2–4 opportunities at once for a side-by-side comparison. |
| `eligibility_check` | Pull one opportunity's eligibility criteria alongside an applicant description so the assistant can judge fit. |
| `subscribe_to_digest` | Opt the user (with their consent + email) into a **free weekly email digest** of new Canadian grants matching a saved search. Double opt-in. |

## Prompts (slash commands)

| Prompt | What it does |
|--------|--------------|
| `/find-for-me` | Match opportunities to a one-sentence business description. |
| `/check-deadlines` | Show opportunities closing in the next 30 days. |

---

## Weekly email digest

Beyond live search, NetGrant offers a free opt-in **weekly email digest**: tell the
assistant the niche you're tracking (keywords + province), give your email, and you'll
get 8–10 matching Canadian grants each week — newest first, falling back to the
strongest current matches. Double opt-in, one-click unsubscribe.

---

## Data coverage & freshness

- **1,300+ live opportunities** across federal, provincial, municipal, and private sources.
- Normalized schema: title, category, region, funding range, deadline, eligibility text, source URL.
- Continuously ingested from 60+ source providers; a daily audit agent re-checks live
  listings, archives dead/expired programs, and corrects drifted details.
- Updated weekly; stale items are auto-archived.

NetGrant is not affiliated with any government or funding body. Always confirm
eligibility and deadlines on the official program page before applying.

---

## Support

Questions, corrections, a missing program, or a partnership idea:
**sami@netgrant.ca** · https://netgrant.ca
