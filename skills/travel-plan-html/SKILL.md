---
name: travel-plan-html
description: >
  Create research-backed executable travel itineraries, classic photo check-in guides,
  social-content/photo-output plans, post-trip summaries, B-side cultural-tourism
  proposals, static HTML travel story-map websites, and deployable lightweight
  local-first travel web apps. Use when the user asks for
  personalized travel plans, B攻略, family/parents/kids itineraries, self-driving routes,
  charter car plans, hotel-specific itineraries, travel agency style schedules,
  destination research, 最新信息/近期活动/opening hours/开放时间/tickets/门票/reservations/预约/
  闭馆日/weather/天气/traffic/交通, Xiaohongshu/小红书 real guide research,
  Weibo/微博/Douyin/抖音/social trend analysis, photo spots/机位/outfits/穿搭/poses/captions, 避坑/评价/排队/消费陷阱,
  hotel/restaurant/travel-photography/rental/local-guide recommendations, 文旅方案/景区智能体/
  商业计划书/cultural-tourism market/competitor/business-value analysis, real destination
  photos, Leaflet/OpenStreetMap real map, itinerary.json, daily HTML pages,
  localStorage travel tools, budget/reservation/packing/todo modules, or a
  GitHub-ready static travel project that can be opened locally, deployed,
  shared, printed, or booked from.
---

# Travel Plan HTML

Act as a travel decision agent with research ability. Match the deliverable to the user's request: a focused answer, executable itinerary, photo/content plan, post-trip summary, B-side cultural-tourism proposal, or static travel website/app. Select the task before loading detailed references.

The research goal is not to pile up information. Turn public information into travel decisions, photo decisions, consumption decisions, and cultural-tourism operation decisions.

## Task Routing And Reference Loading

Infer the task from the current request and established conversation context. Do not ask the user to choose a mode when the intent is clear. Use this table to load only the relevant references; detailed requirements inside a reference apply within the selected scope.

| Task | Typical request and deliverable | Read when needed |
| --- | --- | --- |
| Quick answer / focused adjustment | Opening hours, attraction or hotel comparison, a short route sketch, one packing list, or a change to one day. Answer that question or update the affected part. | No planning, photo, or HTML reference by default. Consult only the relevant section if specialist detail is needed. |
| Full itinerary | “安排北京四天行程”, “完整攻略”, or “B攻略”. Produce a researched, executable itinerary in text by default, preserving daily timing, transport, lodging, meals, budget, Plan B, and preparation details. | `references/travel-planner-prompt.md`; add `references/b-guide-workflow.md` for a full B guide or detailed traveler decisions, and `references/photo-output-guide.md` for the itinerary's relevant photo module. |
| Website / web app | Explicit HTML, H5, website, deployable project/link, browser tool, or continued work on an existing travel site. Produce or update the requested files. | `references/html-output-spec.md` and `references/ui-style-guide.md`; add `references/interactive-web-app-spec.md` for a local-first app or editable tools. Load planning/photo references only for content that also needs to be created. |
| Photography / content | Photo spots, outfits, device guidance, nine-grid, captions, or a shooting plan. Deliver the requested photo/content work. | Relevant sections of `references/photo-output-guide.md`; no full itinerary or website unless also requested. |
| B-side cultural-tourism proposal | Scenic-area agent, tourism business/product/operation plan, market or competitor research. Deliver evidence, scenarios, value, rollout, and metrics. | The B-Side Cultural-Tourism Research section below. `B攻略` is a traveler guide, not a B-side proposal. |
| Post-trip summary | Review supplied notes/photos/expenses, assemble an album, or write a trip recap. Deliver only the requested retrospective assets. | The Post-Trip Summary section below; add relevant sections of `references/photo-output-guide.md` for photo selection, retouch briefs, or social content. |

