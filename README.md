# FundingTracker MCP server

<img src="assets/logo.png" alt="FundingTracker" width="64" align="right">

[FundingTracker](https://fundingtracker.app) helps business owners and brokers track merchant cash advances (MCAs) and business loans. Its hosted MCP server lets Claude, ChatGPT, Cursor, VS Code and other MCP clients work with MCAs. You don't need to install anything.

**Server URL:** `https://fundingtracker.app/api/mcp` (Streamable HTTP)

This repository holds only the listing manifests for MCP directories and clients. The server itself is hosted and run by FundingTracker.

## What it can do

You don't need an account for these:

| Tool | What it does |
|---|---|
| `calculate_mca_apr` | Turns a factor rate into total payback, cost of capital, payment size and effective APR |
| `estimate_mca_payoff` | Estimates the remaining balance, payments left and payoff date |
| `mca_payment_impact` | Measures how heavy a daily or weekly payment is against average daily revenue |
| `search_funders`, `get_funder` | Search FundingTracker's public funder directory, with merchant reviews |
| `search_mca_guides`, `get_mca_guide` | Read FundingTracker's MCA guides |
| `request_funder_listing` | For funding companies: ask to be listed. Nothing is published until the company confirms by email and FundingTracker approves |
| `about_fundingtracker` | What FundingTracker is and how to sign up |

After you sign in to FundingTracker, it can also read your own account:

| Tool | What it does |
|---|---|
| `list_my_deals`, `get_my_deal` | Your advances and loans, balances and recent payments |
| `get_my_upcoming_debits`, `list_my_bank_debits` | Upcoming payments, and the debits your linked bank shows |
| `list_my_alerts`, `get_my_insight` | Alerts FundingTracker sent you, and your dashboard insight |
| `compare_my_deals` | Compares your deals side by side |

Calculator results are estimates. They are not a payoff letter or financial advice.

## Connect

- **Claude:** go to Customize > Connectors > Add custom connector and paste the server URL.
- **Claude Code:** `claude mcp add --transport http fundingtracker https://fundingtracker.app/api/mcp`
- **ChatGPT:** in developer mode, add the server URL as a custom app.
- **Cursor:** [install the server](cursor://anysphere.cursor-deeplink/mcp/install?name=fundingtracker&config=eyJ1cmwiOiJodHRwczovL2Z1bmRpbmd0cmFja2VyLmFwcC9hcGkvbWNwIn0=), or add it to `~/.cursor/mcp.json` with the same entry as [`mcp.json`](mcp.json).
- **VS Code:** [install the server](vscode:mcp/install?%7B%22name%22%3A%22fundingtracker%22%2C%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//fundingtracker.app/api/mcp%22%7D), or run **MCP: Add Server** and choose HTTP.
- **Gemini CLI:** `gemini extensions install https://github.com/Mikelb32/fundingtracker-mcp`
- **Any other MCP client:** use the server URL over Streamable HTTP.

More setup help is at [fundingtracker.app/ai-assistants](https://fundingtracker.app/ai-assistants).

## Sign-in

The public tools need no sign-in. The first time you use an account tool, your client opens FundingTracker's sign-in page.

FundingTracker runs its own OAuth 2.1 server. It uses PKCE (S256) and supports dynamic client registration and client ID metadata documents, so clients don't need an API key. The protected-resource metadata is at `https://fundingtracker.app/.well-known/oauth-protected-resource/api/mcp`.

You can disconnect an app at any time under Settings > Connected apps on fundingtracker.app.

## Listings

- **Official MCP Registry:** [`app.fundingtracker/fundingtracker`](https://registry.modelcontextprotocol.io/v0.1/servers?search=fundingtracker). [`server.json`](server.json) is the published entry.
- **Glama:** [app.fundingtracker/fundingtracker](https://glama.ai/mcp/connectors/app.fundingtracker/fundingtracker)

## Support and policies

- **Support:** info@fundingtracker.app
- **Privacy:** https://fundingtracker.app/privacy
- **Terms:** https://fundingtracker.app/terms

The manifests in this repository are MIT licensed. FundingTracker's service and data are covered by its [terms](https://fundingtracker.app/terms).
