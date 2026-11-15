# HTML Output Specification

Use this reference when the Website / web app task in `SKILL.md` is selected: requested HTML, webpage, website, H5, static travel project, or continued work on an existing travel site. A workspace, a text-file export, or “share with companions” alone does not select this task. Also read `ui-style-guide.md`. Read `interactive-web-app-spec.md` only for requested local-first app/editable tool features; a deployable read-only page does not need editable modules.

The full structure below applies to a full travel website. For a focused page/tool or an existing-site edit, apply only the relevant requirements and preserve the requested scope. When converting an existing itinerary, preserve its approved content and uncertainty notes; do not start a full replan unless requested. A standalone long-image request uses the relevant export/style guidance without requiring a website.

## Folder Structure

Create a `travel-plan/` folder:

```text
travel-plan/
├── index.html
├── css/
│   └── style.css
├── js/
│   └── main.js
├── assets/
│   └── images/
│       ├── day01/
│       ├── day02/
│       └── ...
├── data/
│   └── itinerary.json
├── days/
│   ├── day01.html
│   ├── day02.html
│   └── ...
└── README.md
```

The site must be static, responsive, locally openable, deployable as ordinary static files, shareable, printable, exportable as a long image, and readable without a build step.

## Homepage Requirements

`index.html` must include:

- Full-screen destination cover with the fixed title `出发总是美丽的`.
- Trip subtitle, emotional line, and translucent trip chips.
- Centered paper/scroll swipe interaction that reveals a real-map route preview or a coordinate-based real-map preview.
- Route story map module with a zoomable Leaflet + OpenStreetMap real map by default, day nodes, route curve, hotel/photo/meal/emergency markers, and travel judgment summary.
- Do not show homepage microcopy such as `插画地图`, `真实地图感模式`, or `正式接入可选择 Mapbox/Leaflet`. The real map should appear as the actual route map, with fallback handled silently or through a brief error state only if loading fails.
- One-click `导出长图 PNG` control and a `#poster` export area.
- Trip title.
- Date range, total days, travelers, and transport mode.
- Recommended route overview.
- Daily card entry links.
- Short lodging summary only; detailed lodging-base reasoning belongs inside each daily page.
- Weather overview.
- Budget summary.
- Walking and intensity overview.
- Homepage classic photo check-in overview: best shoot days, must-shoot frames, outfits/props, phone-first device plan, spot-specific optional equipment, and AI/social deliverables.
- Independent Plan B section.
- Independent destination-specific checklist section.
- Interactive `旅行准备工作台` section with budget, reservations, packing, and todo modules when generating the default local-first web app.
- Reservation and real-time verification checklist.
- Emergency information.
- Links to daily pages.

## Daily Page Requirements

Each `days/dayXX.html` page must include:

- Date header and day badge.
- Weather, temperature, clothing, and rain backup.
- Daily lodging base: where to stay that night, why, whether to change hotels, night safety, parking/laundry/hospital/pharmacy/next-day departure logic.
- Route summary.
- `DAY{n} 行程` section: left side time-slot cards; right side a daily Leaflet + OpenStreetMap real map with labeled spots, meals, rest points, photo spots, parking/drop-off, and emergency points.
- Transport and charter/parking card.
- Attraction cards with real images, indoor/outdoor status, traveler fit, walking/stairs/slope/sun/crowd/toilet/parking risks, and rain value.
- Classic photo check-in cards with shot spot, time, pose, composition, outfit, props, phone-first settings, optional spot-specific equipment, and AI output role.
- Meals.
- Safety, hospital, pharmacy, and emergency information.
- Day-filtered budget items, reservations, packing reminders, and todos when the local-first app mode is enabled.
- Per-attraction backup plans for rain, heat/cold, wind, low stamina, crowds, closures, and delays.
- Previous/next navigation.
- Back-to-home link.

Use this visual logic: travel story map H5, date block, clean light header, clear time labels, left-side time-slot cards, right-side daily real map, attraction image/text blocks, transport distance, opening hours, suggested duration, addresses, photo cards, separated Plan B, separated checklist, and daily lodging-base reasoning.