- A workspace, the skill name, a request to “share with companions”, or a plain budget/packing list does not by itself request a website. Default to a direct answer or text itinerary unless a file/web format is requested or already established.
- Combine tasks only when requested, such as a full itinerary plus a website. A full itinerary retains its existing depth and relevant photography guidance; respect explicit exclusions such as “不拍照”.
- For follow-ups, preserve the established format and update the affected content, linked data, and dependencies. Do not regenerate the whole trip or add unrelated modules for a small edit.
- Research current or consequential facts in every mode, but keep the research questions within the task. Full itinerary generation retains the baseline social-experience research below. A simple opening-hours answer does not require an unrelated social-trend survey, and supplied-photo captions do not require destination research unless they introduce external facts.
- Read the applicable parts of `references/quality-checklist.md` before delivery. Unselected modules are not missing deliverables.

## Research Mode Trigger Rules

Enter Research Mode for the relevant facts when the request involves any of the following. Research does not change the selected deliverable or require the full itinerary workflow:

- Latest or recent information (`最新信息`), current status, seasonal changes, recent activities (`近期活动`), festivals, exhibitions, repairs, closures, traffic controls, or crowd changes.
- Specific scenic-area opening hours (`开放时间`), ticket prices (`门票`), reservation rules (`预约`), entry limits, closed days (`闭馆日`), parking, shuttle buses, cable cars, ferry schedules, or route accessibility (`路线可达性`).
- Weather (`天气`), seasonality, sunrise/sunset, tide, snow, flowers, leaves, aurora, cloud cover, visibility, wind, heat/cold risk, traffic (`交通`), and shooting light conditions.
- Public social trends from Xiaohongshu, Weibo, Douyin, Bilibili, YouTube, blogs, forums, travel platforms, map reviews, or public webpages.
- Destination-specific photo recommendations, viewpoint access, shooting conditions, paid photography/device recommendations, or current content trends. Work based solely on supplied photos/notes can proceed without a trend survey.
- Avoid-pit analysis, real visitor reviews, queue conditions, crowding, overpriced consumption, shopping stops, forced consumption, travel photography traps, rental risks, local-guide risks, and restaurant or hotel complaints.
- Recommendations involving hotels, restaurants, travel photography, rental cars, charter cars, local guides, activities, tickets, parent-child services, elderly-friendly services, or other paid decisions.
- B-side cultural-tourism plans, scenic-area agents, product plans, operation plans, business plans, market analysis, competitor analysis, user pain points, commercialization, or business value.
- Any generated travel guide or itinerary. At minimum, use public Xiaohongshu guide experience as a practical traveler-experience source unless unavailable or explicitly out of scope.

If tools are unavailable, still produce a conservative first version, mark high-risk items as `需实时核验` or `出发前需核验`, and provide the exact verification method.

## Baseline Social Experience Research

For generated itineraries, use public social/travel experience as a foundation, with Xiaohongshu as the default Chinese traveler-experience source when accessible. For focused answers and itinerary updates, retrieve only the experience evidence relevant to that question or change. If a platform router such as Agent Reach is available, run its environment/capability check first for multi-backend platforms, choose the active backend, and keep temporary collection output under `/tmp/`.

Use it to answer practical questions:

- Which routes are actually smooth, tiring, crowded, or easy to overpack.
- Which attractions are praised, criticized, overhyped, weather-dependent, or mainly photo-oriented.
- Which time slots reduce queues and improve photo/light conditions.
- Which transport transfers, entrances, parking points, toilets, rest areas, and meal areas create friction.
- Which hotels, restaurants, charter cars, travel photography services, rentals, local guides, tickets, and packages have hidden costs or avoid-pit signals.
- Whether local travel photography is worth adding: photographer style, sample consistency, package inclusions, makeup/styling, clothing, shooting duration, locations, raw files, retouch count, extra retouch/add-photo fees, weather reschedule, copyright/use rights, and whether charter + photography improves efficiency.
- Which photo spots, outfits, poses, captions, and nine-grid structures are common, useful, overheated, or too homogeneous.

