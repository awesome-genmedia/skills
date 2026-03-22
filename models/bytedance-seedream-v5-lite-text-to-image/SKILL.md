---
name: bytedance-seedream-v5-lite-text-to-image
description: "Bytedance | Seedream | v5 | Lite | Text to Image. Generate images from text using ByteDance Seedream v5 Lite. Triggers: text to image, seedream, bytedance, generate image, t2i"
allowed-tools: Bash(curl *), WebFetch
---

# Bytedance | Seedream | v5 | Lite | Text to Image

Generate images from text descriptions using ByteDance's Seedream v5 Lite model. A lightweight, fast image generation model.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bytedance-seedream-v5-lite-text-to-image",
    "version": "0.0.1",
    "input": {}
  }'
```

## Parameters

This model has no documented parameters. Refer to the API documentation for usage details.

## Examples

**Basic text to image:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bytedance-seedream-v5-lite-text-to-image",
    "version": "0.0.1",
    "input": {}
  }'
```

## Related Models

- [bytedance-seedream-v5-lite-edit](../bytedance-seedream-v5-lite-edit/) - Seedream v5 Lite image editing
- [kling-v3-text-to-image](../kling-v3-text-to-image/) - Kling v3 text to image
- [nano-banana-2-text-to-image](../nano-banana-2-text-to-image/) - Nano Banana 2 text to image

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
