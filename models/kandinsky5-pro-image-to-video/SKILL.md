---
name: kandinsky5-pro-image-to-video
description: "Kandinsky 5 | Pro | Image to Video. Generate videos from images using Kandinsky 5 Pro. Triggers: image to video, video generation, kandinsky, animate image"
allowed-tools: Bash(curl *), WebFetch
---

# Kandinsky 5 | Pro | Image to Video

Generate videos from reference images using the Kandinsky 5 Pro model. Supports up to 1024p resolution with acceleration options for faster generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kandinsky5-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A gentle breeze moves through the flowers in the garden",
      "image_url": "https://example.com/garden.jpg",
      "resolution": "512P",
      "num_inference_steps": 28
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | regular | Acceleration level for faster generation. Options: `none`, `regular` |
| image_url | string | - | The URL of the image to use as a reference for video generation. |
| num_inference_steps | integer | 28 | The number of inference steps. |
| prompt | string | - | The prompt to generate the video from. |
| resolution | string | 512P | Video resolution. Options: `512P`, `1024P` |

## Examples

**Standard resolution video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kandinsky5-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Waves gently lapping against the shore",
      "image_url": "https://example.com/beach.jpg"
    }
  }'
```

**High resolution with no acceleration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kandinsky5-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A cat stretching and yawning on a window sill, sunlight streaming in",
      "image_url": "https://example.com/cat-on-sill.jpg",
      "resolution": "1024P",
      "acceleration": "none",
      "num_inference_steps": 35
    }
  }'
```

## Related Models

- [Kandinsky 5 | Pro | Text to Video](../kandinsky5-pro-text-to-video/) - Generate videos from text with Kandinsky 5
- [Wan | v2.6 | Image to Video](../wan-v2-6-image-to-video/) - Wan-based image to video generation
- [Motion | Fast](../motion-fast/) - Fast motion video generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
