# CasaNest MCP

Search public property listings in Portugal from an MCP-compatible assistant. Read and compare listings, and consult INE municipal housing statistics with their source and period.

- [Português: ligar e experimentar](https://casanest.eu/ia)
- [English: connect and try](https://casanest.eu/en/ai)
- [Detailed technical documentation](https://casanest.eu/casanest-ai.md)

## Connection

| Setting | Value |
| --- | --- |
| Server URL | `https://casanest.eu/mcp` |
| Transport | Streamable HTTP |
| Authentication | None / No sign-in |
| Request headers | None required |

A browser GET to `/mcp` returns 405 by design. Configure the URL in an MCP client; clients send POST requests. No CasaNest API key is needed.

## Tools

| Tool | Purpose |
| --- | --- |
| `search_properties` | Search current public listings using structured filters |
| `get_property` | Read a listing returned by search |
| `compare_properties` | Compare 2–4 distinct public listings |
| `get_area_statistics` | Read INE municipal sale value per square metre, source and period |

Example prompts:

> Use CasaNest to find up to 5 properties for sale in Portugal. Include prices, municipality and listing links.

> Search CasaNest for rooms to rent in Leiria municipality, Leiria district, up to 500 euros per month. Keep my filters if there are no matches.

> Use CasaNest to read Leiria's median completed dwelling sale value per square metre. Include the source and period.

Confirm that the assistant actually invokes a CasaNest tool. Empty results are valid and reflect the published inventory. Missing values mean unknown, never zero. INE transaction statistics are not asking prices, valuations or forecasts.

## Public metadata and API

The server is listed as **eu.casanest/catalogue** in the [official MCP Registry](https://registry.modelcontextprotocol.io/v0.1/servers/eu.casanest%2Fcatalogue/versions/latest). This registers the integration metadata; it does not install it automatically in every assistant.

- [Tool schemas / server card](https://casanest.eu/.well-known/mcp/server-card.json)
- [CasaNest connector on Glama](https://glama.ai/mcp/connectors/eu.casanest/catalogue)
- [MCP Registry manifest](https://casanest.eu/mcp-server.json)
- [OpenAPI 3.1](https://casanest.eu/api/public/v1/openapi.json)
- [Optional llms.txt index](https://casanest.eu/llms.txt)

A read-only API example:

```sh
curl --fail --show-error 'https://casanest.eu/api/public/v1/properties?purpose=sale&limit=5'
```

The live technical documentation is authoritative. Queries must respect the published schema, geography, budget periods and rate limits. Do not scrape private routes or bypass a denied request.

## Scope and privacy

The integration exposes only public listings and public statistical data. It cannot publish listings, send messages, reveal private account or CRM data, reserve properties or make payments. Open the listing on CasaNest to contact the advertiser. Requests contain the filters and public IDs needed for the query; do not include personal information. Links may include campaign parameters for aggregate attribution.

This repository contains public integration documentation, not the CasaNest application's source code. Adding a server to an account or registry is not approval by Claude, OpenAI or Google, and does not guarantee ranking in web search.

[Support](https://casanest.eu/contacto) · [Privacy](https://casanest.eu/privacidade) · [Terms](https://casanest.eu/termos)
