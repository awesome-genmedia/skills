---
name: kling-o3-pro-reference-to-video
description: "Kling | o3 | Pro | Referance to Video. Pro-quality video generation from reference images with start/end frame control. Triggers: reference to video, kling, o3, pro, reference, video"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | o3 | Pro | Reference to Video

Generate high-quality videos using reference images for style with start/end frame control. Pro tier delivers superior quality for reference-guided generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-pro-reference-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A warrior marching through a battlefield in the style of @Image1",
      "image_urls": ["https://example.com/epic-painting.jpg"],
      "start_image_url": "https://example.com/warrior-start.jpg",
      "duration": "8",
      "aspect_ratio": "16:9"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio. enum: 16:9, 9:16, 1:1 |
| duration | string | 5 | Video duration in seconds (3-15s). enum: 3-15 |
| elements | array | false | Elements (characters/objects). Reference as @Element1, @Element2. |
| end_image_url | string | false | Image for the last frame. |
| generate_audio | boolean | false | Whether to generate native audio. |
| image_urls | array | false | Reference images. Reference as @Image1, @Image2. |
| multi_prompt | array | false | List of prompts for multi-shot generation. |
| prompt | string | false | Text prompt. Either prompt or multi_prompt required. |
| shot_type | string | customize | Multi-shot generation type. enum: customize |
| start_image_url | string | false | Image for the first frame. |

## Examples

**Reference-guided cinematic video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-pro-reference-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A fantasy dragon flying over mountains in the visual style of @Image1",
      "image_urls": ["https://example.com/fantasy-art.jpg"],
      "duration": "12",
      "aspect_ratio": "16:9",
      "generate_audio": true
    }
  }'
```

**Transition between frames with reference style:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-pro-reference-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A smooth scene transition from forest to ocean in @Image1 painterly style",
      "image_urls": ["https://example.com/impressionist.jpg"],
      "start_image_url": "https://example.com/forest.jpg",
      "end_image_url": "https://example.com/ocean.jpg",
      "duration": "10"
    }
  }'
```

## Related Models

- [kling-o3-standard-reference-to-video](../kling-o3-standard-reference-to-video/) - Standard tier reference to video
- [kling-o3-pro-text-to-video](../kling-o3-pro-text-to-video/) - Pro text to video
- [kling-o3-pro-image-to-video](../kling-o3-pro-image-to-video/) - Pro image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
