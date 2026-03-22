---
name: action-figure-generator
description: "Action Figure Generator. Generate action figure style images using Action Figure Generator. Triggers: action figure, image generation"
allowed-tools: Bash(curl *), WebFetch
---

# Action Figure Generator

Generate action figure style images using Action Figure Generator. Supports multiple aspect ratios (1:1, 2:3, 3:2).

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "action-figure-generator",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/person-photo.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string |  | Options: `1:1`, `2:3`, `3:2` |
| `image_url_1` | string |  |  |
| `style_slug` | string | digital-nomad | Options: `doom-scroller`, `airport-nomad`, `main-character-energy`, `therapy-warrior`, `digital-nomad`, `foodie-explorer`, `spirit-squad-captain`, ... |

## Examples

**Create an action figure:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "action-figure-generator",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/person-photo.jpg"
    }
  }'
```

**Sci-fi action figure:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "action-figure-generator",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "prompt": "A space explorer in a detailed spacesuit with a glowing visor"
    }
  }'
```

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
