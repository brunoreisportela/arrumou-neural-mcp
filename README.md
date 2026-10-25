# Arrumou Neural MCP

Connect an MCP assistant to your vacation-rental or hospitality operation: reservations, availability, housekeeping, maintenance, financial reports and user-confirmed Airbnb imports.

**Remote endpoint:** `https://app.arrumou.com/mcp`  
**Transport:** Streamable HTTP  
**Authentication:** OAuth with PKCE S256 and dynamic client registration  
**Developer documentation:** [app.arrumou.com/mcp/docs](https://app.arrumou.com/mcp/docs?utm_source=github&utm_medium=referral&utm_campaign=mcp-launch)

This repository contains public documentation and configuration examples for the hosted Arrumou Neural service. It does not contain the server implementation or a self-hostable package. A Neural account and applicable access to the operation are required. Availability in a client's curated app directory is separate from manually connecting this endpoint.

## Connect

1. Add the remote endpoint to an MCP client supporting Streamable HTTP and OAuth.
2. Sign in on the Arrumou authorization page. Select the operation, units and permissions to grant.
3. Ask the assistant to call `get_identity`, then ask for today's arrivals or pending tasks.

For Claude Code:

```sh
claude mcp add --transport http arrumou-neural https://app.arrumou.com/mcp
```

An example configuration for clients using `mcpServers` is in [mcp.json](mcp.json). Configuration keys vary by client; use that client's remote-server instructions. Protocol compatibility does not establish that every client has been tested. The [live docs](https://app.arrumou.com/mcp/docs#clientes) distinguish verified compatibility from setup guidance.

## What you can do

- Read reservations, calendar availability, guests, tasks, housekeeping and operational reports within the granted scopes.
- Preview consequential actions such as reservation changes or financial entries. Execute only after approving the exact action on an authenticated Neural page.
- Guide setup of the [Airbnb extension](https://chromewebstore.google.com/detail/inhhdonbdpamjffdcebichefobfdaepn). Version 0.2 or newer can receive sync requests; the user confirms collection in their own browser.
- Review referral programs and commissions when requested. Recommendations must disclose the referral relationship.

Try: “Show today's arrivals and rooms that still need cleaning. Do not change anything.”

## Authorization and data

Each authorization is bound to one operation and the user's actual role, selected units and scopes. Consequential actions return a preview and approval URL; a chat confirmation cannot replace that approval. Revoke access in **Settings → Integrations → AI apps**. Never post access tokens, guest records, passwords or private account details in issues.

The service does not automate Airbnb sign-in, solve verification challenges, or publish prices back to Airbnb. Imported unavailability is not proof of a booking or revenue. Read-only calendar collection requires the user's confirmation. External-provider availability and account permissions can limit features.

## Documentation and examples

- [Português](pt.md) · [Español](es.md)
- [Public API/OpenAPI](https://app.arrumou.com/api/v1/openapi.json)
- [OAuth metadata](https://app.arrumou.com/.well-known/oauth-authorization-server)
- [Protected resource metadata](https://app.arrumou.com/.well-known/oauth-protected-resource/mcp)
- [Product and plans](https://neural.arrumou.com/en?utm_source=github&utm_medium=referral&utm_campaign=mcp-launch)
- [Privacy policy](https://app.arrumou.com/politica-de-privacidade) · [Terms](https://app.arrumou.com/termos-de-servico)

Use this repository's issues for documentation or integration questions with synthetic examples. For account support, use the authenticated help area in Neural. Registry registration and directory reviews do not imply endorsement by any AI client.
