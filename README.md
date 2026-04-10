# DeskModal Plugin Index

Curated list of plugins for the [DeskModal](https://github.com/Desk-Modal/deskmodal) App Market.

DeskModal discovers available plugins by fetching `plugin-index.json` from this repository. Each entry points to a GitHub repository that publishes plugin releases.

## Format

`plugin-index.json` is a JSON array of plugin entries. Each entry has the following fields:

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `owner` | string | yes | GitHub organization or user that owns the plugin repo |
| `repo` | string | yes | GitHub repository name |
| `name` | string | yes | Human-readable display name |
| `description` | string | yes | Short description shown in the App Market |
| `categories` | string[] | yes | One or more categories: `Data`, `Charting`, `Trading`, `Analytics`, `Services` |
| `featured` | boolean | yes | Whether the plugin appears in the featured section of the App Market |

### Example entry

```json
{
  "owner": "Desk-Modal",
  "repo": "plugin-tradesurface-chart",
  "name": "TradeSurface Chart",
  "description": "Advanced multi-asset charting with 50+ indicators and drawing tools",
  "categories": ["Charting"],
  "featured": true
}
```

## JSON Schema

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "type": "array",
  "items": {
    "type": "object",
    "required": ["owner", "repo", "name", "description", "categories", "featured"],
    "properties": {
      "owner": { "type": "string", "minLength": 1 },
      "repo": { "type": "string", "minLength": 1 },
      "name": { "type": "string", "minLength": 1 },
      "description": { "type": "string", "minLength": 1 },
      "categories": {
        "type": "array",
        "items": { "type": "string" },
        "minItems": 1
      },
      "featured": { "type": "boolean" }
    },
    "additionalProperties": false
  }
}
```

## How to Add a Plugin

1. Fork this repository
2. Add your plugin entry to `plugin-index.json`
3. Ensure your entry includes all required fields
4. Submit a pull request

The CI pipeline validates that the JSON is parseable, all required fields are present, and there are no duplicate `owner/repo` combinations.

## License

MIT