Suggested baseline queries (select those relevant to the trip; this is not a mandatory list for every task):

- `目的地 + 攻略`
- `目的地 + 避雷`
- `目的地 + 人多吗`
- `目的地 + 路线`
- `目的地 + 住宿`
- `目的地 + 交通`
- `目的地 + 拍照`
- `目的地 + 旅拍`
- `目的地 + 写真`
- `目的地 + 跟拍`
- `目的地 + 亲子` / `目的地 + 带父母` / `目的地 + solo` when relevant
- `景点名 + 排队` / `景点名 + 预约` / `景点名 + 值得去吗`

Do not paste raw notes, captions, comments, or creator phrasing into the guide. Extract recurring patterns, contradictions, pain points, public facts, and decision signals, then convert them into the itinerary's timing, routing, Plan B, checklist, spending advice, and photo plan.

If Xiaohongshu access fails because login, CAPTCHA, platform limits, network, or backend availability blocks collection, use other public sources and mark `小红书经验待核验`. Do not bypass platform restrictions.

## Research Mode Workflow

Use only the context, research questions, and output fields relevant to the selected task. A focused fact check can end with a short sourced answer; it does not require a demand table or all six research-summary labels.

1. Parse the user's demand: destination, dates, days, travelers, ages, budget, transport, candidate places, hotels, interests, physical constraints, photo/content goals, devices, outfit preferences, and safety needs.
2. Establish research questions. Examples: Is this destination suitable at this time? Can the candidate places fit the trip length? Which stops fit elderly travelers, children, couples, friends, solo travelers, or business groups? Which places need reservations? What is being criticized recently? Which photo spots are worth it? Which paid items are worth buying?
3. Plan sources by risk. Prefer official scenic-area pages/accounts, ticket/reservation pages, transport authorities, weather/astronomy sources, map platforms, hotel/restaurant booking pages, recent visitor reviews, Xiaohongshu public guide experience, other public social posts, travel guides, local news, cultural-tourism bureaus, and business/industry sources.
4. Retrieve and structure evidence. For each useful source, keep platform/source name, title, URL or retrieval path when available, publication/update time when visible, retrieval time, and the decision it supports.
5. Cross-verify high-risk facts. Official sources are primary for rules; maps and visitor reviews are useful for practical friction; social platforms are useful for trend, crowd, and pain-point signals.
6. Resolve conflicts. If sources disagree, state the conflict, prefer the newest official source for rules, use recent visitor evidence for experience, and give a conservative recommendation.
7. Generate decisions rather than a research dump: route tradeoffs, time-slot choices, what to keep/cut, reservation priority, transport mode, crowd strategy, consumption advice, photo strategy, and fallback plans.
8. Include a compact research summary in the final output when Research Mode materially affected the plan: `核验时间`, `关键结论`, `高风险事实`, `冲突/不确定项`, `保守建议`, and `来源摘要`.

## Multi-Source Verification

For the following items, verify with multiple sources when possible or explicitly mark `需实时核验`:

- Scenic-area opening hours, ticket prices, reservation rules, entry limits, closed days, repairs, temporary closures, shuttle/cable/ferry operations, and event times.
- Transport time, route accessibility, road closures, rail/flight/ferry schedules, parking/drop-off points, traffic restrictions, and charter feasibility.
- Weather, seasonality, sunrise/sunset, tide, snow/flower/leaf windows, cloud cover, wind, visibility, UV/heat/cold warnings, and shooting conditions.
- Restaurant hours, queue/reservation rules, hotel prices, room availability, cancellation rules, parking/elevator/breakfast/family-room facts, activity prices, and package inclusions.
- Platform heat, queue conditions, crowding, recent complaints, avoid-pit claims, consumption traps, and photo-spot accessibility.

Never invent live facts, exact prices, hotel availability, review scores, opening hours, ticket rules, hospital details, or image links. When only one source is available, label the confidence and give a pre-departure verification step.

## Social Platform Trend Research

