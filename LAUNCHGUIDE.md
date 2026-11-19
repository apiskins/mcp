# API Skins

## Tagline
CS2 skin prices, buy orders, sales history, item data and Steam inventories for AI agents.

## Description
API Skins gives AI agents live CS2 (Counter-Strike 2) skin market data through a remote MCP server. Agents can look up the cheapest listing of any item on every marketplace we track, the highest buy orders, sales counts and median prices over 7 to 90 days, what each item is (weapon, wear, float range, rarity, collections, cases), and every item in a Steam inventory by Steam ID or trade URL, private inventories included. It is hosted, read-only and needs only an API key, which comes with a free plan.

## Setup Requirements
- `X-API-KEY` (required): your API Skins key, sent as a header. Sign in with Steam on https://apiskins.com and copy it from https://apiskins.com/api-docs. The free plan works.

## Category
Data & Analytics

## Features
- Cheapest listing of any CS2 item on every tracked marketplace, in USD
- Highest buy orders across marketplaces
- Sales count, median and average price over 7, 15, 30 and 90 days
- Item details: weapon, wear, float range, quality, rarity, collections and cases
- Any Steam inventory by Steam ID, or by trade URL for private inventories
- Name search that turns a few words into exact market_hash_names
- Up to 100 items per call
- Hosted remote server: nothing to install
- Read-only tools
- Free plan included

## Getting Started
- "Where is an AK-47 Redline Field-Tested cheapest right now?"
- "What's in this Steam inventory, and what is it worth?"
- "What did a Karambit Doppler sell for over the last 30 days?"
- Tool: find_items — exact market_hash_names from a few words of a name
- Tool: get_offers — the cheapest listing on every marketplace
- Tool: get_buy_orders — the highest buy orders
- Tool: get_sales_summary — sales and median prices (paid plans)
- Tool: get_items — what each item is (paid plans)
- Tool: get_inventory — every CS2 item in a Steam inventory

## Tags
cs2, counter-strike, csgo, skins, steam, steam inventory, prices, price api, trading, buy orders, sales history, market data, gaming, marketplace, inspect link, float

## Documentation URL
https://apiskins.com/ai-agents
