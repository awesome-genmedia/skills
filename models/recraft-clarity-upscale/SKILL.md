---
name: recraft-clarity-upscale
description: "Recraft Clarity Upscale. Upscale and enhance image clarity using Recraft Clarity Upscale. Triggers: image generation, recraft, upscale"
allowed-tools: Bash(curl *), WebFetch
---

# Recraft Clarity Upscale

Upscale and enhance image clarity using Recraft Clarity Upscale.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "recraft-clarity-upscale",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/low-res-image.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `image` | string |  | Image to upscale |

## Examples

**Upscale an image:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "recraft-clarity-upscale",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/low-res-image.jpg"
    }
  }'
```

**Enhance photo quality:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "recraft-clarity-upscale",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/photo-to-enhance.jpg"
    }
  }'
```

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
