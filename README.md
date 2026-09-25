# Sigrex agent plugin

The official [Sigrex](https://sigrex.io) plugin for AI agents. Build, run and
manage your trading automation in plain language: code and AI strategies,
trading bots, webhooks and signals across crypto exchanges, DEXs and
prediction markets.

This is a portable [Agent Plugins v1](https://agent-plugins.org/specification)
package, so it works in any agent that supports the format. It contains:

- **`mcp.json`**: the official Sigrex MCP server (`https://mcp.sigrex.io`,
  Streamable HTTP, OAuth sign-in). No API keys to copy.
- **`skills/sigrex`**: an [Agent Skill](https://agentskills.io) that teaches
  the agent how Sigrex fits together, how to write code strategies and AI
  trading sessions, and the safety rules for anything that can place a trade.

There is no executable code and nothing that downloads or updates itself.

**Requirements:** a free [Sigrex account](https://app.sigrex.io/signup). To
trade live you also need exchange API keys connected in Sigrex, and AI
strategies need an LLM provider key added in your Sigrex settings.

## Install

### Hermes Agent

From the [Hermes plugin catalog](https://hermes-agent.nousresearch.com/docs/plugins):

```bash
hermes plugins install sigrex
hermes plugins enable sigrex
```

Or directly from this repository:

```bash
hermes plugins install sigrexio/agent-plugin --no-enable
hermes plugins enable sigrex
```

On first use your agent opens the Sigrex sign-in page in your browser. Sign
in, approve access, and the Sigrex tools become available.

### Other agents

Any agent that supports Agent Plugins v1 can load this folder as a plugin.
If your agent only supports MCP servers, connect `https://mcp.sigrex.io`
directly (see the [MCP server docs](https://docs.sigrex.io/more/mcp-server));
you can also copy `skills/sigrex` into your agent's skills folder if it
supports Agent Skills.

## What you can ask

- "Show me my active strategies and when each one last triggered."
- "Create a strategy for ETHUSDC that goes long when RSI drops below 30 and
  exits at 1% profit. Keep it inactive so I can review it."
- "Duplicate my BTC momentum strategy for SOL and AVAX."
- "My POPCAT strategy hasn't traded in two days. Read its code and storage and
  tell me why."
- "Build an AI session that checks BTC every 15 minutes and journals its
  reasoning."
- "Pause all my bots in the hyperliquid folder."
- "What's the current price of SOL on Binance?"

## Security

- **The connection has full access to your Sigrex account.** The agent can
  create, modify and delete resources, start strategies and send live trading
  signals. Only enable this plugin in agents and profiles you trust.
- The bundled skill tells the agent to create things inactive, to use `TEST`
  signals first, to redact credentials, and to ask before any action that
  activates, trades, shares or deletes. Still review what it proposes.
- Your OAuth token is stored and refreshed by your agent. No credentials live
  in this repository. Disconnect by disabling or removing the plugin, or
  revoke access in your Sigrex account.
- Trading carries risk. Nothing here is financial advice, and Sigrex does not
  support backtesting.

## Links

- MCP server docs: https://docs.sigrex.io/more/mcp-server
- Sigrex docs: https://docs.sigrex.io
- Support: open an issue on this repository

## License

MIT. See [LICENSE](LICENSE).
