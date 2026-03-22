---
name: "Remove Background Enhance"
description: "Remove backgrounds from images with enhanced quality. Trigger: Use when the user wants to remove an image background, or requests 'remove background', 'rembg', 'background removal', or 'make transparent background'."
allowed-tools: ["Bash"]
---

# Remove Background Enhance

Remove the background from an image with enhanced output quality. Produces clean cutouts suitable for product photography, design compositing, and more.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "rembg-enhance",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/photo-with-background.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `image` | string | (empty) | Input image URL |

## Output

- **Type:** image

## Examples

### Product Photo Background Removal
```json
{
  "model": "rembg-enhance",
  "version": "0.0.1",
  "input": {
    "image": "https://example.com/product-on-table.jpg"
  }
}
```

### Portrait Background Removal
```json
{
  "model": "rembg-enhance",
  "version": "0.0.1",
  "input": {
    "image": "https://example.com/headshot-outdoor.jpg"
  }
}
```

## Related Models

- [Bria Product Shot](../bria-product-shot/SKILL.md) - Place products in new scenes after background removal
- [Kling 1.5 Kolors Virtual Try On](../kling-v1-5-kolors-virtual-try-on/SKILL.md) - Virtual clothing try-on
- [Seedream V4 Edit](../seedream-v4-edit/SKILL.md) - Edit images with text prompts

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