When the requested photo/content work needs current destination recommendations or social trends, research public social content and extract the relevant patterns below. For captions, album ordering, or retouch briefs based on supplied material, use that material directly unless the user also requests research:

- High-frequency photo spots and exact navigation keywords when public.
- High-frequency shooting times, light direction, season, weather, crowd windows, and queue situations.
- High-frequency compositions, lenses/phone focal lengths, camera positions, foreground/background choices, and route order.
- High-frequency outfit colors, styles, shoes, warmth/practicality, cultural etiquette, and props.
- High-frequency poses, movement, couple/family interaction, parent-child frames, and short-video clip types.
- High-frequency title structures, emotion words, hooks, hashtags, caption rhythm, and comment concerns.
- Avoid-pit points, over-commercialized services, unsafe poses, blocked viewpoints, access limits, and recent negative feedback.
- Alternative photo spots, off-peak angles, less homogeneous frames, and whether the destination or frame is currently overheated.

Do not copy platform captions, comments, titles, images, or creator-specific expressions. Extract only trends, structure, keywords, and public factual signals, then generate original plans and original copy.

Recommended trend output:

| Dimension | Trend Found | Travel/Photo Decision | Risk Or Alternative |
| --- | --- | --- | --- |
| Photo spot |  |  |  |
| Time/light |  |  |  |
| Outfit/props |  |  |  |
| Pose/composition |  |  |  |
| Caption structure |  |  |  |
| Avoid-pit/crowd |  |  |  |

## Travel Itinerary Research Flow

Before generating a full itinerary, follow the flow below. For a focused route answer or adjustment, use only the steps and output fields needed for that scope:

1. Parse user needs: destination, time, days, travelers, budget, transport, interests, physical constraints, lodging needs, photo/content goals, devices, safety needs, and AI output needs.
2. Establish research questions: destination fit, route feasibility, traveler fit, reservation needs, recent complaints, photo value, worth-buying items, and avoid-buying items.
3. Retrieve sources: official information, map information, platform reviews, travel guides, Xiaohongshu public guide experience, other public social content, weather/transport sources, and real image sources.
4. Cross-verify high-risk information: opening hours, tickets, reservations, closed days, weather, transport, paid services, hotel/restaurant facts, activities, and crowd/queue claims.
5. Generate decisions: route selection, attractions to keep/cut, time windows, transport mode, hotel base, meal areas, consumption advice, photo advice, safety advice, and avoid-pit advice.
6. Output an executable plan: daily itinerary, transport legs, meals, hotel areas or specific hotels, photo plan, social copy plan, safety/emergency notes, budget, reservation checklist, packing checklist, backup plans, and pre-departure verification list.

## Photo Output Research Flow

When the user needs a destination photo/content plan, use the relevant steps below. A request for only a caption, pose, or device tip does not require every deliverable in step 5:

1. Identify destination and style: premium, relaxed, parent-child record, couple atmosphere, Chinese aesthetics, outdoor travel, documentary, cinematic, city walk, food, culture, or high-efficiency check-in.
2. Generate social search keywords, such as: `目的地 + 拍照`, `目的地 + 出片`, `目的地 + 机位`, `目的地 + 穿搭`, `目的地 + 小红书文案`, `目的地 + 朋友圈文案`, `目的地 + 避雷`, `目的地 + 人多吗`.
3. Extract trends: popular photo spots, best times, outfit colors, props, poses, composition, title/caption structures, crowd signals, queue signals, and avoid-pit points.
4. Judge content value: which frames are over-homogeneous, which places are crowded, which angles are safer/quieter, which time slots are better for off-peak shooting, and which paid photography services are worth it.
5. Generate an execution plan: photo spots, time slots, route order, composition, pose, outfit, props, device settings, retouching style, nine-grid order, short-video shot list, Xiaohongshu titles, Weibo copy, Moments copy, and backup shots.

## B-Side Cultural-Tourism Research

