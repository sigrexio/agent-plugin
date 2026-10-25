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

## Unreleased

- Skills: documented the code rules the Sigrex API now checks when a Code
  Strategy or Code Reaction is created or updated (declared variables, loops
  that end by their condition, read-only built-ins and `$.Ta`, size and loop
  limits, regular expression literals). `sigrex-code-strategies` has a new
  Code Rules section with what to write instead; `sigrex`, `sigrex-reactions`,
  `sigrex-strategy-flows` and `sigrex-llm-trading` point to it.
- No changes to the MCP server configuration.
