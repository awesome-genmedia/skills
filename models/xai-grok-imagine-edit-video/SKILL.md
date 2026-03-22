---
name: xai-grok-imagine-edit-video
description: "XAI | Grok Imagine | Edit Video. Edit videos with text prompts using xAI Grok Imagine. Triggers: video edit, grok, xai, edit video, modify video"
allowed-tools: Bash(curl *), WebFetch
---

# XAI | Grok Imagine | Edit Video

Edit existing videos using text descriptions with xAI's Grok Imagine. Supports up to 720p output resolution.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-imagine-edit-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Make the scene look like it is during a thunderstorm with rain",
      "video_url": "https://example.com/outdoor-scene.mp4",
      "resolution": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| prompt | string | | Text description of the desired edit. |
| resolution | string | 720p | Resolution of the output video. enum: 480p, 720p |
| video_url | string | | URL of the input video to edit. Video will be resized to max 810,000 pixel area. |

## Examples

**Add weather effects:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-imagine-edit-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Add heavy snowfall to the entire scene",
      "video_url": "https://example.com/city-street.mp4",
      "resolution": "720p"
    }
  }'
```

**Style transformation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-imagine-edit-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Transform into a vintage black and white film with grain",
      "video_url": "https://example.com/modern-clip.mp4",
      "resolution": "480p"
    }
  }'
```

## Related Models

- [xai-grok-imagine-image-to-video](../xai-grok-imagine-image-to-video/) - Grok image to video
- [xai-grok-imagine-text-to-video](../xai-grok-imagine-text-to-video/) - Grok text to video
- [xai-grok-imagine-image-edit](../xai-grok-imagine-image-edit/) - Grok image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
