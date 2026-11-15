# Quality Checklist

Read the applicable checks before delivery. Task selection in `SKILL.md` determines the deliverable; this checklist must not add unrequested modules.

## Scope Of Checks

| Selected task | Apply |
| --- | --- |
| Quick answer / focused adjustment | Answer completeness, evidence for relevant current facts, uncertainty, and relevant prohibitions. For an existing artifact, check affected content, links, and data. No full itinerary, photo, or HTML checklist by default. |
| Full itinerary | Full Itinerary Checks; relevant Photo Output and Image Checks. HTML Project Checks only if web output is also requested. |
| Website / web app | HTML Project Checks for the requested pages/features; interactive checks only for selected app modules. Planning checks apply when also generating or replanning the itinerary. |
| Photography / content | Relevant Photo Output and Image Checks, plus current-fact and originality checks. No unrelated itinerary or web requirements. |
| B-side cultural-tourism proposal | Evidence versus inference, pain points, scenarios, commercial value, rollout, metrics, and risks from the B-side workflow. |
| Post-trip summary | Faithfulness to supplied/authorized trip records, no invented experiences or costs, and requested retrospective deliverables. Photo/web checks only when those outputs are requested. |

Respect user exclusions, such as no photography. Treat checks for unselected modules as not applicable; do not add those modules to make the checklist complete.

## Full Itinerary Checks

| Check | Done |
| --- | --- |
| First executable version is produced directly. |  |
| No long questionnaire appears before the first version. |  |
| If assumptions are needed, they are labeled clearly without blocking direct generation. |  |
| Generated Chinese guide text, page copy, captions, and UI labels do not use the pattern `不是...而是...`. |  |
| Xiaohongshu public guide experience is used as a baseline source for every generated travel guide when accessible. |  |
| Social experience signals are naturally integrated into route timing, route cuts, queue/crowd strategy, Plan B, spending advice, avoid-pit notes, checklist, photo decisions, and travel-photography decisions. |  |
| If Xiaohongshu access is blocked or unavailable, the guide marks `小红书经验待核验` and uses other public sources conservatively. |  |
| The guide does not copy Xiaohongshu note text, comments, titles, screenshots, or creator expressions. |  |
| Destination, timing, travelers, transport, hotel, budget, pace, photo, and safety needs are parsed or reasonably assumed. |  |
| Photo/content goals, user devices, outfit/props, paid travel photography willingness, and AI output needs are parsed or reasonably assumed. |  |
| Trip length and route feasibility are judged. |  |
| 2-3 route options are compared and one is clearly recommended. |  |
| Final route overview table exists. |  |
| Every day has an hour-level schedule. |  |
| Every day includes weather, clothing advice, rain alternative, walking time, steps, and intensity. |  |
| Every day includes transport legs, costs or cost ranges, and realistic buffers. |  |
| Specific hotels are recommended or existing hotels are incorporated. |  |
| Hotel facts that depend on live availability are marked `出发前需核验`. |  |
| Meals include areas/types, suitability, budget, and backups. |  |
| Safety, hospital, pharmacy, and emergency notes are included. |  |
| Elderly and child friendliness are evaluated when relevant. |  |
| Charter car type is clearly judged when relevant. |  |
| Budget summary exists for low/medium/comfortable levels or user-specific budget levels. |  |
| Reservation and pre-departure verification checklist exists. |  |
| Packing checklist is adapted to destination, season, weather, and travelers. |  |
| Checklist is not only a photo checklist; it covers destination-specific documents, transport, lodging, weather, medicine, device, travel-photo, and special-scenario needs. |  |
| Overseas checklist includes passport, visa/entry policy, local SIM/eSIM, adapter, insurance, currency, and embassy/emergency info when relevant. |  |
| Packing checklist includes photo devices, batteries, memory/storage, chargers, tripod/gimbal/drone rules, outfit, and props where relevant. |  |
| Adjustment options cover weather, stamina, budget, crowds, driving fatigue, photography, culture, and relaxed pace. |  |

## Photo Output Checks

