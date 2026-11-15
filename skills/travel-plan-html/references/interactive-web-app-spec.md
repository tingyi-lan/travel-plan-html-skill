# Interactive Web App Specification

Use this reference for a requested local-first travel web app, editable browser tool, or interactive budget/reservation/packing/todo feature. A plain budget table, booking checklist, packing list, or shareable read-only page does not by itself request an interactive app. Follow task selection in `SKILL.md`.

Within this app task, the default product target is a static, local-first travel web app: it can be deployed as ordinary files, opened by anyone with the link, and saves each viewer's personal edits in that viewer's browser with `localStorage`.

## Product Scope

Build a lightweight deployable app, not a full account system.

Required properties:

- Static hosting compatible: GitHub Pages, Vercel, Netlify, OpenAI Sites, S3-style static hosting, or a simple web server.
- No backend, database, login, WebSocket, or cloud sync unless the user explicitly asks for that later.
- Every generated page still works as a read-only guide if JavaScript or `localStorage` is unavailable.
- Interactive edits are per browser and per device. They are not shared with other travelers through the public link.
- The project must use relative paths so it can be hosted under a subpath such as `/my-trip/`.
- Do not put API keys, private booking data, passport details, or other secrets into public files.

Explain this in the project README:

```text
This is a static local-first travel app. The shared link opens the same base itinerary for everyone. Your checkbox/status/budget edits are saved only in your browser unless you export and share your local progress JSON.
```

## Required Modules

For a full local-first travel app, include these four modules on the homepage and, where useful, inside daily pages. For a focused tool or feature request, implement only the requested modules and set the data model's module flags accordingly; omit unrelated itinerary pages and modules.

### Budget

Purpose: turn the planning budget into an editable trip ledger.

Minimum UI:

- Summary: planned total, actual total, remaining or over-budget amount.
- Category breakdown: accommodation, food, transport, tickets, activities, shopping, emergency reserve, other.
- Editable item list with amount, currency, category, day, note, paid status.
- Add item, edit item, delete item, toggle paid.
- Reset to planned values.

Data behavior:

- Initial items come from `data/itinerary.json`.
- User edits are saved in `localStorage`.
- If live prices are uncertain, keep the item and mark `needs_verification`.
- Currency conversion is optional in this phase. If multiple currencies appear, show totals by currency rather than inventing exchange rates.

### Reservations

Purpose: make tickets, hotels, restaurants, flights, trains, activities, and verification tasks trackable.

Minimum UI:

- Status chips: `待预订`, `待确认`, `已确认`, `已取消`, `出发前需核验`.
- Fields: type, title, day/date/time, place, confirmation number, booking URL, document note, cost, verification note.
- Toggle status and edit lightweight fields.
- Highlight urgent items and unresolved verification items.

Data behavior:

- Do not invent booking confirmations, prices, live availability, or reservation numbers.
- For public sharing, avoid exposing private confirmation numbers unless the user supplied them and explicitly wants them in the public app.
- If a document or ticket file is not included, show a file checklist entry instead of a fake attachment.

### Packing

Purpose: make the trip checklist usable on the phone during preparation.

Minimum UI:

- Category groups: documents, clothes, weather gear, medicine, devices, photo gear, child/elderly needs, destination-specific items, other.
- Checkbox per item.
- Quantity and owner/member fields when useful.
- Progress count by category and overall progress.
- Reset packed state.

Data behavior:

- Items are adapted to destination, weather, traveler type, and photo equipment.
- Default checked state is false unless the user supplied an actual packed state.
- Save checked state in `localStorage`.

### Todo

Purpose: make pre-departure and daily operations executable.

Minimum UI:

- Group by phase: 7 days before, 3 days before, 1 day before, each morning, each night, before return.
- Fields: title, due phase/date, priority, owner, linked day/place, status, verification note.
- Toggle done, add task, edit task, delete task.
- Show remaining high-priority tasks.

Data behavior:

- Convert verification, booking, packing, transport, weather, photo, and safety actions into todos.
- Keep tasks concrete and action-oriented.
- Do not hide unresolved facts. Mark them as `出发前需核验`.

## Data Model Additions

Extend `data/itinerary.json` with stable IDs and app state seeds.

Required top-level additions:

```json
{
  "tripId": "trip-slug-or-date",
  "app": {
    "mode": "static-local-first",
    "storageKey": "travelPlanApp:trip-slug-or-date:v1",
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
  "budgetItems": [],
  "reservations": [],
  "packingItems": [],
  "todos": []
}
```

Use stable IDs. They must not change when the page reloads or when a small text edit is made.

