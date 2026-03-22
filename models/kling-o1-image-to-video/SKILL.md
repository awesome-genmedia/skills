---
name: kling-o1-image-to-video
description: "Kling O1 | Image to Video. Generate videos from start and end frame images. Triggers: image to video, kling, o1, video generation, animation, i2v"
allowed-tools: Bash(curl *), WebFetch
---

# Kling O1 | Image to Video

Generate videos from a starting image with optional end frame. Use @Image1 and @Image2 references in the prompt to control start and end frames.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o1-image-to-video",
    "version": "0.0.1",
    "input": {
      "start_image_url": "https://example.com/start-frame.jpg",
      "prompt": "camera slowly zooms in on @Image1, gentle motion",
      "duration": "5"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| duration | string | 5 | Duration of the video in seconds. enum: 5, 10 |
| end_image_url | string | | Image to use as the last frame of the video. Max file size: 10MB. |
| prompt | string | | Use @Image1 to reference the start frame, @Image2 to reference the end frame. |
| start_image_url | string | | Image to use as the first frame of the video. Max file size: 10MB. |

## Examples

**Simple image animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o1-image-to-video",
    "version": "0.0.1",
    "input": {
      "start_image_url": "https://example.com/forest.jpg",
      "prompt": "wind blows through the trees in @Image1, leaves rustling gently",
      "duration": "10"
    }
  }'
```

**Start-to-end frame transition:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o1-image-to-video",
    "version": "0.0.1",
    "input": {
      "start_image_url": "https://example.com/morning.jpg",
      "end_image_url": "https://example.com/evening.jpg",
      "prompt": "smooth transition from @Image1 morning scene to @Image2 evening scene",
      "duration": "5"
    }
  }'
```

## Related Models

- [Kling O1](../kling-o1/) - O1-tier image generation
- [Kling O1 | Video to Video Reference](../kling-o1-video-to-video-reference/) - Video-to-video with references
- [Kling O1 | Reference Image to Video](../kling-o1-reference-image-to-video/) - Reference-guided video generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
