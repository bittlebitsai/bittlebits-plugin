# BittleBits MCP Plugin

Connect **Claude**, **Cursor**, and any MCP-compatible AI agent to [BittleBits](https://bittlebits.ai) — bringing your **GEO (Generative Engine Optimization) scores** and **AI-content rewrite suggestions** directly into your agent as tools.

This repository is the installable plugin wrapper. The BittleBits MCP server itself is hosted and remote — it speaks **HTTP/SSE** and authenticates with **OAuth 2.0**, so there is no token to configure and nothing to run locally. Point your client at the server and sign in through your browser.

## What you get

Once connected, your agent can call BittleBits tools to score and rewrite content without copy-pasting between tabs:

| Tool          | What it does                                                                                   |
| ------------- | ---------------------------------------------------------------------------------------------- |
| `get_score`   | Returns GEO metric scores (0–10 per dimension) for a page                                       |
| `get_rewrite` | Returns your original page content and a rewritten version with BittleBits suggestions applied  |

Ask things like *"Get the BittleBits score for my landing page and tell me which areas need the most work,"* or *"Rewrite my homepage applying the BittleBits suggestions but keep the casual tone."*

## Install

The server lives at `https://bittlebits.ai/mcp`. On first use, your client opens a browser window to sign in to your BittleBits account (OAuth) — no API keys or tokens to paste.

### Claude Code (CLI)

```bash
claude mcp add --transport http bittlebits https://bittlebits.ai/mcp
```

### Claude.ai / Claude Desktop

`Settings → Connectors → Add custom connector`, name it **BittleBits**, and set the remote MCP server URL to `https://bittlebits.ai/mcp`.

### Cursor / VS Code

Add to your `mcp.json`:

```json
{
  "mcpServers": {
    "bittlebits": {
      "type": "sse",
      "url": "https://bittlebits.ai/mcp"
    }
  }
}
```

This repo's root [`.mcp.json`](./.mcp.json) contains exactly this config, so MCP-aware directories and clients can auto-detect the server.

## Documentation

Full setup guide and examples: **https://bittlebits.ai/docs/mcp**

## License

[MIT](./LICENSE) © 2026 BittleBits.ai