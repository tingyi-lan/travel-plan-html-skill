# B Guide Workflow

Use this reference for a full-process traveler decision guide, `B 攻略`, or detailed itinerary planning selected in `SKILL.md`. This is not the B-side cultural-tourism proposal workflow. A focused lodging, transport, budget, photo, or safety question may consult the relevant section without requiring the complete B guide. Deliver text unless web output is requested or already established.

## Output Language Rule

Generated travel guides, page copy, captions, and UI text must not use the Chinese sentence pattern `不是...而是...`. Rewrite with direct positive statements.

## Direct Generation Mode

Default to generating a first executable version directly. Extract known facts, make conservative assumptions for missing low-risk details, label defaults clearly, and continue into the guide.

Ask at most 3 short questions only when destination, timing, and trip length are all missing or when a missing detail would make the plan unsafe or impossible. If the user asks for `先确认信息`, `先问我`, `完整问询`, or `按问询表来`, use the compact confirmation groups below. Otherwise, use them as an internal checklist while generating.

## Baseline Xiaohongshu Experience Layer

Every B guide must incorporate real public traveler experience before final route decisions. Use Xiaohongshu public guide/search results as the default Chinese experience source when accessible, then supplement with Weibo, Douyin, Bilibili, map reviews, travel platforms, and public webpages as available.

Use this layer to shape the guide, not as a separate pile of notes:

- Route order, route cuts, and whether a plan is too packed.
- Queue/crowd windows, weather sensitivity, and low-stamina alternatives.
- Repeated avoid-pit points, hidden costs, package traps, charter/travel-photo risks, rental risks, and restaurant/hotel complaints.
- Travel photography signals: photographer or studio style, sample consistency, makeup/styling, clothing, route coverage, shooting duration, raw files, retouch count, add-photo or extra-retouch fees, weather reschedule, copyright/use rights, and whether charter + photography is worth it.
- Photo spots, outfit colors, phone-first shooting tips, spot-specific gear, and homogeneous/overheated frames.
- Daily Plan B, checklist items, and pre-departure verification tasks.

For a normal guide, search patterns should include `目的地 + 攻略`, `目的地 + 避雷`, `目的地 + 人多吗`, `目的地 + 路线`, `目的地 + 住宿`, `目的地 + 交通`, `目的地 + 旅拍`, `目的地 + 写真`, and key attraction-specific queries. For family, parents, solo, photography, food, outdoor, or culture trips, add matching persona keywords.

Do not copy note text, comments, titles, or creator expressions. Extract recurring signals and write original decisions. If Xiaohongshu access is blocked or unavailable, mark `小红书经验待核验`, use other public sources, and keep the guide conservative.

1. Traveler profile and knowledge depth:
   - Trip type, party size, age structure, gender/identity if relevant, knowledge background, culture/learning depth, stamina, pace, rest needs, restrictions such as heat sensitivity, motion sickness, stomach sensitivity, slopes, early starts, crowd avoidance, night safety, accessibility.
   - Use knowledge background only to tune museum, culture, route explanation, and parent-child learning depth. Do not make value judgments.
2. Lodging needs:
   - Budget/tier, willingness to change hotels, priorities such as safety, transit, scenery, price, parking, elevator, breakfast, laundry, family room, hospital/pharmacy, nearby food, quietness, nightlife, and preferred area.
3. Differentiated travel needs:
   - Classic first-time route, niche route, slow travel, culture/museums, nature, food, photo output, travel photography, city walk, night travel, cafes/bookstores/boutiques, intangible heritage, performances, exhibitions, outdoor, parent-child, shopping, diet needs, local experiences.
4. Time, transport, budget, charter, and stamina boundaries:
   - Arrival/return time, main transport, daily transport budget, charter willingness, charter type, charter + travel photography need, charter budget, daily walking tolerance, early-start tolerance.
5. Real image insertion:
   - Image richness, image type, insertion position, authenticity requirement, caption/source/detail preference. Images must support decisions, not decorate the page.
