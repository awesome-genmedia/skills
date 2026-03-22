---
name: imagen-3-fast
description: "Imagen 3 | Fast. Generate image content using Imagen 3 | Fast. Triggers: image generation, imagen"
allowed-tools: Bash(curl *), WebFetch
---

# Imagen 3 | Fast

Generate image content using Imagen 3 | Fast. Supports multiple aspect ratios (1:1, 9:16, 16:9, 3:4, 4:3), negative prompt support.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "imagen-3-fast",
    "version": "0.0.1",
    "input": {
      "prompt": "A beautiful landscape with mountains and a clear blue sky"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | 1:1 | An enumeration.. Options: `1:1`, `9:16`, `16:9`, `3:4`, `4:3` |
| `negative_prompt` | string |  | Text prompt for what to discourage in the generated images |
| `prompt` | string |  | Text prompt for image generation |
| `safety_filter_level` | string | block_medium_and_above | An enumeration.. Options: `block_low_and_above`, `block_medium_and_above`, `block_only_high` |

## Examples

**Basic generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "imagen-3-fast",
    "version": "0.0.1",
    "input": {
      "prompt": "A beautiful landscape with mountains and a clear blue sky"
    }
  }'
```

**Advanced generation with options:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "imagen-3-fast",
    "version": "0.0.1",
    "input": {
      "prompt": "A beautiful landscape with mountains and a clear blue sky",
      "aspect_ratio": "9:16",
      "negative_prompt": "blurry, distorted, low quality, watermark"
    }
  }'
```

## Related Models

- [Imagen 3](../imagen-3/) - Generate image content using Imagen 3.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
