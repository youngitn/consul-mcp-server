# Consul MCP Server (Customized)

This is a customized version of the [Consul MCP Server](https://github.com/kocierik/consul-mcp-server) modified specifically to support **Consul ACL Tokens**.

## What's Changed?
- Added support for `CONSUL_TOKEN` environment variable.
- The underlying Consul client now correctly authenticates to secure clusters (with ACL enabled), allowing it to fetch both Services and Key-Value (KV) configurations without being blocked as an anonymous user.

## Configuration in MCP / Claude / Cursor

Use the following configuration in your `mcp_config.json` (or equivalent IDE settings):

```json
{
  "mcpServers": {
    "consul-mcp": {
      "command": "node",
      "args": [
        "C:/path/to/your/consul-mcp-server/build/index.js"
      ],
      "env": {
        "CONSUL_HOST": "10.4.0.53",
        "CONSUL_PORT": "8500",
        "CONSUL_TOKEN": "your-acl-token-here"
      }
    }
  }
}
```

## Setup & Build

1. Clone this repository
2. Run `npm install`
3. Run `npm run build`
