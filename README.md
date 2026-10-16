# TrimCarbon for Claude

Estimate the CO₂ of general-aviation flying in Claude: for one pilot, for a flight school or club fleet, or from the fuel you burned. TrimCarbon has figures for about 60 aircraft types, from a Cessna 152 to a Beechcraft Baron, based on each type's fuel flow at about 75% power.

This plugin adds:

- **The TrimCarbon connector**, a remote MCP server at `https://mcp.trimcarbon.com/mcp`.
- **The `flight-emissions` skill**, which tells Claude which TrimCarbon tool fits each question.

## Install

In Claude Code:

```
/plugin install trimcarbon --marketplace trimcarbon/claude
```

On Claude Code before 2.1.275, add the marketplace first:

```
/plugin marketplace add trimcarbon/claude
/plugin install trimcarbon@trimcarbon
```

In the Claude apps, add the connector only: https://trimcarbon.com/ai has the steps.

## What you can ask

- "What's the CO₂ of 50 hours a year in a Cessna 172?"
- "Our school flies 600 hours in 172s and 120 hours in a Seminole. What's our footprint?"
- "How much CO₂ does burning 100 gallons of avgas release?"
- "What would it cost to offset that?"

Results show in an interactive card where you can change the hours or the fuel amount.

## Tools

| Tool | What it does |
|---|---|
| `search_aircraft` | Finds aircraft types by name or ICAO code, with kg of CO₂ per flight hour |
| `estimate_flight_hours` | CO₂ from hours in one or more aircraft types, per year or in total |
| `estimate_fuel_burn` | CO₂ from avgas 100LL, mogas or Jet A, in US gallons, liters or kg |
| `quote_offset` | TrimCarbon's prices to offset an amount of CO₂, with a link to continue on trimcarbon.com |
| `import_logbook` | A card that reads your ForeFlight, Garmin Pilot or LogTen export on your device and shows the CO₂ by aircraft type. The file is never uploaded; you choose to share the totals |

With a connected TrimCarbon account, these tools read your own account:

| Tool | What it does |
|---|---|
| `get_my_account` | Your email, your offset plan and your offset API access |
| `get_my_impact` | How much CO₂ you have offset: in total, by source, by year, and the projects funded |
| `list_my_offsets` | Your offset orders, newest first, with their certificate links |
| `get_certificate` | One certificate: projects, registries, retirement serial numbers, links to the certificate and its PDF |
| `get_api_impact` | For offset API customers: the CO₂ offset through the API, in total and by month |

All tools are read-only. Nothing is bought in the chat: you sign up and pay on trimcarbon.com.

## Data

The plugin sends data only to TrimCarbon's MCP server at `https://mcp.trimcarbon.com/mcp`. Each tool call sends the tool's inputs (aircraft types, hours, fuel amounts, an amount of CO₂ for prices, or a certificate number). A logbook file stays on your device; only the totals you share go to the conversation. The server doesn't receive your conversation. The estimate tools need no account. The account tools work only after you connect your TrimCarbon account (OAuth) and only read it; you can remove the connection at any time on trimcarbon.com/account. TrimCarbon records which tools are used, without names or emails, to improve them, and keeps a 90-day log of which account tools read your account. See the [privacy policy](https://trimcarbon.com/legal/privacy-policy).

The figures count the CO₂ from burning fuel only. They leave out fuel production and non-CO₂ effects.

## Support

- Setup and details: https://trimcarbon.com/ai
- Contact: contact@trimcarbon.com or https://trimcarbon.com/contact

## License

MIT. See [LICENSE](LICENSE).