| Check | Done |
| --- | --- |
| Photography is treated as a core itinerary module, not only a note under attractions. |  |
| Homepage includes a classic photo check-in overview, and daily pages repeat spot-specific photo cards where relevant. |  |
| Every photogenic core stop has a classic check-in card: exact spot, best time, light/weather, crowd strategy, pose/action, composition, outfit, props, device plan, safety/permission, backup, and AI output role. |  |
| Phone-only users receive phone-first shot, lens/mode, composition, and practical setting advice. |  |
| Optional gear is recommended by spot only when useful: tripod, gimbal/Pocket, action camera, drone, mirrorless/DSLR, lens choice, or fill light. |  |
| Drone, Pocket/gimbal, Action camera, or mirrorless/DSLR advice appears only when relevant and includes safety, legality, weather, battery, and permit constraints. |  |
| Special photo conditions are verified or marked `出发前需核验`: sunrise/sunset, cloud cover, moon phase, aurora forecast, no-fly zones, viewpoint access, tide/water reflection, crowd control. |  |
| Outfit and prop advice is scene-specific, culturally respectful, walkable, weather-aware, and safe. |  |
| Paid travel photography, equipment rental, makeup/styling, and charter + photography are judged with cost risks and alternatives when photo goals are high. |  |
| Travel-photography advice includes style fit, package contents, raw files, retouch count, add-photo fees, makeup/styling, clothing, weather rescheduling, copyright/use rights, and phone-first alternatives. |  |
| AI output plan exists when useful: retouched photo brief, nine-grid, poster, short-video template, or social caption plan. |  |
| The itinerary does not claim AI retouching is complete unless image-editing tools were actually used. |  |

## Image Checks

| Check | Done |
| --- | --- |
| Every core attraction has at least 1 real image or appears in the missing-image checklist. |  |
| Important/photo-risk/physical-risk/transport-complex attractions have the required extra images. |  |
| Images are inserted near the relevant attraction, transport, walking, parking, photo-tip, or weather section. |  |
| No fabricated image URL is used. |  |
| Each image has source, caption, alt text, content description, and bias/authenticity reminder. |  |
| If images cannot be obtained, final HTML is not falsely presented as complete. |  |

## HTML Project Checks

| Check | Done |
| --- | --- |
| `travel-plan/index.html` exists. |  |
| `travel-plan/days/dayXX.html` exists for every day. |  |
| `travel-plan/css/style.css` exists. |  |
| `travel-plan/js/main.js` exists, even if minimal. |  |
| `travel-plan/data/itinerary.json` exists and parses as JSON. |  |
| `itinerary.json` includes `tripId`, `app`, `budgetItems`, `reservations`, `packingItems`, and `todos` when producing the local-first web app. |  |
| Budget, reservations, packing, and todo items use stable IDs. |  |
| `travel-plan/assets/images/dayXX/` folders exist for saved local images or image placeholders/checklists are clearly documented. |  |
| `travel-plan/README.md` exists. |  |
| HTML pages can open locally without a build step. |  |
| The project uses relative paths and is deployable as static files under a subpath. |  |
| First screen is a bright destination cover with fixed title `出发总是美丽的`, not `专属 Travel Plan`. |  |
| Cover includes subtitle, emotional line, and 3-5 glass chips. |  |
| Swipe paper/scroll reveal exists, does not expose the map before opening, and does not duplicate the full prompt. |  |
| Route story map module includes Leaflet + OpenStreetMap real map mode by default. |  |
| Homepage route story map directly shows a zoomable real map and does not show labels such as `插画地图`, `真实地图感模式`, or `正式接入可选择 Mapbox/Leaflet`. |  |
| Leaflet assets load when online, OpenStreetMap attribution is visible, and map container has stable dimensions on mobile and desktop. |  |
| Real map markers include available scenic spot, hotel, meal, photo, transport, parking/drop-off, hospital/pharmacy, and emergency coordinates. |  |
| Nodes without coordinates are marked `坐标需核验` or `coordinateStatus: needs_verification`, not silently omitted from the plan. |  |
| Route polylines are labeled as planning lines unless a real routing API is configured. |  |
| Fallback route map remains available for offline/CDN-failure fallback and long-image export, and it is coordinate-based rather than an abstract decorative curve. |  |
| Route story map module includes day nodes, route curve, labels, hotel/photo/meal/emergency markers, and judgment summary. |  |
| Long-image export button and `#poster` export area exist. |  |
| Homepage links to every daily page. |  |
| Homepage includes a photo output overview when the trip has photo value. |  |
| Homepage includes a practical `旅行准备工作台` or equivalent local-first app dashboard. |  |
| The dashboard includes budget, reservations, packing, and todo modules. |  |
| Budget module shows planned/actual totals, category breakdown, editable items, paid toggles, and reset behavior. |  |
| Reservation module shows status chips, unresolved verification items, booking links or file notes, and does not invent private confirmation data. |  |
| Packing module groups items by category, supports checkboxes, quantities/owners where useful, and shows progress. |  |
| Todo module groups tasks by phase, supports done/add/edit/delete, and highlights high-priority unresolved tasks. |  |
| `js/main.js` loads initial app data, merges saved local state by stable ID, persists edits to `localStorage`, and keeps the guide readable if storage fails. |  |
| Export local progress JSON, import local progress JSON, and reset local progress controls exist. |  |
| README explains that shared-link edits are per-browser localStorage and do not sync across travelers. |  |
| README includes static deployment notes for the requested host or common static hosts. |  |
| Daily previous/next/back-home links work. |  |
| Daily page main section is titled `DAY{n} 行程`, `每日路线概览`, or similar human travel-agent wording; it does not use `每日完整执行脚本`. |  |
| Daily page uses left-side time-slot cards and a right-side daily Leaflet + OpenStreetMap real map with labeled spots, meals, rest points, photo spots, and emergency points. |  |
| Time-slot cards include expandable/scannable notes with images, attraction details, indoor/outdoor status, transport, ticket/opening/reservation notes, queue risk, toilets, rest points, and cut-if-delayed advice. |  |
| Daily pages include photo check-in cards and `photoPlan` data where relevant. |  |
| Detailed lodging-base reasoning appears inside each daily page, while the homepage only has a short lodging summary. |  |
| Plan B is a separate section organized by day and affected attraction, with specific indoor or lower-risk alternatives. |  |
| Checklist is a separate section organized by time node: 7 days before, 3 days before, 1 day before, each morning, each night, before return. |  |
| Mobile layout has no overlapping text or broken tables. |  |
| Print CSS exists. |  |
| Image paths render correctly. |  |
| Core content remains readable if optional external resources fail. |  |

