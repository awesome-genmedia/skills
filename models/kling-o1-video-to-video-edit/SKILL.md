---
name: kling-o1-video-to-video-edit
description: "Kling O1 | Video to Video | Edit. Edit videos using prompts with element and image references. Triggers: video editing, kling, o1, video to video, edit"
allowed-tools: Bash(curl *), WebFetch
---

# Kling O1 | Video to Video | Edit

Edit existing videos using text prompts with support for element and image references. Apply transformations, add characters, and modify video content.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o1-video-to-video-edit",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/original.mp4",
      "prompt": "change the weather to snowy, add falling snowflakes"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| elements | array | | Elements (characters/objects) to include. Reference in prompt as @Element1, @Element2. |
| image_urls | array | | Reference images for style/appearance. Reference in prompt as @Image1, @Image2. |
| keep_audio | boolean | false | Whether to keep the original audio from the video. |
| prompt | string | | Use @Element1, @Element2 to reference elements and @Image1, @Image2 to reference images. |
| video_url | string | | Reference video URL. Only .mp4/.mov formats, 3-10 seconds duration, 720p+. |

## Examples

**Weather modification with audio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o1-video-to-video-edit",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/outdoor-scene.mp4",
      "prompt": "transform the scene into a rainy evening, add puddle reflections",
      "keep_audio": true
    }
  }'
```

**Style editing with reference images:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o1-video-to-video-edit",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/street.mp4",
      "prompt": "apply the color grading from @Image1, make it look cinematic",
      "image_urls": ["https://example.com/color-reference.jpg"]
    }
  }'
```

## Related Models

- [Kling O1 | Video to Video Reference](../kling-o1-video-to-video-reference/) - Video transformation with references
- [Kling O1 | Image to Video](../kling-o1-image-to-video/) - Generate video from images

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
