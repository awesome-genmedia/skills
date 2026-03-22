---
name: photon
description: "Photon. Generate high-quality images using Photon. Triggers: image generation, luma photon"
allowed-tools: Bash(curl *), WebFetch
---

# Photon

Generate high-quality images using Photon. Supports multiple aspect ratios (1:1, 3:4, 4:3, 9:16, 16:9, 9:21, 21:9), reproducible results via seed.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "photon",
    "version": "0.0.1",
    "input": {
      "prompt": "A stunning portrait photograph with dramatic studio lighting"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | 16:9 | An enumeration.. Options: `1:1`, `3:4`, `4:3`, `9:16`, `16:9`, `9:21`, `21:9` |
| `character_reference_url` | string |  | URL of a character reference image |
| `image_reference_url` | string |  | URL of a reference image to guide generation |
| `image_reference_weight` | number | 0.85 | Weight of the reference image. Larger values will make the reference image have |
| `prompt` | string |  | Text prompt for image generation |
| `seed` | integer |  | Random seed. Set for reproducible generation |
| `style_reference_url` | string |  | URL of a style reference image |
| `style_reference_weight` | number | 0.85 | Weight of the style reference image |

## Examples

**Generate a portrait:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "photon",
    "version": "0.0.1",
    "input": {
      "prompt": "A stunning portrait photograph with dramatic studio lighting"
    }
  }'
```

**Vintage style photo:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "photon",
    "version": "0.0.1",
    "input": {
      "prompt": "A vintage film photograph of a European cafe terrace in autumn",
      "aspect_ratio": "9:16",
      "seed": 42
    }
  }'
```

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