## Daily Page Template

Each day page should include modules equivalent to:

```html
<header class="day-hero">
  <div class="date-badge">
    <span class="day-number">D1</span>
    <span class="date">具体日期</span>
  </div>
  <div class="day-summary">
    <h1>当日标题</h1>
    <p class="route">起点 -> 景点 -> 餐饮区 -> 酒店</p>
    <div class="meta-grid">
      <div>天气：多云 20-28℃</div>
      <div>住宿：酒店/区域</div>
      <div>交通：自驾/包车/公共交通</div>
      <div>步数：约 8000 步</div>
    </div>
  </div>
</header>

<section class="day-route-section">
  <h2>DAY1 行程</h2>
  <div class="day-route-layout">
    <div class="time-slot-list"></div>
    <aside class="daily-real-map">
      <div class="daily-map" data-day-map="1"></div>
    </aside>
  </div>
</section>

<section class="transport-section">
  <h2>交通与包车判断</h2>
</section>

<section class="spots-section">
  <h2>景点与活动</h2>
</section>

<section class="photo-section">
  <h2>经典出片打卡指南</h2>
</section>

<section class="food-section">
  <h2>餐饮建议</h2>
</section>

<section class="hotel-section">
  <h2>今日住宿 Base</h2>
</section>

<section class="safety-section">
  <h2>安全与应急</h2>
</section>

<section class="backup-section">
  <h2>Plan B｜天气与体力调整</h2>
</section>
```

## Visual Style

- Use the travel story map H5 style from `ui-style-guide.md`.
- Use a bright destination cover, literary title, paper/scroll interaction, zoomable Leaflet + OpenStreetMap real map on the homepage, daily Leaflet + OpenStreetMap real maps, and a magazine-like light visual system.
- Use cards, timeline, tables, and image grids.
- Keep colors fresh and readable; highlighted times and risks may use stronger colors but must not be harsh.
- Build mobile-first responsive pages for phone and desktop.
- Use CSS Grid/Flexbox; avoid complex frameworks.
- Make image ratios consistent with `object-fit: cover`.
- Put captions and sources below each image.
- Ensure the top of each daily page immediately shows date, weather, hotel, theme, and route.
- Do not create pure long text pages.
- Leaflet + OpenStreetMap is the default real-map test integration. External fonts, icon libraries, or map tiles may fail; core content and the fallback route map must remain readable offline.
- Every image must have `alt`.
- Tables must scroll horizontally or become cards on mobile.
- Add print styles for PDF/export.
- Add long-image export styles for `#poster`.
- Add highlight styles for core experiences, risks, cuttable items, and must-keep items.

## CSS Requirements

`css/style.css` must define:

- Global font, color, spacing, and max page width.
- Full-screen cover, warm overlay, literary title, subtitle, emotional line, and chips.
- Paper/scroll reveal card, swipe slider, route map SVG, animated route path, and route labels.
- Route story map module with Leaflet real map, stable map height/aspect ratio, marker popups, category legend, loading/failure state, and no visible map-mode toggle labels.
- Daily route layout with left-side time-slot cards and right-side Leaflet real map.
- Long-image poster export layout.
- Homepage overview cards.
- Day hero and date badge.
- Time-slot cards and expandable travel-handbook blocks.
- Transport cards.
- Attraction cards.
- Photo check-in cards, outfit/prop tags, device notes, and AI output cards.
- Image gallery and captions.
- Tables.
- Risk, warning, budget, and must-keep highlights.
- Mobile responsive behavior.
- Print styles.

## Leaflet Real Map Requirements

Use Leaflet + OpenStreetMap as the default real-map test integration:

- Add Leaflet CSS and JS from a public CDN in `index.html`; no API key is required.
- Include a visible map container such as `<div id="real-map"></div>` with a stable height on mobile and desktop.
- Initialize the map in `js/main.js` from `data/itinerary.json`.
- Use OpenStreetMap tiles with visible attribution. Do not hide or remove attribution.
- Add markers for scenic spots, hotel bases, restaurants/meal areas, photo spots, transport hubs, parking/drop-off points, hospitals, pharmacies, and emergency points when coordinates are available.
- Use category colors, icons, or marker classes, plus a compact legend.
- Each marker popup should include name, day, time window when known, role, short decision note, risk/verification note, and link/anchor to the related day section when possible.
- Draw route lines as simple Leaflet polylines between known coordinates. Label them as planning lines, not exact navigation routes, unless a routing API is explicitly configured.
- If a node lacks coordinates, include it in `routeMap.nodes` with `lat` and `lng` as `null`, show it in the text route and coordinate-fallback map list, and mark `coordinateStatus` as `needs_verification`.
- If Leaflet, CDN assets, or OSM tiles fail to load, display the fallback route map and a short message: `真实地图加载失败，已显示备用路线图`.
- Try to export the real map in long-image PNG first. If cross-origin tile export fails, use a coordinate-based fallback that preserves real geography and place order; do not use an abstract decorative route curve as the final exported map.

Use the same Leaflet pattern for each daily page:

- Add a stable container such as `<div class="daily-map" data-day-map="1"></div>` in every `days/dayXX.html`.
- Initialize daily maps from the same `routeMap.nodes` and `routeMap.lines`, filtered by day.
- Include daily scenic spots, hotel, meals, photo spots, transport hubs, parking/drop-off, hospital/pharmacy, emergency, and backup points when coordinates are available.
- Fit the map bounds to the day's available coordinates.
- If a day has missing coordinates, list those points next to the map as `坐标需核验` instead of silently dropping them.

Use this node shape in `routeMap.nodes`:

```json
{
  "id": "day01-kiyomizu",
  "name": "清水寺",
  "type": "attraction",
  "day": 1,
  "time": "09:00-11:00",
  "lat": 34.9949,
  "lng": 135.785,
  "coordinateStatus": "verified",
  "role": "核心景点 / 清晨人像",
  "decisionNote": "适合早到避开二年坂人流",
  "riskNote": "台阶较多，雨天防滑",
  "anchor": "day01-kiyomizu"
}
```

Allowed marker `type` values: `attraction`, `hotel`, `meal`, `photo`, `transport`, `parking`, `hospital`, `pharmacy`, `emergency`, `backup`, `other`.

Use this line shape in `routeMap.lines`:

```json
{
  "id": "day01-main-route",
  "day": 1,
  "type": "planning_polyline",
  "label": "D1 计划动线",
  "nodeIds": ["day01-hotel", "day01-kiyomizu", "day01-gion"],
  "note": "点位连线仅表示计划顺序，不等于真实导航路线"
}
```

## Data Requirements

Create `data/itinerary.json` with at least:

```json
{
  "tripId": "",
  "tripTitle": "",
  "startDate": "",
  "endDate": "",
  "travelers": "",
  "transportMode": "",
  "ui": {
    "format": "travel-story-map-h5",
    "heroTitle": "出发总是美丽的",
    "subtitle": "",
    "emotionalLine": "",
    "chips": [],
    "exportTarget": "poster"
  },
  "app": {
    "mode": "static-local-first",
    "storageKey": "travelPlanApp:trip-id:v1",
    "version": 1,
    "modules": {
      "budget": true,
      "reservations": true,
      "packing": true,
      "todos": true
    },
    "share": {
      "defaultMode": "public-readonly-base-itinerary",
      "localEdits": "per-browser-localStorage",
      "exportLocalProgress": true,
      "importLocalProgress": true
    }
  },
  "routeMap": {
    "mode": "leaflet",
    "provider": "openstreetmap",
    "fallbackMode": "illustrated",
    "center": { "lat": null, "lng": null },
    "zoom": 11,
    "nodes": [],
    "lines": [],
    "summary": ""
  },
  "socialExperience": {
    "status": "verified / partial / needs_verification",
    "retrievedAt": "",
    "primaryPlatforms": ["xiaohongshu"],
    "queries": [],
    "signals": [
      {
        "topic": "queue / route / avoid-pit / photo / travelPhoto / food / lodging / charter / spending / weather",
        "finding": "",
        "decisionImpact": "",
        "confidence": "high / medium / low",
        "verificationNote": ""
      }
    ]
  },
  "travelPhotography": {
    "recommendation": "none / optional / recommended / charter_plus_photo / photographer_plus_styling",
    "fitReason": "",
    "bestDayAndTime": "",
    "style": "",
    "packageChecklist": [],
    "costRisks": [],
    "serviceRisks": [],
    "questionsBeforeBooking": [],
    "phoneFirstAlternative": ""
  },
  "days": [
    {
      "day": 1,
      "date": "",
      "city": "",
      "hotel": "",
      "theme": "",
      "weather": {
        "condition": "",
        "high": "",
        "low": "",
        "rainProbability": "",
        "wind": "",
        "clothingAdvice": ""
      },
      "route": [],
      "timeSlots": [
        {
          "time": "",
          "title": "",
          "place": "",
          "transport": "",
          "cost": "",
          "walking": "",
          "staminaCost": "",
          "handbook": "",
          "cutIfDelayed": ""
        }
      ],
      "dailyMap": {
        "provider": "openstreetmap",
        "nodes": [],
        "lines": [],
        "summary": ""
      },
      "transport": [],
      "spots": [],
      "lodgingBase": {
        "area": "",
        "why": "",
        "changeHotel": "",
        "nightSafety": "",
        "parking": "",
        "laundry": "",
        "hospitalPharmacy": "",
        "nextDayDeparture": ""
      },
      "photoPlan": [
        {
          "shotName": "",
          "spot": "",
          "bestTime": "",
          "pose": "",
          "composition": "",
          "outfit": "",
          "props": "",
          "devicePlan": "",
          "weatherAndCrowdFallback": "",
          "aiOutputRole": ""
        }
      ],
      "meals": {},
      "walking": {
        "minutes": "",
        "steps": "",
        "intensity": ""
      },
      "safety": {},
      "backupPlan": {
        "rain": [],
        "heatOrCold": [],
        "wind": [],
        "lowStamina": [],
        "crowd": [],
        "closure": [],
        "delay": []
      },
      "aiOutputs": []
    }
  ],
  "planB": [],
  "budgetItems": [],
  "reservations": [],
  "packingItems": [],
  "todos": [],
  "checklist": {
    "sevenDaysBefore": [],
    "threeDaysBefore": [],
    "oneDayBefore": [],
    "eachMorning": [],
    "eachNight": [],
    "beforeReturn": []
  }
}
```

For `budgetItems`, `reservations`, `packingItems`, `todos`, localStorage behavior, and static deployment requirements, follow `interactive-web-app-spec.md`.

## Image File Requirements

- Save attraction images under `assets/images/dayXX/`.
- Use English or pinyin filenames with no spaces.
- Include `alt` text for every image.
- Show source, content description, and authenticity warning under every image.
- List all image sources in project `README.md`.

Image source table:

| Filename | Date | Attraction | Source URL | Image content | Real on-site? | Bias warning |
| --- | --- | --- | --- | --- | --- | --- |

## Project README Requirements

The generated `travel-plan/README.md` must explain:

- What the project is.
- How to open `index.html`.
- How to deploy the folder to a static host or share it as a public link.
- How local browser progress works for budget, reservations, packing, and todos.
- How to export, import, or reset local progress JSON.
- How to use the right-swipe route reveal and route story map.
- How the Leaflet + OpenStreetMap real map works, what to do if map tiles fail, and which nodes have approximate or missing coordinates.
- How to export the long image PNG.
- What each folder is for.
- Image source notes.
- Social-experience source notes: which public platforms were checked, which queries were used, what signals affected route decisions, and which items still need verification.
- Photo check-in, device, outfit, prop, and AI output notes.
- Which facts need pre-departure verification.
- How to modify one day's itinerary.
- How to replace images.
- How to print or export PDF.