6. Optional confirmation:
   - If the user explicitly wants confirmation before the full guide, output a compact table covering travel time, destination, days, candidate places, traveler profile, age/gender/identity, knowledge background, explanation depth, stamina, restrictions, lodging, transport, charter, walking, preferences, food, image richness, image type, insertion location, authenticity, and real-time verification.
   - If the user did not request confirmation, put assumptions at the top and generate the guide.

## Traveler-Type Mapping

Adapt the guide to the traveler:

| Traveler Type | Planning Focus |
| --- | --- |
| Young female solo trip | Safety, night return, lodging area, walking distance, photo output, solo-friendly meals |
| Young male solo trip | Transport efficiency, budget, walking intensity, night-route safety |
| Student | Value, public transport, low ticket cost, photo spots |
| Working adult | Relaxed rhythm, comfortable lodging, less friction, better meals |
| Parents trip | Low intensity, fewer hotel changes, hospitals, toilets, parking, elevators, midday rest |
| Parent-child | Children's activities, toilets, rest points, safety, flexible rhythm, simple learning tasks |
| Photographer/content creator | Light, spots, timing, outfits, devices, content output |
| Culture/learning traveler | Museums, historic districts, city context, architecture/literature/history explanation |
| Parent-child learning | Knowledge broken down for children, interactive tasks, low-intensity learning route |
| Low-budget traveler | Spend on safe lodging, transport efficiency, core tickets, necessary rest; avoid expensive default charter |

## Full B Guide Results

For a complete B guide, produce these results within the user's requested scope. For a focused update, revise only the affected results:

1. User demand parsing table:
   - Travel time, destination, candidate places, travelers, transport, days, trip type, knowledge background, explanation depth, budget sensitivity, stamina, rhythm, charter judgment, charter dates, charter risks, image insertion strategy, social-experience findings, core risks.
2. Travel feasibility judgment:
   - Fit between days and destinations, what to keep/cut/add, lodging-base logic, transport mode, charter type, culture/learning depth, which places require real images, trip theme, top 3-5 risks, and planning principles.
3. Two or three route options:
   - Stable low-friction, richer scenery/experience, and a user-interest theme route. Compare route order, nights, suitable people, pros/cons, transport pressure, hotel changes, charter strategy, travel-photo fit, culture fit, image value, weather flexibility, budget, and recommendation.
4. Final route overview:
   - Day, date, base, core route, theme, transport, charter/photo, transport time/cost, walking time/steps, intensity, culture depth, traveler friendliness, photo value, reservation, rain fit, real-image status, image judgment, bad-weather alternative, must-keep, cuttable.
5. D1-Dn daily route overview:
   - Use human travel-agent page language such as `DAY1 行程`, `每日路线概览`, and `今日安排`. Do not use UI headings like `每日完整执行脚本`.
   - Include daily goal, route, transport and charter judgment, time table, attraction/activity cards, meals, lodging base for that day, intensity, safety/emergency, weather/crowd/closure alternatives, and daily reminders.
6. Spot tradeoff table:
   - Attraction/activity, type, recommendation, reason, risk, suitable/unsuitable travelers, suggested duration, walking, transport, parking, food, toilets, rain fit, photo value, culture value, required real image, suggested image type, image keywords, nearby medical keywords, one-sentence decision.
7. Safety and emergency module:
   - Hospitals/ER/pharmacies around each lodging base and core area when verifiable; otherwise search templates. Include fever, stomach issues, falls, motion sickness, altitude, heatstroke, cold, allergy, lost person, lost documents, phone battery, vehicle trouble, transport delays, insurance, and overseas embassy/emergency number logic.
8. Pre-departure checklist, reservation checklist, adjustment rules, avoid-pit and spending optimization, photo/outfit/content sharing, layered companion experience, and post-trip summary.

## Daily Page Content Rules

Apply these layout rules when daily HTML pages are requested. Each day should feel rich, visual, and executable. Text itineraries use equivalent planning detail without creating pages or maps.

