---
name: kling-v2-6-pro-image-to-video
description: "Kling | v2.6 | Pro | Image to Video. Generate videos from images with optional end frame and audio. Triggers: image to video, kling, video generation, animation, i2v"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | v2.6 | Pro | Image to Video

Generate high-quality videos from a starting image with optional end frame and native audio generation. Supports 5 and 10-second durations with Chinese and English voice support.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-6-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/landscape.jpg",
      "prompt": "camera slowly pans across the landscape with gentle wind",
      "duration": "5",
      "generate_audio": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| duration | string | 5 | The duration of the generated video in seconds. enum: 5, 10 |
| end_image_url | string | | URL of the image to be used for the end of the video. |
| generate_audio | boolean | true | Whether to generate native audio for the video. Supports Chinese and English voices. |
| image_url | string | | URL of the image to be used for the video. |
| negative_prompt | string | blur, distort, and low quality | Negative prompt to avoid unwanted elements. |
| prompt | string | | Text prompt describing the desired video motion. |

## Examples

**Simple image animation with audio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-6-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/ocean-sunset.jpg",
      "prompt": "waves gently crashing on the shore, seagulls flying",
      "duration": "10",
      "generate_audio": true
    }
  }'
```

**Start-to-end frame transition:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-6-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/day-scene.jpg",
      "end_image_url": "https://example.com/night-scene.jpg",
      "prompt": "time-lapse of day transitioning to night",
      "duration": "5",
      "negative_prompt": "blur, distort, and low quality, flickering"
    }
  }'
```

## Related Models

- [Kling | v2.6 | Pro | Text to Video](../kling-v2-6-pro-text-to-video/) - Text-only video generation
- [Kling O1 | Image to Video](../kling-o1-image-to-video/) - O1-tier image-to-video generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
