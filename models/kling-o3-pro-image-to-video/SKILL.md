---
name: kling-o3-pro-image-to-video
description: "Kling | o3 | Pro | Image to Video. Pro-quality image animation with start/end frames and multi-shot support. Triggers: image to video, kling, o3, pro, animate, i2v"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | o3 | Pro | Image to Video

Animate static images into high-quality videos using Kling o3 Pro. Supports start/end frame images, multi-shot generation, and native audio.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "The horse gallops across the open plain, mane flowing in the wind",
      "image_url": "https://example.com/horse-photo.jpg",
      "duration": "8",
      "generate_audio": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| duration | string | false | Video duration in seconds (3-15s). enum: 3-15 |
| end_image_url | string | | URL of the end frame image (optional). |
| generate_audio | boolean | false | Whether to generate native audio. |
| image_url | string | | URL of the start frame image. |
| multi_prompt | array | | List of prompts for multi-shot generation. |
| prompt | string | | Text prompt. Either prompt or multi_prompt required. |
| shot_type | string | customize | Multi-shot generation type. enum: customize |

## Examples

**Pro image animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "The city comes alive at night as streetlights flicker on and cars begin to move",
      "image_url": "https://example.com/city-dusk.jpg",
      "duration": "12",
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
    "model": "kling-o3-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "The ice melts away revealing a lush spring meadow",
      "image_url": "https://example.com/frozen-lake.jpg",
      "end_image_url": "https://example.com/spring-meadow.jpg",
      "duration": "10",
      "generate_audio": false
    }
  }'
```

**Quick animation clip:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "The cat pounces playfully at a butterfly",
      "image_url": "https://example.com/cat-garden.jpg",
      "duration": "5"
    }
  }'
```

## Related Models

- [kling-o3-standard-image-to-video](../kling-o3-standard-image-to-video/) - Standard tier image to video
- [kling-o3-pro-text-to-video](../kling-o3-pro-text-to-video/) - Pro text to video
- [kling-v3-pro-image-to-video](../kling-v3-pro-image-to-video/) - Kling v3 Pro image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