Budget item shape:

```json
{
  "id": "budget-hotel-day01",
  "category": "accommodation",
  "title": "",
  "plannedAmount": 0,
  "actualAmount": null,
  "currency": "CNY",
  "day": 1,
  "placeId": "",
  "paid": false,
  "payer": "",
  "splitBetween": [],
  "status": "planned",
  "note": "",
  "verificationNote": ""
}
```

Reservation shape:

```json
{
  "id": "reservation-ticket-day01",
  "type": "ticket",
  "title": "",
  "status": "needs_verification",
  "day": 1,
  "date": "",
  "time": "",
  "placeId": "",
  "bookingUrl": "",
  "confirmationNumber": "",
  "documentNote": "",
  "cost": null,
  "currency": "CNY",
  "verificationNote": ""
}
```

Packing item shape:

```json
{
  "id": "packing-passport",
  "category": "documents",
  "name": "",
  "quantity": 1,
  "owner": "",
  "required": true,
  "packed": false,
  "note": ""
}
```

Todo shape:

```json
{
  "id": "todo-check-weather-day01",
  "phase": "threeDaysBefore",
  "title": "",
  "priority": "high",
  "status": "open",
  "owner": "",
  "day": 1,
  "placeId": "",
  "verificationNote": ""
}
```

Allowed enum values:

- Budget categories: `accommodation`, `food`, `transport`, `tickets`, `activities`, `shopping`, `photo`, `health`, `fees`, `reserve`, `other`.
- Reservation types: `flight`, `train`, `hotel`, `restaurant`, `ticket`, `activity`, `tour`, `car`, `transfer`, `other`.
- Reservation statuses: `to_book`, `to_confirm`, `confirmed`, `cancelled`, `needs_verification`.
- Todo phases: `sevenDaysBefore`, `threeDaysBefore`, `oneDayBefore`, `eachMorning`, `eachNight`, `beforeReturn`.
- Todo status: `open`, `done`.
- Priority: `high`, `medium`, `low`.

## JavaScript Requirements

Implement the interaction in `js/main.js` or small local modules under `js/`.

Required behavior:

- Load initial app data from `data/itinerary.json`.
- Derive a `storageKey` from `itinerary.app.storageKey`.
- Merge saved local state over the initial seed by stable item ID.
- Render budget, reservations, packing, and todos from data.
- Persist every toggle/edit/add/delete to `localStorage`.
- Provide `导出本地进度 JSON`, `导入本地进度 JSON`, and `重置本地进度` controls.
- Keep controls accessible with labels and keyboard focus states.
- Keep all modules usable on mobile without overlapping text.
- If `localStorage` fails, show a compact warning and keep the base itinerary readable.

Local state shape:

```json
{
  "version": 1,
  "updatedAt": "",
  "budgetItems": {},
  "reservations": {},
  "packingItems": {},
  "todos": {}
}
```

Store user edits as maps keyed by item ID, so the generated base itinerary can be updated later without wiping unrelated local progress.

## UI Placement

Homepage:

- Add an `行前工作台` or `旅行准备工作台` section after the route/story overview and before the long checklist.
- Use tabs or segmented controls for `预算`, `预订`, `打包`, `Todo`.
- Show compact summary cards above each module.
- Keep dense tool UI smaller than hero text. This area should feel like a practical trip dashboard.

Daily pages:

- Show day-filtered reservations, budget items, packing reminders, and todos near the relevant daily route or checklist section.
- Link module items to day/place anchors when possible.

README:

- Explain local edits, export/import/reset, and deployment.
- Explain that shared links do not sync personal local edits.

## Deployment Requirements

Generated projects must be deployable without a build step unless the user explicitly asks for a framework.

Static deployment checklist:

- Use relative asset paths.
- Include `index.html` as the app entry.
- Ensure daily pages work under a subpath.
- Do not rely on absolute local filesystem paths.
- Keep all required app code in the generated folder.
- Do not require Node.js for viewing the final site.
- Include a README section for GitHub Pages, Vercel, Netlify, and OpenAI Sites or the specific host requested by the user.

When the user asks Codex to deploy and an OpenAI Sites project is configured, use the Sites workflow. Otherwise, prepare the source so it can be uploaded to any static host.

## Future Upgrade Boundary

Do not quietly promise these in the first local-first app:

- Multi-user real-time editing.
- Cloud sync across devices.
- Login, roles, or private share permissions.
- Real payment settlement.
- Automatic email inbox parsing.
- Secure private document storage.

It is fine to include them in a roadmap section only when the user asks for product planning.
