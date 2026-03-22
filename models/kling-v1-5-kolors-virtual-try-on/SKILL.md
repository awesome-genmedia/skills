---
name: "Kling 1.5 Kolors Virtual Try On"
description: "Virtual try-on using Kling 1.5 Kolors. Trigger: Use when the user wants to try on clothing virtually, or requests 'virtual try on', 'try on clothes', 'kling kolors', or 'see how clothing looks on me'."
allowed-tools: ["Bash"]
---

# Kling 1.5 | Kolors Virtual Try On

Virtually try on garments by combining a human image with a garment image. See how clothing looks on a person without physical fitting.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-5-kolors-virtual-try-on",
    "version": "0.0.1",
    "input": {
      "human_image_url": "https://example.com/person.jpg",
      "garment_image_url": "https://example.com/dress.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `garment_image_url` | string | (empty) | URL to the garment image |
| `human_image_url` | string | (empty) | URL for the human image |

## Output

- **Type:** image

## Examples

### Try On a Jacket
```json
{
  "model": "kling-v1-5-kolors-virtual-try-on",
  "version": "0.0.1",
  "input": {
    "human_image_url": "https://example.com/model-photo.jpg",
    "garment_image_url": "https://example.com/leather-jacket.jpg"
  }
}
```

### Try On a Formal Dress
```json
{
  "model": "kling-v1-5-kolors-virtual-try-on",
  "version": "0.0.1",
  "input": {
    "human_image_url": "https://example.com/full-body-photo.jpg",
    "garment_image_url": "https://example.com/evening-gown.jpg"
  }
}
```

## Related Models

- [AI Face Aesthetics](../ai-face-aesthetics/SKILL.md) - Face shape adjustments
- [Bria Product Shot](../bria-product-shot/SKILL.md) - Product photography generation
- [Remove Background Enhance](../rembg-enhance/SKILL.md) - Background removal for clean garment images

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
