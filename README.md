# Company Data MCP (SteadyScrape)

[![dev.steadyscrape/company-data MCP connector](https://glama.ai/mcp/connectors/dev.steadyscrape/company-data/badges/score.svg)](https://glama.ai/mcp/connectors/dev.steadyscrape/company-data)

A remote MCP server for company research: company profiles read from their public websites, lists of sites that use a named technology, and hiring summaries from public career boards.

**Endpoint (Streamable HTTP):**

```
https://company.mcp.steadyscrape.dev/mcp
```

The same server is also served at `https://mcp.steadyscrape.dev/company/mcp`. It is hosted on the [SteadyScrape MCP gateway](https://company.mcp.steadyscrape.dev). Tools run in your own [Apify](https://apify.com/steady-scrape) account. Nothing to install or host.

## Tools

All tools are read-only.

| Tool | What it does |
|---|---|
| `company_profile` | Reads 1–10 company websites and returns name, description, industry guess, published address, founded year and employee count, logo, social pages and detected technologies. No email addresses or phone numbers. |
| `sites_using_technology` | Company websites that use named technologies (e.g. Shopify, HubSpot, Klaviyo, Stripe), filterable by country, language, niche keywords and domain rank. |
| `company_hiring_summary` | Hiring activity of 1–5 companies from public career boards: open and new roles, change over time, top functions, locations, seniority and remote mix. |
| `get_results` | Fetch results of a call that returned a `run_id` because it took longer than about two minutes. Free. |

Each call is billed by Apify to your own account at the Store price of the underlying SteadyScrape Actor (see the [server page](https://company.mcp.steadyscrape.dev) for prices and free-plan limits). Errors and refused calls are free; listing tools and connecting cost nothing.

## Authentication

Sign in with your own Apify account (free to create). Clients that support MCP OAuth (Claude, VS Code, Cursor, ChatGPT developer mode) open the Apify sign-in the first time. Apify runs the sign-in (OAuth 2.1 with PKCE); SteadyScrape never sees your Apify password. You can revoke access any time in Apify Console → Settings → API & Integrations.

## Client setup

**Claude.ai / Claude Desktop:** Settings → Connectors → *Add custom connector* → paste the endpoint URL → Connect, then sign in to Apify.

**Claude Code:**

```bash
claude mcp add --transport http steadyscrape-company "https://company.mcp.steadyscrape.dev/mcp"
```

**Cursor, Windsurf** and other clients that use `mcpServers`:

```json
{
  "mcpServers": {
    "steadyscrape-company": { "url": "https://company.mcp.steadyscrape.dev/mcp" }
  }
}
```

**VS Code** (`.vscode/mcp.json`):

```json
{
  "servers": {
    "steadyscrape-company": { "type": "http", "url": "https://company.mcp.steadyscrape.dev/mcp" }
  }
}
```

**Clients that only speak stdio:**

```json
{
  "mcpServers": {
    "steadyscrape-company": { "command": "npx", "args": ["-y", "mcp-remote", "https://company.mcp.steadyscrape.dev/mcp"] }
  }
}
```

## Example prompts

- "Profile stripe.com, ramp.com and brex.com: industry, size, socials and tech stack."
- "Find US Shopify stores that also use Klaviyo, in the pet supplies niche."
- "How has hiring changed at Figma and Canva over the last 90 days?"

## Links

- Server page: https://company.mcp.steadyscrape.dev
- Privacy: https://mcp.steadyscrape.dev/privacy
- Support: https://mcp.steadyscrape.dev/support
- Terms: https://steadyscrape.dev/terms
- Official MCP Registry: `dev.steadyscrape/company-data` ([`server.json`](server.json))
- Glama: https://glama.ai/mcp/connectors/dev.steadyscrape/company-data ([`glama.json`](glama.json))

## License

MIT. This repo contains configuration and docs only; the tools are paid services on Apify.
