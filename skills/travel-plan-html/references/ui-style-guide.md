# UI Style Guide

Use this reference for requested travel HTML, a website, H5, static web project, or a visual page/poster export. Follow task selection in `SKILL.md`: a text itinerary or an answer intended for sharing does not require this visual workflow. Apply full-site requirements to full sites, and only the relevant visual rules to a focused page/tool, export, or existing-site edit.

## Product Direction

Generate an interactive travel story map H5, not a plain guide document, booking app flow, Bootstrap page, or Markdown-like article.

Core experience:

1. A magazine-like destination cover.
2. Literary emotional entry with the fixed title `出发总是美丽的`.
3. A right-swipe paper/scroll interaction that reveals the route map.
4. A travel story map with day nodes, route curve, base hotels, photo spots, meal/rest points, emergency points, and planning judgment.
5. Rich daily route pages built around `DAY{n} 行程` and `每日路线概览`.
6. Classic photo check-in guide on the homepage and repeated inside relevant daily spots.
7. Separate Plan B, destination-specific checklist, and emergency notes.
8. One-click long-image PNG export.

## First Screen Cover

Use a full-screen destination-specific high-resolution landscape image.

Requirements:

- Use a real destination image, not an abstract illustration.
- Keep it bright, natural, relaxed, and travel-magazine-like.
- Add a light warm overlay for readability.
- Do not use black tech style, dark earth visuals, grass close-ups, abstract tech images, or a booking-app hero.

Cover title:

```text
出发总是美丽的
```

Title requirements:

- Centered in the upper-middle of the first viewport.
- Fully visible on mobile and desktop; no overflow.
- Use calligraphy/serif/literary Chinese typography.
- Do not use heavy black sans, huge PPT-style titles, or `专属 Travel Plan`.

Suggested CSS:

```css
.hero-title {
  font-family: "Ma Shan Zheng", "Noto Serif SC", "Songti SC", "STSong", serif;
  font-size: clamp(34px, 4.8vw, 64px);
  font-weight: 400;
  line-height: 1.28;
  letter-spacing: 0.12em;
  color: #fff;
  text-align: center;
  text-shadow: 0 12px 38px rgba(60, 42, 28, 0.32);
  white-space: nowrap;
}
```

Subtitle format:

```text
【目的地】｜【天数】日【同行人/出行方式】计划
```

Examples:

- 京都｜4 日一人自由行计划
- 京都与大阪｜7 日亲子自由行计划
- 伊犁草原｜6 日朋友自驾计划

Emotional line:

- Default: `尤其是在一个阳光普照的清晨上路。`
- Solo trip: `尤其是在一个人决定重新出发的时候。`
- Couple trip: `尤其是在两个人一起奔向远方的时候。`
- Friends: `尤其是在笑声把路途填满的时候。`
- Self-driving: `尤其是在方向盘指向远方的时候。`
- Family/parents/kids: `把奔波放慢，把团圆走成风景。`

## Cover Chips

Show 3-5 translucent pill chips from traveler profile and system judgment:

- 一人自由行
- 手机出片路线
- 含雨天 Plan B
- 少换酒店
- 低步数路线
- 文化深度讲解
- 预算友好
- 含经典机位

Style:

- Light translucent glass effect.
- Pill shape.
- Avoid colorful icon clutter.

## Swipe-To-Reveal Map

Place a centered paper/scroll card in the hero, below title/subtitle. The route preview must be centered, not isolated in the lower-right corner.

Initial state:

- The preview map must be fully covered by paper.
- The paper should have fold, crease, slight shadow, paper brightness, and subtle torn-edge texture.
- Show the prompt only once:

```text
右滑开启属于你的专属地图
```

Slider copy:

```text
滑动开启
```

Do not repeat the full prompt inside both the card and the slider.

After the user swipes right:

- Paper slides/tears/rolls open to the right.
- A compact real route map is revealed. Use Leaflet + OpenStreetMap when the page is online; if the hero reveal must stay offline-safe, use a static coordinate-based real-map preview with accurate geography rather than an abstract route curve.
- Route lines and markers may animate, but they must sit on a real map or real-coordinate fallback.
- Warm red route nodes light up in sequence.
- Node labels appear in sequence.
- After animation, scroll to the route story map module.

Use Pointer Events for mouse, touchpad, finger, and stylus compatibility.

## Route Preview Map

The route preview must feel like a real travel map, not an abstract illustration, default Google screenshot, or black module.

Style:

- Use a real map base by default. Prefer Leaflet + OpenStreetMap if it can load in the reveal card.
- If an interactive map inside the reveal card is too heavy, use a static real-coordinate preview that preserves the relative geography, coastline/river/rail/road feel, and place order.
- Use light, comfortable map colors.
- Use soft bright route polylines that follow the trip node sequence. Label them as planning lines unless a routing API is configured.
- Use warm red or vermilion node dots.
- Labels must be rounded capsule cards with place name and short execution cue.

Example node labels:

- 京都站｜轻装抵达
- 伏见稻荷｜清晨鸟居
- 清水寺｜二年坂人像
- 岚山｜竹林与河岸

## Route Story Map Module

This is the core selling point.

Include:

- A zoomable real map implemented with Leaflet + OpenStreetMap tiles for the free test version.
- Internal coordinate-based real-map fallback for long-image export and CDN/tile failure.
- Day nodes.
- Route curves.
- Place labels.
- Hotel base markers.
- Photo spot markers.
- Meal/rest markers.
- Emergency markers.
- Travel judgment summary.
- One-click long-image export button.

Do not show homepage labels or helper text such as `插画地图`, `真实地图感模式`, `地图模式`, or `正式接入可选择 Mapbox/Leaflet`. The user-facing module should simply feel like the route map.

Real map mode:

- Use Leaflet with OpenStreetMap tiles by default; no API key is required for testing.
- Include proper OpenStreetMap/Leaflet attribution and do not hide it.
- Plot verified or explicitly approximate coordinates for scenic spots, hotel bases, meals, photo spots, parking/drop-off points, transit hubs, hospitals, pharmacies, and emergency points.
- Use category-specific marker colors or icons and clear popups with name, day, time, role, risk note, and link to the relevant daily card when possible.
- Draw route lines as simple polylines through the itinerary coordinates unless a routing API is explicitly configured. Do not present straight-line polylines as exact driving, walking, or transit routes.
- If coordinates are missing, show the node in the coordinate-fallback map list and mark it as `坐标需核验`.
- If Leaflet or map tiles fail to load, keep the coordinate-based fallback map and all itinerary content usable.

Fallback route map:

- Stable for long-image export.
- Must still be based on real coordinates and real geography.
- Magazine-like, light, premium, not cheap cartoon.
- Avoid abstract decorative curves, pure flat map, and black tech style.

Future map upgrades:

- China routes can upgrade to AMap when a Web JS API key is provided, but do not show this as normal page copy.
- International or branded projects can upgrade to Mapbox GL JS when a Mapbox access token is provided, but do not show this as normal page copy.
- Long-image export should try to export the real map first. If cross-origin tile capture fails, use the coordinate-based fallback and show a brief export note.

## Daily Route Pages

Daily pages are the most important experience. Use human travel-agent language such as `DAY1 行程`, `每日路线概览`, and `今日安排`. Do not use mechanical labels such as `每日完整执行脚本`.

The main daily section should place time-slot cards on the left and a daily real map on the right. Use Leaflet + OpenStreetMap by default, scoped to that day's route and markers. It includes:

- Time.
- Place.
- Transport.
- Stay duration.
- Food.
- Physical intensity.
- Traveler fit.
- Photo spots.
- Avoid-pit notes.
- Plan B.
- Emergency point.

Each time slot may expand into a travel handbook block with attraction images, indoor/outdoor status, photo advice, ticket/opening/reservation notes, queue risk, toilets, rest points, and what to cut if delayed. Use timeline storytelling and rich cards, not large table stacks.

## Long Image Export

Include a `一键导出长图 PNG` button.

Export area:

```html
<div id="poster">...</div>
```

Export content:

- Cover title.
- User trip summary.
- Travel quote.
- Real route map when capture succeeds; coordinate-based real-map fallback if tile export fails.
- Daily route overviews.
- Photo guide.
- Plan B.
- Checklist.
- Emergency reminder.

Do not export:

- Debug buttons.
- Map toggle controls.
- Navigation controls.
- Temporary interaction controls.

Use `html2canvas` or equivalent DOM-to-image library. If external library loading fails, keep a graceful fallback: tell the user to use browser screenshot/print export.

## Prohibitions

Do not generate:

- `专属 Travel Plan` as the main title.
- Black tech hero.
- Grass close-up hero.
- Oversized title that clips.
- Duplicate right-swipe prompt.
- Route preview visible before the paper opens.
- Isolated lower-right route preview.
- Heavy black sans-serif hero.
- Markdown document page.
- App booking flow.
- Large piles of tables.
- Default Bootstrap styling.
- Too many bright icons.
