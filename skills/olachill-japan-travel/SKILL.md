---
name: olachill-japan-travel
description: Use when the user wants to find, compare, check availability for or get a quote on Japan travel services — tours and day trips, activities and cultural experiences, attraction or transport tickets, ryokan, private airport transfers, cars with driver, charter buses or coaches, helicopter flights, golf, or a Japan travel eSIM — or to look up an existing OlaChill booking. Uses the OlaChill MCP tools.
---

# OlaChill Japan Travel

OlaChill (MIA Co., Ltd., Osaka) provides bookable and request-based travel services in Japan. This plugin connects the OlaChill MCP server (`olachill`). Always use its tools instead of guessing prices, availability or product details.

## Pick the most specific tool

| User need | Tool |
| --- | --- |
| Suggestions or a shortlist from preferences (area, interests, budget) | `recommend_japan_travel_options` |
| A named place, product or type of tour, activity, cultural experience, attraction/transport ticket or ryokan | `search_travel_products`, then `check_product_availability` for dates |
| Helicopter sightseeing, charter or transfer | `search_helicopter_experiences` |
| Private car with driver to/from an airport (1–6 people) | `search_private_transfers` |
| Bus, coach, minibus or van with driver for a group | `search_charter_vehicles` → `get_charter_quote` → (only after explicit confirmation) `request_charter_quote` |
| Golf rounds or golf trips | `search_golf_packages` |
| Car with driver by the day or hour (Alphard, Lexus, etc.) | `search_chauffeur_services` |
| Japan travel eSIM data plans (needs number of days) | `search_esim_plans` |
| An existing booking or request (needs reference + email) | `get_booking_status` |
| Other OlaChill services without a dedicated tool | `list_olachill_services` |

## Rules

1. Search tools before quote or action tools.
2. Charter transport: call `get_charter_quote` before `request_charter_quote`. Only call `request_charter_quote` after the user has explicitly agreed to send the request **and** has given their name and email. Set `user_confirmed` to `true` only in that case. Never invent contact details.
3. Prices are "from" prices, dated reference prices or estimates. Say so. Do not present availability, prices or bookings as confirmed unless the tool result says so.
4. Never invent availability, prices, booking references, product IDs or services. If a tool returns an error or no results, say so and suggest the closest alternative tool or a different query.
5. Always give the user the product `url` from the tool result so they can book or read full conditions on olachill.com, and mention `important_conditions` when present.
6. `get_booking_status` only with a booking reference and email the user supplied. Do not repeat other personal data back unnecessarily.
7. Out of scope: airline flights, hotels other than the listed ryokan, restaurants, weather, visas and general travel advice. Say OlaChill does not cover these.

## Answer format

- Lead with a short shortlist (name, area, duration, from-price with currency and tax basis, link).
- Then next steps: check a date, get a quote, or open the booking link.
- Reply in the user's language.