- Title the main section `DAY{n} 行程`, with the left side as time-slot cards and the right side as the day's real map.
- Use a Leaflet + OpenStreetMap daily map by default, filtered to that day's route, with labeled stops, rest points, photo spots, meal points, and emergency points.
- Each time slot should be expandable or scannable. Under each time period, include transport, images, attraction notes, indoor/outdoor status, photo advice, route handbook details, ticket/opening/reservation notes, crowd/queue risk, toilets, rest points, and what to cut if delayed.
- Every attraction card should include whether it is indoor or outdoor, image(s), photo advice, traveler fit, walking/stairs/slope/sun/crowd/toilet/parking risk, and rainy-day value.
- Each transfer should show transport mode, estimated time/cost, steps or walking minutes, stamina cost, and whether the next day should be lighter.
- Balance high and low intensity across days. If one day is tiring, arrange a lower-intensity next day or a clear rest block.

## Plan B, Checklist, And Lodging Placement

Separate these into distinct sections:

- Plan B:
  - Format by day and by affected attraction.
  - For each outdoor/weather-sensitive spot, state what it changes to if rain, heat, wind, closure, heavy crowd, or low stamina happens.
  - Prefer specific indoor alternatives: museums, galleries, malls, bookshops, cafes, indoor markets, performances, spas, hotel rest, parent-child indoor venues, and local workshops.
- Checklist:
  - Do not make it only a photo checklist.
  - Adapt to destination and trip type: passport, visa, entry policy, local SIM/eSIM, adapter, insurance, currency, student ID, elderly/child documents, driving license/international permit, rental-car documents, medicines, rain/heat/cold gear, highland/snow/desert/island/outdoor gear, museum/show/theme-park booking proof, chargers, power bank, storage, camera gear.
  - Output by time node: 7 days before, 3 days before, 1 day before, every morning, every night back at hotel, before return.
- Lodging base:
  - Put detailed lodging-base reasoning inside each daily arrangement, especially whether to stay, change hotels, return safely at night, park, do laundry, access hospitals/pharmacies, and depart easily the next day.
  - Homepage may show only a short lodging summary. Do not make homepage lodging base a dominant standalone block.

## Photo, Outfit, And Content Rules

- Put the classic photo check-in guide in the homepage overview and repeat relevant spot-level cards in each daily page.
- Default to phone-first shooting when the user does not specify equipment.
- Still recommend individualized equipment per spot when it clearly helps: tripod for night/selfie, gimbal/Pocket for walking video, action camera for movement/water/snow, drone only when legal and safe, mirrorless/telephoto/wide-angle for advanced users.
- Every day should include 1-3 must-shoot frames, one family/group frame when relevant, one short-video idea when useful, outfit/prop notes, device notes, weather/crowd fallback, and AI/social output role.
- Do not sacrifice normal travel experience for photo output. Mark places that are not worth extra detours only for photos.

## Avoid-Pit And Spending Rules

Include:

- Popular spots that may not fit this traveler.
- Image-beautiful places with ordinary actual experience.
- Queues, inflated prices, hidden consumption, shopping stops, and package traps.
- Restaurants, travel photography, charter, rental, guide, tickets, or tours that may not be worth it.
- Money worth spending and money to avoid spending.
- Hotel selection rules that reduce friction.
- How to avoid traffic, parking, and platform-promotion bias.
- For charter and travel photography: verify vehicle, seats, oil/toll/parking, driver meals, overtime, route changes, insurance, photographer style, shooting time, raw files, retouch count, makeup, clothing, drone, add-on fees, refund/weather policy, and copyright/use rights.

## Post-Trip Summary

When useful, include a post-trip asset plan:

- Route track summary, representative photo per day, Moments/Xiaohongshu/family-group copy direction, parent-child growth record, parents album, couple/friends copy, culture summary, photography shot list and retouch plan, route map, annual travel report, city check-in image, nine-grid, short-video script, travel bill, and avoid-pit review.
