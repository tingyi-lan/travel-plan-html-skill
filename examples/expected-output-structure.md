# Expected Output Structure

For the full itinerary plus local-first web app explicitly requested in `sample-user-request.md`, the skill should produce the following. This is not the default checklist for quick answers, standalone photography/content, proposals, or recaps. For a full text itinerary, use the relevant planning outputs without generating web files.

1. User demand parsing table.
2. Travel feasibility judgment.
3. 2-3 route options with one recommendation.
4. Final route overview table.
5. D1-Dn hour-level daily itinerary.
6. Specific hotel recommendations and booking verification notes.
7. Real attraction photos near matching sections, or a missing-image checklist.
8. Daily weather, walking time, steps, elderly/child friendliness, meals, transport, and safety.
9. Classic photo check-in guidance: exact spots, best time, pose, composition, outfit, props, device plan, paid photography/rental judgment, and AI/social output plan.
10. Travel story map web app UI: bright destination cover, `出发总是美丽的`, swipe paper reveal, Leaflet + OpenStreetMap route map, coordinate fallback, and long-image export.
11. Interactive local-first trip dashboard: budget, reservations, packing, and todo modules with `localStorage` progress.
12. Budget, reservation checklist, packing checklist, todo/checklist phases, and adjustment options.
13. For the requested web app, a deployable `travel-plan/` static app with `index.html`, daily pages, CSS, JS, images, `data/itinerary.json`, and README.

## Task Routing Examples

These examples describe output scope, not researched destination facts. Resolve relative dates and verify relevant current facts when actually executing a request.

| User request | Expected scope |
| --- | --- |
| “故宫下周一开放吗？简短回答。” | Focused official-rule/date verification and a short sourced answer. No itinerary, photography survey, or website. |
| “北京四天路线简单说一下。” | Concise route sketch with relevant feasibility/experience checks. No full daily handbook or web files. |
| “安排北京四天完整行程，带父母，发给家人看。” | Full researched text itinerary with daily execution detail, relevant photo guidance, budget, Plan B, and checklists. Sharing with family does not imply a website. |
| “把这份已经确定的行程做成只读 HTML，路线不变。” | Convert the supplied plan into a read-only travel site, retaining source/uncertainty notes. No full replan or editable dashboard. |
| “做一个能勾选并保存进度的行李清单网页。” | Focused packing tool with local progress. No unrelated budget/reservation/todo modules or daily itinerary pages. |
| “根据我上传的照片写三条旅行朋友圈文案。” | Three original captions grounded in the supplied photos. No destination/trend survey unless external facts or research are requested. |
| “给景区做一个智能体商业方案。” | B-side research, pain points, scenarios, commercial value, rollout, and metrics. No personal travel itinerary or website by default. |
| “根据这些笔记和实际账单整理旅行复盘。” | Summary and actual spending grounded in the supplied records. No invented experiences, new itinerary, or website. |
| “把现有攻略网站第二天换成雨天方案。” | Update day 2 and affected map/data/budget/checklist references; retain the site's established format and unrelated days. |
