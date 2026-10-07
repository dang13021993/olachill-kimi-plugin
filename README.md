# OlaChill Japan Travel — Kimi Plugin

Kimi plugin that connects Kimi to OlaChill's public travel MCP server at `https://olachill.com/mcp`.

Kimi can search and compare Japan travel services from OlaChill (MIA Co., Ltd., Osaka): tours and day trips, activities, attraction and transport tickets, ryokan on request, private airport transfers, chauffeur cars, charter buses and coaches, helicopter flights, golf and travel eSIM — and look up an existing booking.

## Contents

```
kimi.plugin.json                      Plugin manifest (Kimi Plugin specification)
skills/olachill-japan-travel/SKILL.md Tool-selection and safety rules for the agent
commands/plan.md                      /olachill:plan <trip details>
commands/charter-quote.md             /olachill:charter-quote <itinerary>
LICENSE                               MIT
```

This plugin is configuration only. It contains no server code, credentials or data; all tools run on the OlaChill MCP server.

## Tools (13)

`search_travel_products`, `recommend_japan_travel_options`, `check_product_availability`, `search_helicopter_experiences`, `search_private_transfers`, `search_charter_vehicles`, `get_charter_quote`, `request_charter_quote`, `get_booking_status`, `list_olachill_services`, `search_golf_packages`, `search_chauffeur_services`, `search_esim_plans`.

All tools are read-only except `request_charter_quote`, which sends a quote request to OlaChill and is only called after the user explicitly confirms and provides a name and email.

## Install

Kimi Code CLI:

```
/plugins install https://github.com/dang13021993/olachill-kimi-plugin
/reload
```

Kimi Work: ask the Plugin Builder to import https://github.com/dang13021993/olachill-kimi-plugin, then Plugins → Personal → **+** to install.

## Usage examples

- "Find a Mt Fuji day tour from Tokyo for 2 adults on 15 November."
- "Airport transfer from Kansai Airport to Kyoto for 4 people with 6 suitcases."
- "Quote a 45-seat coach Osaka → Kyoto → Nara, one day, 40 people."
- `/olachill:plan 7 days Tokyo + Osaka in April, family of 4`

## Data and privacy

- No authentication is required; no API keys are stored in the plugin.
- Prices returned are public "from" or reference prices; availability and bookings are only confirmed when a tool result says so.
- Personal data (name, email) is sent only when the user asks to submit a charter quote request or to check a booking. See https://olachill.com for OlaChill's privacy policy.

## Support

MIA Co., Ltd. (OlaChill) — https://olachill.com
