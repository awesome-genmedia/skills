---
name: kling-v1-pro-image-to-video
description: "Kling v1 | Pro | Image to Video. Convert images to high-quality videos using Kling v1 Pro with masking and end-frame support. Professional Kling image animation. Triggers: kling v1 pro image to video, kling pro i2v, kling v1 pro animate, kling pro image animation"
allowed-tools: Bash(curl *), WebFetch
---

# Kling v1 | Pro | Image to Video

Convert images to high-quality videos using Kling v1 Pro. Professional-grade image-to-video with static masking for selective animation and end-frame targeting for controlled transitions.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/cityscape.jpg",
      "prompt": "Cars driving through the streets, lights flickering, people walking on sidewalks, vibrant city life",
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
| negative_prompt | string | blur, distort, and low quality | Things to avoid |
| prompt | string | - | Text prompt for the animation |
| static_mask_url | string | - | URL of a mask image defining static (non-animated) areas |
| tail_image_url | string | - | URL of the image to use for the end of the video |

## Examples

**Professional portrait animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/business-portrait.jpg",
      "prompt": "The person nods slightly and smiles confidently, professional office setting",
      "aspect_ratio": "9:16",
      "duration": 5,
      "negative_prompt": "blur, distort, and low quality"
    }
  }'
```

**Selective animation with masking:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/still-life.jpg",
      "static_mask_url": "https://example.com/table-mask.png",
      "prompt": "The candle flame flickers, smoke rises gently, the table and objects remain still",
      "aspect_ratio": "16:9",
      "cfg_scale": 0.5
    }
  }'
```

**Transition between start and end frames:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/empty-canvas.jpg",
      "tail_image_url": "https://example.com/finished-painting.jpg",
      "prompt": "An invisible hand painting a landscape, brush strokes appearing on the canvas",
      "duration": 5
    }
  }'
```

## Related Models

- [Kling v1 | Standard | Image to Video](../kling-v1-standard-image-to-video/) - Standard tier (faster, more affordable)
- [Kling v2.1 | Pro | Image to Video](../kling-v2-1-pro-image-to-video/) - Latest generation Pro
- [Kling v1 | Pro | Text to Video](../kling-v1-pro-text-to-video/) - Pro text-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
