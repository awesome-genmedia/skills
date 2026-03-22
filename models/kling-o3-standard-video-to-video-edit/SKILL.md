---
name: kling-o3-standard-video-to-video-edit
description: "Kling | o3 | Standard | Video to Video | Edit. Edit videos with text prompts and reference images at standard quality. Triggers: video edit, kling, o3, standard, video to video, v2v"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | o3 | Standard | Video to Video | Edit

Edit existing videos using text prompts at standard quality. Support for reference images and element binding for editing control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-standard-video-to-video-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Add falling autumn leaves throughout @Video1",
      "video_url": "https://example.com/park-footage.mp4",
      "keep_audio": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| elements | array | false | Elements (characters/objects) to include. Reference as @Element1, @Element2. |
| image_urls | array | false | Reference images for style/appearance. Reference as @Image1, @Image2. |
| keep_audio | boolean | true | Whether to keep the original audio from the reference video. |
| prompt | string | false | Text prompt for editing. Reference video as @Video1. |
| shot_type | string | customize | Multi-shot video generation type. enum: customize |
| video_url | string | false | Reference video URL. Only .mp4/.mov, 3-10s duration, 720-2160px. |

## Examples

**Add visual effects:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-standard-video-to-video-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Add magical sparkle effects and a rainbow in @Video1",
      "video_url": "https://example.com/garden-scene.mp4",
      "keep_audio": true
    }
  }'
```

**Environment change:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-standard-video-to-video-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Change the background in @Video1 to a futuristic city skyline",
      "video_url": "https://example.com/person-walking.mp4",
      "image_urls": ["https://example.com/futuristic-city.jpg"],
      "keep_audio": false
    }
  }'
```

## Related Models

- [kling-o3-pro-video-to-video-edit](../kling-o3-pro-video-to-video-edit/) - Pro tier video editing
- [kling-o3-standard-video-to-video-reference](../kling-o3-standard-video-to-video-reference/) - Standard video to video reference
- [xai-grok-imagine-edit-video](../xai-grok-imagine-edit-video/) - Grok video editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
