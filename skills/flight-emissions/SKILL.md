---
name: flight-emissions
description: Estimate the CO₂ of general-aviation flying with TrimCarbon's tools, for a pilot, a flight school, a club or an operator, from aircraft type and hours, from a fleet, or from fuel burned. Use when someone asks about the carbon footprint, CO₂ or emissions of their flying, what offsetting it would cost, or about their own TrimCarbon offsets and certificates.
---

# Flight emissions with TrimCarbon

The TrimCarbon connector has these estimate tools:

- `search_aircraft`: finds aircraft types by name or ICAO type designator, with kg of CO₂ per flight hour.
- `estimate_flight_hours`: CO₂ from hours in one aircraft type, or in several for a fleet (up to 25 rows), per year or in total.
- `estimate_fuel_burn`: CO₂ from an amount of avgas 100LL, mogas or Jet A, in US gallons, liters or kg.
- `quote_offset`: TrimCarbon's prices to offset an amount of CO₂, with links to continue on trimcarbon.com. It doesn't buy anything.
- `import_logbook`: a card that reads a logbook export on the person's device (see Logbooks).

## Pick the tool from what the person gives

1. Aircraft type and hours: call `estimate_flight_hours`. For a school or club, put one row per type.
2. Fuel amounts: call `estimate_fuel_burn`. Ask which fuel and unit if they aren't clear.
3. A type name that may not match: call `search_aircraft` first, then use the name it returns.
4. If the person gives hours but no type, ask for the type. Don't guess one.
5. Use `period: "year"` when the hours are per year, and `"total"` for a single trip or a past total.

## Say what the figure covers

- The figures count the CO₂ from burning the fuel only. They leave out fuel production and non-CO₂ effects. Say so once.
- Each result links to the trimcarbon.com page that explains the figure. Share that link when the person asks how it's calculated.
- The result shows in a card where the person can change the hours or the fuel. If they change it, use the new figures that the card reports.

## Offsetting

- Call `quote_offset` only when the person asks what offsetting costs or how to offset.
- Present the options the tool returns: one-time (whole tonnes), and for yearly amounts the yearly and monthly plans.
- The person signs up and pays on trimcarbon.com, through the link. Never say that anything was bought in the chat.

## The person's own TrimCarbon account

These tools work after the person connects their TrimCarbon account. Claude asks them to connect it on the first call. They only read.

- `get_my_account`: their email, offset plan and offset API access.
- `get_my_impact`: how much CO₂ they have offset, by source and year, and the projects funded.
- `list_my_offsets`: their orders, newest first, with certificate numbers and links.
- `get_certificate`: one certificate by its number (`TC-7K2M-9QXF-4HJD`), with projects, registries and retirement serial numbers.
- `get_api_impact`: for companies on the offset API, the CO₂ offset through it.

Call them only when the person asks about their own account, offsets or certificates.

## Logbooks

To estimate from a logbook export (ForeFlight, Garmin Pilot, LogTen), call `import_logbook`. The card asks for the file, reads it on the person's device and uploads nothing. When the person shares the totals, you get the hours and CO₂ per aircraft type, for the last 12 months and for all flights. Types the card can't match are listed without CO₂: estimate them with `estimate_flight_hours` and the closest type, after you ask the person.

If the card doesn't show, point the person to https://trimcarbon.com/import-logbook, which does the same in the browser.
