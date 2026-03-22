---
name: kling-o3-standard-image-to-video
description: "Kling | o3 | Standard | Image to Video. Animate images into videos with audio generation and multi-shot support. Triggers: image to video, kling, o3, animate, i2v"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | o3 | Standard | Image to Video

Animate static images into videos using Kling o3 Standard. Supports start and end frame images, multi-shot generation, and native audio generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "The waves gently crash against the shore as seagulls fly overhead",
      "image_url": "https://example.com/beach-photo.jpg",
      "duration": "5",
      "generate_audio": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| duration | string | 5 | Video duration in seconds (3-15s). enum: 3-15 |
| end_image_url | string | | URL of the end frame image (optional). Not used with multi-prompt. |
| generate_audio | boolean | true | Whether to generate native audio for the video. |
| image_url | string | | URL of the start frame image. |
| multi_prompt | array | | List of prompts for multi-shot video generation. |
| prompt | string | | Text prompt for video generation. Either prompt or multi_prompt required. |
| shot_type | string | customize | Multi-shot video generation type. enum: customize |

## Examples

**Animate a landscape photo:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Clouds drift slowly across the sky as the sun sets behind the mountains",
      "image_url": "https://example.com/mountain-sunset.jpg",
      "duration": "10",
      "generate_audio": true
    }
  }'
```

**Start and end frame animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A flower blooming from bud to full bloom",
      "image_url": "https://example.com/flower-bud.jpg",
      "end_image_url": "https://example.com/flower-bloom.jpg",
      "duration": "8",
      "generate_audio": false
    }
  }'
```

**Short animation without audio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "The character smiles and waves at the camera",
      "image_url": "https://example.com/character.png",
      "duration": "3",
      "generate_audio": false
    }
  }'
```

## Related Models

- [kling-o3-pro-image-to-video](../kling-o3-pro-image-to-video/) - Kling o3 Pro image to video
- [kling-o3-standard-text-to-video](../kling-o3-standard-text-to-video/) - Kling o3 Standard text to video
- [kling-v3-standard-image-to-video](../kling-v3-standard-image-to-video/) - Kling v3 Standard image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
