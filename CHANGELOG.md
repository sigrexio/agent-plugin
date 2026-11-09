# Changelog

## 1.0.0 - 2026-09-25

- First release.
- Sigrex MCP server (`https://mcp.sigrex.io`, Streamable HTTP, OAuth).
- `sigrex` workflow skill with references for code strategies, LLM sessions
  and the signal payload.

## 1.0.1 - 2026-09-26

- Added the catalog banner (`assets/banner.png`, 1200×600).
- No changes to the MCP server configuration or the `sigrex` skill.

## 1.0.4 - 2026-10-02

- Hermes Agent: documented the connect step. Hermes signs in only to MCP
  servers the user adds, so the README, the new `after-install.md` and the
  `sigrex` skill now give the one-time `hermes mcp add` command and the Hermes
  Desktop steps.
- The `sigrex` skill tells the agent what to do when the Sigrex tools are not
  available yet.
- No changes to the MCP server configuration.

## 1.1.1 - 2026-10-10

- Added 12 detailed skills alongside `sigrex`: `sigrex-overview`,
  `sigrex-strategy-flows`, `sigrex-webhooks`, `sigrex-cex-bots`,
  `sigrex-dex-bots`, `sigrex-prediction-bots`, `sigrex-code-strategies`,
  `sigrex-llm-trading`, `sigrex-reactions`, `sigrex-api-mcp`, `sigrex-social`
  and `sigrex-integrations`. They cover complete strategy flows, payloads,
  every bot type, the code sandbox, LLM tools, the REST API and testing.
- `sigrex` is now the entry point: it keeps the MCP connection steps, safety
  rules and tool tips, routes to the detailed skills, and documents
  `send_data_hook_message`, `resolve_llm_reaction_prompt_template`,
  `askQuestion` and the public-strategy tools.
- Removed the `sigrex` skill's `references/` files; the detailed skills
  replace them.
- Updated for the current platform: `$.Price` is deprecated, Telegram
  Signals and the Pine Script builder no longer exist.
- Still no executable code: the skills contain documentation and examples
  only.
- No changes to the MCP server configuration.

## 1.2.0 - 2026-10-23

- Hermes Agent: the plugin now declares the Sigrex server as OAuth in
  `plugin.json` (`extensions.com.nousresearch.hermes.servers.sigrex.auth`).
  Hermes signs in to the plugin's own server, so you no longer add it
  yourself: run `hermes mcp login sigrex`, or choose Authenticate on the
  Sigrex card in Hermes Desktop. Hermes stores and refreshes the token in your
  profile, adds nothing to `config.yaml`, and signs you out when you remove
  the plugin.
- Needs a Hermes release with plugin OAuth sign-in. On an older release,
  `hermes mcp login sigrex` reports that the server is not found; the README,
  `after-install.md` and the `sigrex` skill keep the `hermes mcp add` steps
  for that case.
- Other agents ignore the new extension. No changes to the MCP server URL or
  transport, and no changes to the skills beyond the Hermes connect steps.

## 1.2.1 - 2026-10-26

- Skills: documented the code rules the Sigrex API now checks when a Code
  Strategy or Code Reaction is created or updated (declared variables, loops
  that end by their condition, read-only built-ins and `$.Ta`, size and loop
  limits, regular expression literals). `sigrex-code-strategies` has a new
  Code Rules section with what to write instead; `sigrex`, `sigrex-reactions`,
  `sigrex-strategy-flows` and `sigrex-llm-trading` point to it.
- No changes to the MCP server configuration.

## 1.2.2 - 2026-11-02

- Skills: documented the new HTTP limits for Code Strategies and Code
  Reactions: at most 30 `$.Http` calls per run (`generateSignature` doesn't
  count) and response bodies up to 5 MB. Over a limit the call returns
  `status: 0` with the reason in `text`; the strategy is not suspended.
  `sigrex-code-strategies` lists them in Limits and the runtime reference,
  which also notes that failed responses are cached and that identical GETs
  in flight are shared; `sigrex-strategy-flows` troubleshooting covers the
  `status: 0` replies.
- No changes to the MCP server configuration.

## 1.2.3 - 2026-11-05

- Skills: API keys can no longer be added or tested through the Sigrex MCP
  server. The user adds exchange, prediction-market and LLM keys in the
  dashboard under **API connection**; the MCP tools can still list them,
  switch them on or off, delete them and change an LLM key's model.
  `sigrex`, `sigrex-overview`, `sigrex-api-mcp`, `sigrex-strategy-flows`,
  `sigrex-cex-bots`, `sigrex-prediction-bots` and `sigrex-llm-trading` no
  longer tell the agent to create or test keys, and tell it not to ask for
  keys in the chat.
- No changes to the MCP server configuration.

## 1.2.4 - 2026-11-09

- Hermes Agent: the plugin now declares the Sigrex server as untrusted in
  `plugin.json` (`extensions.com.nousresearch.hermes.servers.sigrex.trust`).
  The connection has full account access, including live trades, so Hermes
  asks you before every write-capable Sigrex tool call.
- Other agents ignore the new setting. No changes to the MCP server URL,
  transport or OAuth sign-in, and no changes to the skills.
