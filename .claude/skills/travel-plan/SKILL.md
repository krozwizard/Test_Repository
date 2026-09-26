---
name: travel-plan
description: Build a complete travel plan (itinerary, bookings checklist, food picks, packing list) for an upcoming trip and save it under travel/plans/. Use whenever the user says they are planning a trip, mentions a destination and dates, or asks for an itinerary. Example: "/travel-plan Osaka, Nov 12-16, leisure".
---

# Travel plan

Turn a short trip request into a finished plan file, the same way every time.

## 1. Gather the trip details

Pull these from the request. Ask only for what is missing and cannot be defaulted.

| Detail | Required | Default if not given |
| --- | --- | --- |
| Destination (city/region) | yes | — |
| Dates (start and end) | yes | — |
| Departure city | no | value in `travel/preferences.md` |
| Purpose (leisure / business / mixed) | no | leisure |
| Travelers | no | 1 |
| Budget level | no | value in `travel/preferences.md` |
| Language of the plan | no | the language the user wrote the request in |

## 2. Read the traveler's context

- `travel/preferences.md`: standing preferences (home airport, seat, hotel style, pace, dietary notes, loyalty programs). Follow them.
- `profile.md`: interests to weave into the itinerary. The traveler loves Japanese food, culture and scenery, loves pizza (Margherita, pepperoni, Neapolitan), and follows AI and semiconductor technology closely.
- Existing files in `travel/plans/`: avoid repeating the exact same restaurants or sights from earlier trips to the same place unless the user asks for favorites.

## 3. Research

If web search is available, check and cite:
- Weather and daylight for the dates
- Local holidays, festivals or events during the stay (and crowd warnings)
- Entry requirements for a Korean passport holder (visa, arrival registration such as Visit Japan Web)
- Transit options from the arrival airport and useful passes
- For business or mixed trips: tech and industry sites relevant to AI or semiconductors, if any are near the destination

If web search is not available, say so at the top of the plan and mark time-sensitive items as "verify before travel".

## 4. Write the plan

Copy `travel/TEMPLATE.md` to `travel/plans/<start-date>-<destination-slug>.md` (for example `travel/plans/2026-11-12-osaka.md`) and fill in every section. Rules:

- Day-by-day itinerary with morning / afternoon / evening blocks. Keep the pace set in preferences; leave one unscheduled block per day.
- At least one local specialty meal per day, and one well-rated pizza place for the trip when the destination has one.
- Group sights by neighborhood to cut transit time; give the transit step between blocks.
- Every booking item in the checklist gets a "book by" date counted back from the trip start.
- Keep prices in local currency with an approximate KRW figure.

## 5. Finish

1. Show the user a short summary: dates, the headline of each day, and the booking deadlines that fall in the next two weeks.
2. Commit the new plan file with a message like `Add travel plan: Osaka, 2026-11-12 to 11-16` and push to the current branch.
3. Offer to adjust anything (pace, hotel area, restaurants) and update the same file when asked.
