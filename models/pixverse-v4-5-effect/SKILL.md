---
name: pixverse-v4-5-effect
description: "PixVerse v4.5 | Effect. Apply visual effects to images and generate videos using PixVerse v4.5 | Effect. Triggers: pixverse, video effects, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# PixVerse v4.5 | Effect

Apply visual effects to images and generate videos using PixVerse v4.5 | Effect. Supports configurable duration, quality control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v4-5-effect",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/your-image.jpg",
      "template_slug": "jellycat-everything"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `duration` | integer | 5 |  |
| `image_url` | string |  |  |
| `image_urls` | array |  |  |
| `motion_mode` | string | normal | Controls animation speed. Options: `normal`, `fast` |
| `quality` | string | 720p | Options: `360p`, `540p`, `720p`, `1080p` |
| `sound_effect_content` | string |  |  |
| `sound_effect_switch` | boolean | True |  |
| `template_slug` | string | jellycat-everything | Pixverse Effect |

## Examples

**Apply visual effect:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v4-5-effect",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/your-image.jpg",
      "template_slug": "jellycat-everything"
    }
  }'
```

**Different effect style:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v4-5-effect",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/your-image.jpg",
      "template_slug": "squish",
      "duration": 8,
      "quality": "1080p",
      "motion_mode": "fast"
    }
  }'
```

## Related Models

- [PixVerse v4.5 | Transition](../pixverse-v4-5-transition/) - Create smooth video transitions between images using PixVerse v4.5 | Transition.
- [PixVerse v4.5 | Text to Video](../pixverse-v4-5-text-to-video/) - Generate videos from text descriptions using PixVerse v4.5 | Text to Video.
- [PixVerse v4.5 | Image to Video](../pixverse-v4-5-image-to-video/) - Generate videos from images using PixVerse v4.5 | Image to Video.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