## Prohibitions

Apply content and feature prohibitions only where the corresponding task/module is in scope. Factual accuracy, originality, privacy, and safety apply to every task.

- For a full itinerary, do not deliver only a list of attractions. A requested attraction shortlist may stay a shortlist.
- For executable plans, do not deliver abstract advice without execution details.
- Do not use the Chinese sentence pattern `不是...而是...`.
- Do not copy destination-specific content from a user's example itinerary.
- Do not invent current facts, hotel availability, review scores, prices, opening hours, ticket rules, hospital details, or image links.
- Do not place photos only at the end.
- Do not ignore weather, walking steps, age/stamina, medical risk, or budget.
- Do not treat shooting guidance as a vague "good for photos" note.
- Do not recommend illegal drone use, unsafe poses, culturally inappropriate clothing/props, or risky night/water/cliff shooting.
- Do not promise AI retouching, posters, or videos unless the needed tools and user photos are available.
- Do not say "recommend charter" without judging type, date, cost risks, and alternatives.
- Do not use complex dependencies that prevent local opening.
- Do not require a backend, login, database, or build step for the default local-first app.
- Do not claim shared-link edits sync across people or devices unless a backend is actually implemented.
- Do not expose sensitive booking confirmation numbers, documents, passport details, or private traveler data in public files unless the user explicitly supplied and approved them.
- Do not generate a black tech hero, default Bootstrap style, booking-app flow, or Markdown-like document page.
- Do not place the route preview in the lower-right corner or show it before the paper reveal.
- Do not omit long-image export when generating the H5.
- Do not give the user a plan that still needs heavy second-pass organizing.
- Do not show homepage map-mode copy such as `插画地图`, `真实地图感模式`, or `正式接入可选择 Mapbox/Leaflet`.
- Do not deliver user-facing route maps as abstract illustrated curves when a real map can be rendered.
- Do not use `每日完整执行脚本` as a visible section title.

## Final Response

For a focused answer, photo/content task, proposal, or recap, deliver the requested result with relevant source/uncertainty notes. Do not add an unrelated project completion report or next-step question.

When a requested web project is complete, summarize:

- Output folder and key files.
- Any facts marked `出发前需核验`.
- Any missing-image items, if applicable.
- What was verified locally.
- A short question asking what the user wants adjusted next.
