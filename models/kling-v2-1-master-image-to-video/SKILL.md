---
name: kling-v2-1-master-image-to-video
description: "Kling v2.1 | Master | Image to Video. Convert images to premium videos using Kling v2.1 Master. The highest quality Kling image-to-video model. Triggers: kling master image to video, kling v2.1 i2v, kling master animate, premium image to video kling"
allowed-tools: Bash(curl *), WebFetch
---

# Kling v2.1 | Master | Image to Video

Convert images to premium-quality videos using Kling v2.1 Master. The highest quality tier for image-to-video in the Kling v2.1 family, with control over aspect ratio, duration, CFG scale, and negative prompting.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-1-master-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/mountain-lake.jpg",
      "prompt": "Gentle ripples spreading across the lake surface, clouds slowly drifting overhead",
      "aspect_ratio": "16:9",
      "duration": 5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio. Options: `16:9`, `9:16`, `1:1` |
| cfg_scale | number | 0.5 | Classifier-free guidance scale |
| duration | integer | 5 | Video duration in seconds |
| image_url | string | - | URL of the input image |
| negative_prompt | string | - | Text describing what to avoid |
| prompt | string | - | Text prompt to guide the animation |

## Examples

**Animate a portrait:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-1-master-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/woman-portrait.jpg",
      "prompt": "She slowly turns her head and smiles, hair gently flowing, soft natural lighting",
      "aspect_ratio": "9:16",
      "duration": 5,
      "negative_prompt": "blurry, distorted, low quality"
    }
  }'
```

**Product showcase animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-1-master-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/luxury-watch.jpg",
      "prompt": "The watch slowly rotates, light catching the crystal and metal details, premium product showcase",
      "aspect_ratio": "1:1",
      "cfg_scale": 0.5
    }
  }'
```

## Related Models

- [Kling v2.1 | Master | Text to Video](../kling-v2-1-master-text-to-video/) - Master text-to-video
- [Kling v2.1 | Pro | Image to Video](../kling-v2-1-pro-image-to-video/) - Pro tier image-to-video
- [Google Veo 3 | Image to Video](../veo-3-image-to-video/) - Google's image-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
