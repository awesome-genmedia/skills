---
name: kling-o1-reference-image-to-video
description: "Kling O1 | Reference Image to Video. Generate videos using reference images and elements. Triggers: reference to video, kling, o1, video generation, character consistency"
allowed-tools: Bash(curl *), WebFetch
---

# Kling O1 | Reference Image to Video

Generate videos using reference images and elements for consistent character/object appearance. Reference elements with @Element1 and images with @Image1 in prompts.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o1-reference-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "@Element1 walks through a busy marketplace, cinematic",
      "elements": [{"image_url": "https://example.com/character.jpg"}],
      "aspect_ratio": "16:9",
      "duration": 5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video frame. enum: 16:9, 9:16, 1:1 |
| duration | integer | 5 | Duration of the video in seconds. |
| elements | array | | Elements (characters/objects) to include in the video. |
| image_urls | array | | Reference images for style/appearance. |
| prompt | string | | Take @Element1, @Element2 to reference elements and @Image1, @Image2 to reference images. |

## Examples

**Character animation with reference:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o1-reference-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "@Element1 dances gracefully on stage under spotlight",
      "elements": [{"image_url": "https://example.com/dancer.jpg"}],
      "aspect_ratio": "9:16",
      "duration": 10
    }
  }'
```

**Multi-element scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o1-reference-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "@Element1 and @Element2 meeting at a park, friendly conversation",
      "elements": [{"image_url": "https://example.com/person1.jpg"}, {"image_url": "https://example.com/person2.jpg"}],
      "image_urls": ["https://example.com/park-style.jpg"],
      "aspect_ratio": "16:9",
      "duration": 5
    }
  }'
```

## Related Models

- [Kling O1](../kling-o1/) - O1-tier image generation
- [Kling O1 | Image to Video](../kling-o1-image-to-video/) - Direct image-to-video generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
