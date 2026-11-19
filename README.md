# API Skins MCP server

CS2 skin market data for AI agents, from [API Skins](https://apiskins.com): the cheapest listing of any CS2 item on every marketplace we track, the best buy orders, sales history, what each item is, and the items in any Steam inventory.

It is a remote MCP server: nothing to install or run. Point your MCP client at

```
https://api.apiskins.com/mcp
```

with your API key in the `X-API-KEY` header (or as `Authorization: Bearer <key>`).

## Get a key

Sign in with Steam on [apiskins.com](https://apiskins.com) and copy your key from the [API docs page](https://apiskins.com/api-docs). The free plan works.

## What you can ask

- "Where is an AK-47 Redline Field-Tested cheapest right now?"
- "What does a Karambit Doppler sell for instantly, and what did it sell for over the last 30 days?"
- "What's in this Steam inventory, and what is it worth?" (give a Steam ID or a trade URL)
- "Compare the cheapest listing of these 20 skins across marketplaces."
- "Which collection and case is the M4A1-S Printstream from, and what float range does Minimal Wear have?"

## Tools

| Tool | What it answers |
| --- | --- |
| `find_items` | Exact `market_hash_name`s from a few words of a name, like "redline field tested". Use it first when unsure of a name. |
| `get_offers` | The cheapest listing (lowest sell offer) of up to 100 items on every marketplace, in USD. |
| `get_buy_orders` | The highest buy order of up to 100 items on each marketplace that has buy orders: what they sell for right now. |
| `get_sales_summary` | Sales count, median and average price over the last 7, 15, 30 and 90 days, and typical 15-day volume. Paid plans. |
| `get_items` | What each item is: type, weapon, wear and float range, quality, rarity, collections, cases, picture. Paid plans. |
| `get_inventory` | Every CS2 item in a Steam inventory, by SteamID64 (public inventories) or by trade URL (private ones too): name, asset ID, class ID, instance ID, inspect link. |

Every tool is read-only. Items are named by Steam's exact `market_hash_name`, like `AK-47 | Redline (Field-Tested)`. Prices are in US dollars.

## Plans

Each tool call is one API request on your plan. `find_items` counts toward the per-minute limit only.

| Plan | Price | Requests / 30 days | Requests / minute | Covers |
| --- | --- | --- | --- | --- |
| Free | $0 | 100 | 60 | Prices and buy orders from a limited set of marketplaces, Steam inventories |
| Trader | $14.99 / month | 5,000 | 120 | Every marketplace, sales and item data |
| Pro | $49.99 / month | 25,000 | 300 | Every marketplace, sales and item data |
| Business | $119.99 / month | 100,000 | 300 | Every marketplace, sales and item data |

See [apiskins.com/pricing](https://apiskins.com/pricing) for the current plans.

## Setup

### Claude Code

```sh
claude mcp add --transport http apiskins https://api.apiskins.com/mcp --header "X-API-KEY: <your key>"
```

### Cursor

In `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "apiskins": {
      "url": "https://api.apiskins.com/mcp",
      "headers": { "X-API-KEY": "<your key>" }
    }
  }
}
```

### VS Code

In `.vscode/mcp.json`:

```json
{
  "servers": {
    "apiskins": {
      "type": "http",
      "url": "https://api.apiskins.com/mcp",
      "headers": { "X-API-KEY": "<your key>" }
    }
  }
}
```

### Windsurf and other clients

Any client that takes a Streamable HTTP URL and headers: URL `https://api.apiskins.com/mcp`, header `X-API-KEY: <your key>`.

## Notes

- Over the per-minute limit, a tool answers with an error; wait a few seconds before calling again.
- A tool's error says why: a wrong name, a missing key, a route that needs a paid plan, or a private inventory asked for by Steam ID.

## Links

- [API Skins](https://apiskins.com)
- [For AI agents](https://apiskins.com/ai-agents)
- [API docs](https://apiskins.com/api-docs) and [OpenAPI document](https://apiskins.com/openapi.json)
- [llms.txt](https://apiskins.com/llms.txt)
- Support: [support@apiskins.com](mailto:support@apiskins.com)
