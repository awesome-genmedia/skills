---
name: bytedance-seedream-v5-lite-edit
description: "Bytedance | Seedream | v5 | Lite | Edit. Edit images using ByteDance Seedream v5 Lite model. Triggers: image edit, seedream, bytedance, edit image, modify"
allowed-tools: Bash(curl *), WebFetch
---

# Bytedance | Seedream | v5 | Lite | Edit

Edit images using ByteDance's Seedream v5 Lite model. A lightweight, fast image editing model.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bytedance-seedream-v5-lite-edit",
    "version": "0.0.1",
    "input": {}
  }'
```

## Parameters

This model has no documented parameters. Refer to the API documentation for usage details.

## Examples

**Basic image edit:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bytedance-seedream-v5-lite-edit",
    "version": "0.0.1",
    "input": {}
  }'
```

## Related Models

- [bytedance-seedream-v5-lite-text-to-image](../bytedance-seedream-v5-lite-text-to-image/) - Seedream v5 Lite text to image
- [firered-image-edit-v1-1](../firered-image-edit-v1-1/) - Firered image editing
- [nano-banana-2-edit](../nano-banana-2-edit/) - Nano Banana 2 image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
