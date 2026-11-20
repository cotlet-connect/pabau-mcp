# Pabau MCP server for ChatGPT and Claude

Pabau publishes an official API for selected business operations. Cotlet.dev connects ChatGPT, Claude and other AI agents to your signed-in Pabau account for scheduling and contact work. Clinical notes and treatment decisions stay outside this connection.

## What you can ask

> Read a practitioner's appointment book.

> Find the correct contact record.

> Review a selected booking's time.

> Prepare an appointment change.

> Read the available appointment services.

> Check the contact details needed by reception.

## Connect in 2 minutes

Get your API key at https://cotlet.dev/app and export it as `COTLET_API_KEY`.

### ChatGPT

Settings → Apps → add connector URL `https://cotlet.dev/mcp/v1/connect`, then sign in with Cotlet.dev. No API key needed.

### Claude Code

```bash
claude mcp add --transport http cotlet https://cotlet.dev/mcp/v1 --header "Authorization: Bearer $COTLET_API_KEY"
```

### Cursor

Copy `.cursor/mcp.json` from this repo into your project:

```json
{
  "mcpServers": {
    "cotlet": {
      "url": "https://cotlet.dev/mcp/v1",
      "headers": {
        "Authorization": "Bearer ${COTLET_API_KEY}"
      }
    }
  }
}
```

## Run the local MCP bridge

Python 3.10+, with no dependencies. Clone this repository, set your Cotlet.dev API key, then run:

```bash
export COTLET_API_KEY="your-key"
python3 pabau_agent.py serve
```

This local stdio bridge lists seven browser helper tools: `pabau_guide`, `pabau_status`, `pabau_open`, `pabau_read`, `pabau_click`, `pabau_type` and `pabau_close`.
It forwards calls to the hosted Cotlet.dev MCP server.
The 63 task tools described on the integration page are available through the hosted connection.

Without a key, the local bridge can list its helpers; calls return setup instructions.

```bash
python3 pabau_agent.py connect
python3 pabau_agent.py guide
python3 pabau_agent.py status
```

## Questions from Pabau users

**Does Pabau have an API?**

Pabau publishes an official API for selected business operations. The Cotlet.dev page, checked 12 November 2026, says its help center excludes creating pipelines and stages through that API.

**Is there an official Pabau MCP server?**

No vendor-operated Pabau MCP server or official ChatGPT or Claude connector was established in the sources checked on 12 November 2026.

**What is the scope of this connection?**

Scheduling and contact work for reception. Clinical notes, diagnosis, treatment and prescriptions stay outside these capabilities.

**Is Cotlet.dev affiliated with Pabau?**

No. Cotlet.dev is independent and is not affiliated with Pabau.

## Integration details

[Pabau tools and setup on Cotlet.dev](https://cotlet.dev/integrations/pabau-api-mcp-server?utm_source=github&utm_medium=readme&utm_campaign=pabau)

---

More: https://cotlet.dev/integrations/pabau-api-mcp-server?utm_source=github&utm_medium=readme&utm_campaign=pabau

Start free: https://cotlet.dev/signup?app=pabau&utm_source=github&utm_medium=readme&utm_campaign=pabau
