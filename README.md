# travel-plan-html skill

This repository contains a Codex skill that routes a travel request to a focused answer, full itinerary, photography/content plan, cultural-tourism proposal, post-trip summary, or requested travel website/app.

Quick questions stay focused. Full itineraries retain detailed planning and relevant photo guidance, with text as the default output. HTML, H5, deployable sites, and editable browser tools are generated when requested or continued from an established web task. Follow-up edits preserve the existing format and update only the affected content. Task routing and reference selection are defined in `skills/travel-plan-html/SKILL.md`.

## Skill

The skill lives at:

```text
skills/travel-plan-html/
```

It includes:

- `SKILL.md`: trigger metadata and core workflow.
- `references/travel-planner-prompt.md`: travel planning rules and itinerary structure.
- `references/b-guide-workflow.md`: detailed traveler decisions and full B-guide workflow.
- `references/photo-output-guide.md`: classic check-in, outfit, device, and AI/social output rules.
- `references/ui-style-guide.md`: travel story map H5 visual and interaction rules.
- `references/html-output-spec.md`: static website file and layout requirements.
- `references/interactive-web-app-spec.md`: deployable local-first app rules for budget, reservations, packing, todos, localStorage progress, and static hosting.
- `references/quality-checklist.md`: final validation checklist.
- `agents/openai.yaml`: UI metadata for Codex skill lists.

## Install

Clone this repository and copy `skills/travel-plan-html` into your Codex skills directory:

```bash
git clone https://github.com/tingyi-lan/travel-plan-html-skill.git
cd travel-plan-html-skill
mkdir -p ~/.codex/skills
cp -R skills/travel-plan-html ~/.codex/skills/
```

Then invoke it with a prompt such as:

```text
Use $travel-plan-html to plan a 7-day family self-driving trip with classic photo check-in guidance and generate a deployable local-first travel web app with budget, reservations, packing, and todo modules.
```

## Notes

The skill requires real-time verification for weather, openings, tickets, hotel facts, transport, hospitals, restaurants, images, photo conditions, viewpoint access, and drone/no-fly rules. If a fact cannot be verified, the generated itinerary must mark it as `出发前需核验`.

When a local-first travel web app is requested, the output is static and deployable. Anyone with the link can open the base itinerary, while each viewer's budget, reservation, packing, and todo edits are saved only in that viewer's browser with `localStorage` unless they export and share their local progress JSON. A read-only site or focused tool includes only its requested modules.
