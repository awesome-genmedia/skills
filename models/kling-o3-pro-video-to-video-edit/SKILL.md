---
name: kling-o3-pro-video-to-video-edit
description: "Kling | o3 | Pro | Video to Video | Edit. Edit videos with text prompts, reference images, and elements at pro quality. Triggers: video edit, kling, o3, pro, video to video, v2v"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | o3 | Pro | Video to Video | Edit

Edit existing videos using text prompts with pro-quality output. Support for reference images and element binding for precise editing control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-pro-video-to-video-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Change the weather in @Video1 to heavy snowfall",
      "video_url": "https://example.com/outdoor-scene.mp4",
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

**Weather change edit:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-pro-video-to-video-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Turn the daytime scene in @Video1 into a dramatic nighttime with moonlight",
      "video_url": "https://example.com/park-walk.mp4",
      "keep_audio": true
    }
  }'
```

**Style edit with reference image:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-pro-video-to-video-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Apply the color grading from @Image1 to @Video1",
      "video_url": "https://example.com/street-footage.mp4",
      "image_urls": ["https://example.com/warm-tones.jpg"],
      "keep_audio": false
    }
  }'
```

## Related Models

- [kling-o3-standard-video-to-video-edit](../kling-o3-standard-video-to-video-edit/) - Standard tier video editing
- [kling-o3-pro-video-to-video-reference](../kling-o3-pro-video-to-video-reference/) - Pro video to video reference
- [xai-grok-imagine-edit-video](../xai-grok-imagine-edit-video/) - Grok video editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