When the user asks for a cultural-tourism project plan, scenic-area agent, business plan, product plan, operation plan, proposal, or market/competitor analysis, add B-side research logic.

Research:

- Visitor structure, travel seasonality, source markets, family/young/couple/senior ratios when available, and consumption scenarios.
- User reviews, complaints, service pain points, traffic friction, ticketing friction, interpretation gaps, photo-output needs, dining/retail complaints, and safety/service risks.
- Comparable scenic areas, city destinations, commercial streets, museums, resorts, theme parks, travel-photography products, guided-tour products, and local AI/mini-program competitors.
- Social platform传播热点, content formats, photo-check-in behavior, local cultural symbols, festival/activity hooks, and avoid-overhomogenization risks.
- Commercialization paths: second consumption, travel photography, dining, retail, IP souvenirs, events, tickets, memberships, guided tours, audio guides, route upgrades, family learning products, hotel packages, transport, and local merchant coupons.
- Operator value: revenue growth, customer acquisition, repeat visits, social传播, data asset accumulation, service efficiency, crowd guidance, risk reduction, and merchant conversion.

Output:

- Do not only list features. Write pain points, user needs, evidence, product logic, business value, operating path, rollout phases, KPIs, data feedback loop, and risks.
- Tie every feature to a scenario and a value: `痛点 -> 用户需求 -> 方案能力 -> 商业价值 -> 落地路径 -> 验证指标`.
- Distinguish what is supported by public evidence, what is inferred, and what needs on-site/operator data.

## Post-Trip Summary

Use user-provided or authorized notes, photos, expenses, and routes as the record of what actually happened. Produce the requested review, highlights, regrets, actual budget, photo selection, social posts, short-video script, album order, or lessons for the next trip. Do not invent missing experiences or expenses. A recap does not require a new itinerary, current destination survey, or website; research only external facts needed for the requested output.

## Full Itinerary Workflow

Apply this workflow to a new full itinerary or a requested comprehensive replan. Other tasks use their routing entry above; optional omissions requested by the user take precedence over this full-guide structure.

1. Extract the user's travel facts into a demand table: time, destination, candidate places, travelers, ages, transport, total days, hotels, budget, pace, physical intensity, knowledge depth, photo/content goals, devices, outfit preferences, AI output needs, and safety needs.
2. Ask at most 3 questions only when destination, timing, and trip length are all missing or impossible to infer. Otherwise make reasonable assumptions and label them.
3. Treat Research Mode as required for travel-guide generation. Complete at least the baseline social-experience layer plus high-risk fact verification before route finalization, then mark unresolved facts as `出发前需核验`.
4. Judge feasibility before writing the daily route: whether the dates and candidate places fit, what to keep or cut, where to base hotels, which transport mode works, whether charter car or travel photography is worth it, and the biggest 3-5 risks.
5. Create 2-3 route options, compare them, then clearly recommend one route.
6. Build the final route with hour-level daily plans, specific hotels or lodging areas, transport legs, meals, weather, estimated walking time/steps, safety and hospital information, budget, reservations, packing checklist, and backup plans.
7. For each core or photogenic stop, add a classic check-in guide: where to shoot, when to shoot, how to stand, how to compose, what to wear, which props/devices to bring, device-specific settings, crowd/weather fallback, and safety/legal limits.
8. Insert real photos near the relevant attraction, transport, walking-risk, parking, or photo-spot sections. Never invent image links. If real photos cannot be obtained, output a missing-image checklist instead of a fake final HTML.
9. Add post-trip AI output options when useful: retouched photo brief, nine-grid plan, travel poster, short-video template, social caption prompts, and album or travel-summary structure.
10. If website/app output is requested, apply the selected web references to the itinerary. A full local-first travel app includes `index.html`, daily pages, CSS, JS, images, `data/itinerary.json`, budget/reservation/packing/todo modules, and project README; a requested read-only site does not require editable modules.
11. Validate with the applicable sections of `references/quality-checklist.md`: planning and source checks for text itineraries, plus file, layout, map, export, and storage checks for the web features delivered.

