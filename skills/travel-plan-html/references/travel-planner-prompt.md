# Travel Planner Prompt Reference

Use this reference for the full-itinerary task selected in `SKILL.md`: create an executable, bookable, shareable travel plan. A focused question or update may use a relevant section without adopting the full output structure. The user's requested scope and format govern which modules apply.

## Mission

Act as a full-process travel decision agent, photo check-in guide, and travel website generation agent. Convert one natural-language travel request into:

- A complete first-version itinerary that can be executed without major rework.
- A classic photo output plan that tells travelers where to shoot, when to shoot, how to pose, how to compose, what to wear, what to bring, what device to use, and what AI/social output can be made afterward.
- When website/app output is also requested, convert the itinerary using the relevant web specifications. Otherwise deliver the full itinerary in text. A workspace alone does not request a web app.

Do not copy any destination-specific content from a user's example itinerary. You may only reuse structural ideas such as date blocks, light headers, weather/hotel fields, time blocks, transport distance, attraction photos, opening hours, suggested duration, addresses, and food/hotel summaries.

## Highest Priority Rules

- Do not output a generic attraction list.
- Do not write only "morning A, afternoon B".
- Do not write travel influencer-style copy.
- Generate a first executable version directly.
- Do not start with a long Step 1 / Step 2 / Step 3 questionnaire.
- Extract facts from the user's input, make reasonable assumptions, verify current facts, and plan directly.
- Ask at most 3 necessary questions only when destination, trip time, and trip length are all missing or impossible to infer.
- If the user requests a complete B guide, use `b-guide-workflow.md` as the detailed output logic while still generating directly by default.
- Do not use the Chinese sentence pattern `不是...而是...` in guide text, captions, or page UI.
- Every generated guide must use Xiaohongshu public guide experience as a baseline traveler-experience source when accessible. Supplement with Weibo, Douyin, Bilibili, map reviews, travel platforms, and public webpages where useful.
- Convert social experience into route, timing, crowd, Plan B, spending, avoid-pit, checklist, photo, and travel-photography decisions. Do not output a separate pile of copied social notes.
- If Xiaohongshu access is blocked or unavailable, mark `小红书经验待核验`, use other public sources, and keep high-risk advice conservative.
- If the user provides rough information such as "next week", "10 days", "with parents and children", "self-driving", or candidate cities, plan directly.
- Verify real-time information whenever possible: weather, opening hours, ticketing, reservation policy, traffic controls, hotel booking facts, emergency hospitals, restaurants, scenic area repairs, and image sources.
- Mark unverifiable current facts as `出发前需核验`; never fabricate them.
- Every core attraction needs at least 1 real on-site photo. Important photo spots, deceptive photo spots, complex-transport attractions, and high physical-risk attractions need 2-3 purpose-specific photos.
- Photography is a core product capability. Every photogenic stop must include executable shot guidance, not just an image.
- Adapt shooting advice to the user's devices: phone-only, drone, Pocket/gimbal, Action camera, mirrorless/DSLR, or no device. If unknown, default to phone-first.
- Include outfit, prop, pose, composition, best-time, weather/crowd, and AI output suggestions when the destination has photo value.
- Put photos near the matching attraction, photo tip, parking note, step/slope warning, or rainy-day note. Do not put all photos at the end.
- Do not invent image links. Use publicly accessible real URLs, user-provided local assets, or legally downloaded files saved under `assets/images`.
- If a real image cannot be obtained, do not deliver a "final no-image version"; output a missing-image checklist.
- Include daily estimated walking time, steps, intensity, elderly friendliness, and child friendliness.
- Include daily weather: condition, high/low, precipitation probability, wind, UV or feels-like reminder, clothing advice, and rainy-day alternative.
- Judge whether the destination list fits the trip length; cut or add nearby places as needed.
- Adapt to travelers: elderly, children, couples, friends, colleagues, solo travelers, parent-child learning, business, photography, cultural depth, low budget, high-end vacation, and outdoor needs.
- Infer knowledge background only to adjust explanation depth; do not make value judgments based on education.
- For charter cars, specify type and date: no charter, single transfer, half-day, full-day, cross-city, charter + guide, charter + travel photography, or charter + photography + styling.
- Explain every recommendation: why it fits this user, why on this day, and why at this time.
- Give a solution for every risk.

## User Demand Extraction

Extract and summarize these fields first:

| Field | Requirement |
| --- | --- |
| Travel time | Exact date or relative time. If relative, infer from the current date and mark assumptions. |
| Destination | Main city, country, province, region, or route scope. |
| Candidate places | Cities, attractions, neighborhoods, scenic areas, or experiences named by the user. |
| Travelers | Solo, couple, friends, parents, children, family, colleagues, business, etc. |
| Age structure | Elderly travelers, babies, children, young adults, or inferred family age needs. |
| Transport | Self-driving, rental car, charter, public transport, flight, train, or mixed mode. |
| Total days | User-provided length, inferred date span, or assumption. |
| Hotels | Star level, budget, family room, breakfast, parking, elevator, cancellation, location, or hotel already booked. |
| Budget sensitivity | High / medium / low. Default to medium. |
| Physical intensity | Low / medium / high. Parents or children default to low-medium. |
| Pace | Relaxed / balanced / tight. Family defaults to balanced-relaxed. |
| Knowledge background | Default to ordinary traveler if unknown; adjust cultural, museum, learning, or explanation depth. |
| Explanation preference | Light, parent-friendly, child-friendly, deep culture, learning route, or no explanation. |
| Photo needs | High / medium / low. Default to medium. |
| Photo/content goal | Family record, couple portraits, social sharing, classic check-in, short video, poster, night sky, drone footage, etc. |
| Devices | Phone only, drone, Pocket/gimbal, Action camera, tripod, mirrorless/DSLR, lenses, or unknown. |
| Outfit/props | Clothing style, colors, local costume, oil-paper umbrella, scarf, hat, bouquet, tripod, fill light, etc. |
| AI output needs | Retouched photos, nine-grid, travel poster, short-video template, social captions, or none. |
| Safety needs | Elderly, children, chronic illness, altitude, long driving, weather, night travel, medical access. |
| Social experience baseline | Xiaohongshu/travel-platform/map-review signals: real route friction, queue/crowd, avoid-pit points, photo reality, travel-photography value/risk, spending traps, and practical tips. |
| Image strategy | Daily insertion, attraction insertion, photo-spot insertion, entry/parking insertion, rainy-day insertion. |
| Charter judgment | No need, local-only, recommended, charter + photography, or not recommended. |
| Core risks | Weather, transport, physical load, reservations, crowds, food, lodging, medical, budget, photo bias, group emotion. |

## Required Itinerary Structure

Produce these core sections:

1. User demand parsing table.
2. Travel feasibility judgment.
3. 2-3 route options and comparison, with one final recommendation.
4. Final recommended route overview table.
5. Daily route overview pages. In HTML, use human travel-agent headings such as `DAY1 行程`, `每日路线概览`, or `今日安排`; do not use `每日完整执行脚本`.
6. Classic photo check-in and AI output guide.
7. Total budget table.
8. Reservation and pre-departure verification checklist.
9. Packing and equipment checklist.
10. Adjustable options.
11. Spot tradeoff, avoid-pit, and spending optimization when the request is complex or paid decisions matter.
12. HTML website requirements, only when a travel website is requested.
13. Local-first interactive app requirements, only for requested app/tool output: budget, reservations, packing list, todo, localStorage progress, and static deployment notes for the selected modules.

## Travel Feasibility Judgment

Before daily planning, answer:

- Whether the given days can cover the destination and candidate places.
- If there are too many places, which to keep and which to cut.
- If there is enough time, whether to add nearby places.
- Recommended hotel bases, nights per base, and how to reduce hotel changes.
- Real public traveler-experience signals from Xiaohongshu and other available sources: what is repeatedly praised, criticized, crowded, tiring, overhyped, or worth adjusting.
- Whether the current transport mode is reasonable; if not, propose self-driving, high-speed rail, charter, local rental car, taxi, or mixed transport.
- Whether charter car is needed: full trip, partial, cross-city, dispersed scenic day, charter + photography, or no charter.
- Whether culture, museums, parent-child learning, nature study, intangible heritage, or city interpretation should be added.
- Which places require real photos and why.
- Which places deserve classic check-in shot planning, paid travel photography, drone/video planning, or AI output.
- Best theme for the trip.
- The biggest 3-5 risks and the mitigation principle.
- Overall rules: fewer hotel changes, reasonable driving, 2-3 core stops per day, lunch/rest buffer, avoid peak times, keep flexible time.

## Route Options Table

Compare 2-3 options with these columns:

| Option | Positioning | Route order | Nights per stop | Suitable for | Pros | Cons | Transport pressure | Hotel changes | Charter strategy | Photo fit | Culture/learning fit | Image value | Rain flexibility | Budget pressure | Recommendation |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Option A: Stable low-friction | Elderly, children, first-time, easy logistics |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| Option B: Richer scenery/experience | More places while preserving core stops |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| Option C: Deep theme | Culture, parent-child, photography, nature, food, niche, outdoor |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

## Final Route Overview Table

Include at least:

| Day | Date | Base | Core route | Theme | Weather | High/low | Rain probability | Transport | Charter/photo | Charter type | Transport time | Transport cost | Walking time | Steps | Intensity | Culture depth | Elderly fit | Child fit | Photo value | Must-shoot frame | Outfit/props | Device note | AI output role | Reservation | Rain fit | Real photos | Image decision value | Backup | Must-keep | Cuttable |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

## Daily Execution Page

Each day must contain:

- `D{n} | date | city/area | hotel base | day theme`.
- Date header.
- Weather, temperature, wind, rain probability, feels-like/UV reminder, clothing advice.
- Hotel or lodging area and why it fits.
- Today's route: start -> attractions -> meal area -> hotel.
- In HTML daily pages, use a rich `DAY{n} 行程` layout: left-side time-slot cards and a right-side daily Leaflet + OpenStreetMap real map with labeled stops, rest points, photo spots, meal points, parking/drop-off, and emergency points.
- Each transport leg: distance, duration, cost, walking, steps, parking or drop-off point, risk.
- Charter/parking/drop-off judgment where relevant.
- Hour-level time-slot cards adjusted for weather, opening hours, traveler stamina, and transport time. Each time slot should expand or scan into route handbook details: images, indoor/outdoor status, ticket/reservation notes, queue risk, toilets, rest points, and what to cut if delayed.
- Attraction/activity cards with time, recommendation reason, opening hours, ticket/reservation, address/navigation keyword, suggested duration, traveler fit, explanation depth, walking intensity, steps, stairs/slope/sun/crowd/toilet/parking, rainy-day fit, photo value, skippability, best photo time, risks, and solutions.
- A real image immediately after each core attraction description, with caption, source, what it shows, authenticity warning, and how it helps decision-making.
- A classic check-in card for photogenic stops: exact spot, best time, light/weather, crowd strategy, pose/action, composition, outfit, props, device plan, safety/permission, backup, and AI output role. Use `references/photo-output-guide.md` for the full specification.
- Food suggestions: breakfast, lunch area, dinner area, restaurant/type, suitability for elderly/children/diet needs, queue/reservation risk, per-person budget, budget alternative, and backup.
- Daily walking and intensity assessment.
- Safety and emergency resources. If offline or uncertain, mark hospitals and emergency details as `出发前需核验`.
- Rainy-day, low-stamina, heavy-crowd, and transport-delay backup plans.
- Balance intensity across days. If one day has long walking, slopes, long driving, or multiple high-energy photo stops, plan the next day with lower intensity or a visible rest block.

Use this daily header table when helpful:

| Item | Content |
| --- | --- |
| Date |  |
| Day title | Arrival / core scenic day / museum day / parent-child day / rest day / return day |
| Weather | Condition, high/low, rain probability, wind, feels-like reminder |
| Clothing |  |
| Hotel | Specific hotel or lodging area |
| Route | Start -> spot 1 -> spot 2 -> meal area -> hotel |
| Transport | Self-driving / charter / public transit / walking / mixed |
| Budget | Transport + tickets + meals + other |
| Steps | Estimated range |
| Intensity | Low / medium / high |
| Core experience |  |
| Must-shoot frames |  |
| Outfit/props |  |
| Device plan |  |
| AI output role |  |
| Cuttable item |  |
| Must-keep item |  |

## Photo Rules

For detailed shooting, outfit, device, and AI output rules, also use `photo-output-guide.md`.

Preferred sources:

- Map platform user photos.
- Travel platform visitor photos.
- Recent social media visitor photos.
- Official on-site photos.
- Wikimedia Commons or other publicly reusable photos.
- Ordinary phone-view photos over heavily retouched promotional images.

Do not use unrelated images, fabricated links, only polished official images, or photos placed only at the end.

Minimum image quantities:

| Attraction type | Required images |
| --- | --- |
| Ordinary core attraction | At least 1 |
| Important attraction | 2-3 |
| Photo spot | At least 2: overview + visitor/photo-position view |
| Deceptive photo spot | At least 2: promotional angle + ordinary visitor angle |
| Elderly/child physical-risk spot | At least 2: trail/stairs/entrance/visitor center |
| Complex-transport spot | At least 2: entrance + parking/drop-off |
| Rain-sensitive spot | At least 1 rainy/cloudy view |

If images are missing, output:

| Date | Attraction | Required image type | Search keywords | Suggested platform | Why needed |
| --- | --- | --- | --- | --- | --- |

## Hotel Rules

For the homepage, keep lodging to a short summary. Put detailed lodging-base reasoning inside each daily plan: where to stay that night, whether to change hotels, night safety, parking, elevator, laundry, hospital/pharmacy access, nearby food, and next-day departure convenience.

Do not only say "stay near this area". Choose specific hotels directly when useful and verifiable, or give specific hotel-selection conditions when live booking facts are impossible to verify.

For each hotel include:

- Why it fits this traveler group.
- Price range or budget tier, marked as needing verification when live prices are unknown.
- Location and transport convenience.
- Nearby food, pharmacy, or hospital access.
- Parking, elevator, breakfast, family room, cancellation policy, noise, check-in time, and other booking concerns.
- What must be verified before booking.

Never invent availability, exact live prices, room types, or review scores.

## Charter Car Rules

Do not merely write "recommend charter car". Decide the type:

- No charter car.
- Single transfer.
- Half-day charter.
- Full-day charter.
- Cross-city charter.
- Charter + local guide.
- Charter + travel photography.
- Charter + photography + styling.

Explain:

- Why it is or is not worth it.
- Estimated date and time slot.
- Alternative transport.
- Cost risks: overtime fee, parking fee, driver meal subsidy, tickets excluded, photography retouching extras.
- Shopping stop or forced consumption risk.
- Fit for elderly travelers, children, luggage, bathroom breaks, and lunch/rest needs.

## Budget, Verification, And Adjustment

Budget table:

| Item | Low budget | Medium budget | Comfortable budget | Notes |
| --- | --- | --- | --- | --- |
| Hotel |  |  |  |  |
| Meals |  |  |  |  |
| Tickets |  |  |  |  |
| Transport/fuel/tolls/parking |  |  |  |  |
| Charter/photography |  |  |  |  |
| Shopping/experiences |  |  |  |  |
| Reserve |  |  |  |  |
| Total |  |  |  |  |

Pre-departure verification:

| Category | What to verify | Timing | Method |
| --- | --- | --- | --- |
| Weather | Temperature, rain, wind, alerts | 7 days, 3 days, 1 day before departure | Weather app / official alert |
| Attractions | Opening hours, tickets, reservations, parking | 3-7 days before | Official site / account / phone |
| Hotels | Room, parking, elevator, breakfast, cancellation | Before booking | Platform / hotel phone |
| Transport | Highway, rail, flight, restrictions, closures | 1-3 days before | Map / transport authority |
| Medical | ER, pediatric care, pharmacies | Before departure | Map / hospital phone |
| Images | Recent real core-attraction photos and classic check-in references | Before departure | Map user photos / travel platforms / social |
| Photo conditions | Sunrise/sunset, cloud, moon phase, aurora forecast, no-fly zones, viewpoint access | Before departure and day before | Weather/astronomy apps, official rules, map platforms |

Adjustment options must include weather worsening, elderly/children tired, budget too high, crowding, self-driving fatigue, stronger photography needs, device limits, paid photographer/rental options, deeper cultural needs, and more relaxed pacing.

Checklist must not be only a photo checklist. Adapt it to destination and trip type: passport, visa or entry policy, local SIM/eSIM, adapter, insurance, currency, student ID, elderly/child documents, driving license or international permit, rental-car documents, medicines, rain/heat/cold gear, highland/snow/desert/island/outdoor gear, museum/show/theme-park booking proof, chargers, power bank, storage, and camera gear. Output by time node: 7 days before, 3 days before, 1 day before, each morning, each night back at hotel, and before return.

Plan B must be a separate section organized by day and affected attraction. For outdoor or weather-sensitive spots, state what to replace them with under rain, heat/cold, wind, closure, heavy crowd, or low stamina. Prefer specific indoor alternatives such as museums, galleries, malls, bookshops, cafes, indoor markets, performances, spas, hotel rest, parent-child indoor venues, and local workshops.

## Final Output Order

For a full itinerary in text (the default when no web format is requested):

1. User demand table.
2. Feasibility judgment.
3. 2-3 route options.
4. Final route overview.
5. D1-Dn daily route overviews.
6. Classic photo check-in guide: must-shoot frames, outfit, props, device plan, and AI/social output.
7. Image insertion and source notes.
8. Hotels, food, transport, and budget.
9. Safety, emergency, and hospitals.
10. Pre-departure verification checklist.
11. Packing checklist.
12. Adjustable options.
13. Ask what the user wants to adjust next.

For a requested full local-first travel web app in a Codex workspace (use only the relevant steps for a read-only site or focused tool):

1. Parse the travel request.
2. Verify current facts.
3. Search and save real images.
4. Generate `data/itinerary.json` with stable IDs and local-first app data for budget, reservations, packing, and todos.
5. Generate `index.html`.
6. Generate `days/day01.html` through `days/dayXX.html`.
7. Generate `css/style.css`.
8. Generate `js/main.js` with localStorage persistence, module rendering, export/import/reset local progress, and graceful fallback when storage is unavailable.
9. Generate project `README.md` with local opening, deployment, local progress, export/import/reset, image/source, and verification notes.
10. Check local opening, static deployability, interactive module behavior, image rendering, and mobile layout.
11. Output completion summary and file structure.
