# Pyxino: story generation and adaptation pipeline (v1)

First version of the n8n workflows behind Pyxino, an automated pipeline that
collects stories, builds narrative artifacts, adapts them to a target culture
and validates the result.

## Workflows (`workflows/`)

| File | Role |
|---|---|
| A1-scrape-story-catalog | Scrape the story catalog |
| A2-scrape-full-story-page | Scrape full story pages |
| A3-artifacts-factory | Build narrative artifacts |
| A4-local-profiles-factory | Generate locale profiles |
| A5-story-adaptation | Culturally adapt a story |
| A6-story-validation-engine | Automatic validation |
| A7-human-review-callback | Human review callback |
| A8-illustration-generator | Generate illustrations |
| A9-illustration-validation | Validate illustrations |
| storyAdaptationTest | Adaptation test workflow |

## Setup

1. Import each JSON into n8n (Workflows, Import from file).
2. Recreate your own credentials (Firebase service account, LLM API key, etc.).
   No credentials are included in the exports.
3. Replace the placeholders: `YOUR_FIREBASE_PROJECT_ID`, `YOUR_EMAIL@example.com`,
   `YOUR_BRAND_EMAIL@example.com`, `YOUR_N8N_HOST`.

## Notes

Exports were cleaned: pinned data, instance IDs and personal values removed.

## Example data (`data/`)

Sample pipeline outputs for two stories, each adapted to three cultures
(Tunisian, Italian, Japanese). Exported from Firestore, then cleaned
(tracking fields, URLs and engagement counters removed).

| Folder | Content |
|---|---|
| `raw_stories/` | Source story metadata (2 stories). The original text is not redistributed: see `source_domain` |
| `story_bibles/` | Story Bible per story (characters, relationships, world rules) |
| `story_blueprints/` | Blueprint per story (structure, key events, protected elements) |
| `locale_profiles/` | Locale Profile per story x culture (6 files) |
| `index.json` | Stories and target cultures |

Stories: Cinderella (`416c9893cf9c4515`) and Sleeping Beauty (`40ec4d125d8d2dee`).
Source: readthetale.com. Five profiles have status `done`; the Cinderella Tunisian
profile has status `validated`.
