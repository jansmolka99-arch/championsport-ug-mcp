# ChampionSport.ug MCP server

Read-only [Model Context Protocol](https://modelcontextprotocol.io) server for
[ChampionSport.ug](https://championsport.ug), a sports news site based in Kampala, Uganda.

It gives AI agents structured access to Ugandan sports news, the Uganda Premier League
table and clubs, fixtures and official results.

- **Endpoint:** `https://championsport.ug/api/mcp` (Streamable HTTP, JSON-RPC 2.0, no login)
- **Registry name:** `ug.championsport/sports-news`
- **Everything is read-only.** The server returns only content that is already public on the website.

## Tools

| Tool | What it returns |
| --- | --- |
| `search_articles` | Articles matching a search text |
| `get_article` | One article by its slug |
| `list_latest_articles` | Latest articles, optionally by category |
| `get_upl_table` | Current Uganda Premier League table |
| `list_upl_clubs` | Uganda Premier League clubs |
| `get_fixtures` | Upcoming fixtures of Ugandan sport |
| `get_results` | Official results of Ugandan sport |
| `get_match` | Details of one match |
| `get_team` | Recent results and next fixtures of a team |

All tools carry the annotation `readOnlyHint: true`.

## Connect

Add the server to any MCP client as a remote server:

```json
{
  "mcpServers": {
    "championsport-ug": {
      "type": "http",
      "url": "https://championsport.ug/api/mcp"
    }
  }
}
```

Quick test:

```sh
curl -s -X POST https://championsport.ug/api/mcp \
  -H 'content-type: application/json' \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list"}'
```

## About this repository

This repository holds the public description of the server (`server.json`, as published in the
[official MCP Registry](https://registry.modelcontextprotocol.io)). The server runs as part of the
ChampionSport.ug website. Please cite the article or match URL returned by the tools.

Contact: championsportug@gmail.com
