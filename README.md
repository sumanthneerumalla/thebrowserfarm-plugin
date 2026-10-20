# The Browser Farm plugin

Isolated real cloud Chromium browsers for agents and bot teams: one per website, many in
parallel. Bundles:

- **Connector** (`mcp.json`): the hosted The Browser Farm MCP server over Streamable HTTP
  (`https://api.thebrowserfarm.com/mcp`). No local install.
- **Skill** (`skills/thebrowserfarm/SKILL.md`): teaches the agent the browse loop and how to
  split work across browsers or across a team of agents.

## Setup

1. Get an API key at https://www.thebrowserfarm.com.
2. Set `THEBROWSERFARM_API_KEY` to it. The plugin sends it as `Authorization: Bearer <key>`.

Grok Bot can also add `https://api.thebrowserfarm.com/mcp` as a custom MCP server with that
header. For a plain-text guide, `curl -H 'Accept: text/plain' https://api.thebrowserfarm.com/mcp`.

## Tools

`open_browser`, `navigate`, `snapshot`, `click`, `type`, `extract`, `close_browser`,
`list_browsers`. The loop: open → navigate → snapshot → click/type by ref → extract → close.

## Example prompts

- "Find the court rates and booking software for these 8 badminton clubs, as a CSV."
- "Open the pricing page of each of these 12 competitors and summarize their plans."

## Security

- **Network endpoint:** one hosted MCP server at `api.thebrowserfarm.com`. Browsers run in The
  Browser Farm cloud, not on your machine.
- **Credentials:** the plugin contains no secrets; the API key comes from your environment.
- **Isolation:** each browser is a separate context; private network addresses are blocked on
  every request.
- **Contents:** Markdown and JSON only.

## License

MIT