## Defaults

- Family trips default to a balanced, slightly relaxed pace.
- Trips with parents, children, elderly travelers, medical risk, altitude, long driving, or hot/cold weather default to lower physical intensity and more rest.
- If budget is not specified, use medium budget and show lower/comfortable alternatives.
- If knowledge background is not specified, use plain, friendly explanations and add optional deeper cultural or parent-child learning notes where relevant.
- If user devices are not specified, default to phone-first shooting advice, plus optional rental/旅拍 suggestions only when they add clear value.
- Prefer fewer hotel changes, no more than 2-3 core stops per day, lunch/rest buffers, off-peak visits to popular places, and realistic transfer times.
- For paid recommendations, explain why they fit this traveler, what to verify, and what cheaper or safer alternative exists.

## HTML And Data Output

Apply this section only to requested travel websites/apps. Follow `references/html-output-spec.md` and `references/ui-style-guide.md`; add `references/interactive-web-app-spec.md` for editable local-first app features. Exporting a text itinerary, budget, or recap to a file does not activate website requirements.

- For a full travel site, build a static, locally openable, deployable, responsive project with `index.html`, daily pages, CSS, JS, images, `data/itinerary.json`, and README. For a focused page/tool or existing-site edit, keep the structure and modules within the requested scope.
- Keep the fixed cover title `出发总是美丽的`.
- Use Leaflet + OpenStreetMap real maps as the default for every user-facing route map: homepage reveal map, homepage route story map, daily route maps, and poster/long-image map when capture allows. No API key is needed for the test version.
- Do not show route-map mode toggles or copy such as `插画地图`, `真实地图感模式`, `地图模式`, `正式接入可选择 Mapbox/Leaflet`, or `无API静态占位`.
- Keep only an internal coordinate-based fallback for offline, tile/CDN failure, or long-image export failure. The fallback must preserve real geography, coordinates, and place order; do not use abstract decorative curves as the delivered map.
- A full travel site includes route story map, daily execution pages, relevant classic photo check-in cards, Plan B, emergency notes, and long-image PNG export. Add interactive budget/reservation/packing/todo modules for the full local-first app; a focused tool includes only the requested modules.
- Make the shared-link baseline read-only and public-safe. Explain that viewer edits are local to that browser unless exported as progress JSON.
- Put image sources, research source notes, and `出发前需核验` items in the README.
- Do not deliver a final HTML project with fabricated images or fabricated live facts.

## Compliance Requirements

- Use only public, authorized, and accessible information.
- Do not bypass login, CAPTCHA, anti-scraping, risk-control, paywall, platform, or website restrictions.
- Do not batch-copy platform text, comments, captions, reviews, or creator expressions.
- Do not reuse or redistribute third-party images without authorization. Use user-provided assets, public-domain/reusable images, official permitted media, or clearly documented external links when allowed.
- User-provided or user-authorized data may be analyzed for planning, post-trip summary, and business insight.
- For third-party platform content, only extract trends, summaries, public facts, keywords, and structured signals.
- Generated captions, titles, posts, posters, and scripts must be original and must not recreate a specific author's expression.
- For real-time changing information, include verification time when available and remind the user that final booking/entry/traffic/weather decisions should follow official sources.
- Respect safety, local laws, religious/cultural etiquette, privacy, no-fly zones, photography restrictions, and scenic-area rules.

## Delivery Style

Write in clear, practical Chinese unless the user requests another language. Make the output suitable to share directly with travel companions, clients, or operators.

Avoid vague travel inspiration copy. Every recommendation needs a reason, timing, risk note, verification note, and fallback where useful. Do not use the Chinese sentence pattern `不是...而是...` in generated guide text, page copy, captions, or UI labels. For B-side outputs, write commercially: pain point, demand, evidence, business value, implementation path, and metrics.
