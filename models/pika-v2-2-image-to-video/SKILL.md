---
name: pika-v2-2-image-to-video
description: "Pika | v2.2 | Image to Video. Animate images into videos with Pika v2.2. Triggers: image to video, pika, animation, i2v, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Pika | v2.2 | Image to Video

Animate a single image into a video using Pika v2.2. Control duration, resolution, and use negative prompts to guide the output quality.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pika-v2-2-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/sunset-beach.jpg",
      "prompt": "waves gently rolling onto the shore, seagulls flying",
      "duration": 5,
      "resolution": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| duration | integer | 5 | The duration of the generated video in seconds. |
| image_url | string | | URL of the image to use as the first frame. |
| negative_prompt | string | | A negative prompt to guide the model. |
| prompt | string | | Text prompt describing the desired motion. |
| resolution | string | 720p | The resolution of the generated video. enum: 720p, 1080p |
| seed | integer | | The seed for the random number generator. |

## Examples

**1080p animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pika-v2-2-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "prompt": "person slowly smiles and turns head slightly",
      "duration": 5,
      "resolution": "1080p",
      "negative_prompt": "blurry, distorted face, low quality"
    }
  }'
```

**Nature scene animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pika-v2-2-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/waterfall.jpg",
      "prompt": "water cascading down, mist rising, birds flying past",
      "duration": 5,
      "resolution": "720p",
      "seed": 42
    }
  }'
```

## Related Models

- [Pika | v2.2 | Text to Video](../pika-v2-2-text-to-video/) - Text-only video generation
- [Pika | v2.2 | PikaScenes](../pika-v2-2-pikascenes/) - Multi-image scene composition
- [Pika | v2 | Turbo | Image to Video](../pika-v2-turbo-image-to-video/) - Faster image-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
