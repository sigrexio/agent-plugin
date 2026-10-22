# Sigrex is installed

Two steps are left before the Sigrex tools appear.

**1. Enable the plugin**

```bash
hermes plugins enable sigrex
```

**2. Sign in to your Sigrex account**

```bash
hermes mcp login sigrex
```

Your browser opens the Sigrex sign-in page. Sign in and approve access; the
command waits up to five minutes. Run the same command to sign in again later.

In Hermes Desktop: open **Capabilities → Connectors** and choose
**Authenticate** on the Sigrex card.

Start a new session and try: "Show me my active Sigrex strategies."

If `hermes mcp login sigrex` reports that the server is not found, your
Hermes release predates plugin sign-in. Add the server yourself instead:

```bash
hermes mcp add sigrex --url https://mcp.sigrex.io --auth oauth --connect-timeout 300
```

In Hermes Desktop on such a release: **Capabilities → Connectors → Add your
own**, with name `sigrex`, type Streamable HTTP, URL `https://mcp.sigrex.io`
and auth OAuth. Save, then choose **Authenticate** on the Sigrex card.

The connection has full access to your Sigrex account, including actions that
can place live trades. More: https://github.com/sigrexio/agent-plugin