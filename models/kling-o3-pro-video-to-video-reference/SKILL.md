---
name: kling-o3-pro-video-to-video-reference
description: "Kling | o3 | Standard | Video to Video | Reference. Transform videos using reference images and elements with prompt control. Triggers: video to video, kling, o3, reference, video edit, v2v"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | o3 | Standard | Video to Video | Reference

Transform existing videos using reference images for style and appearance. Reference images and elements in your prompt for precise control over the output.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-pro-video-to-video-reference",
    "version": "0.0.1",
    "input": {
      "prompt": "Apply the style of @Image1 to @Video1, keeping the motion intact",
      "video_url": "https://example.com/original-video.mp4",
      "image_urls": ["https://example.com/style-reference.jpg"],
      "duration": "5",
      "aspect_ratio": "16:9",
      "keep_audio": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio. enum: 16:9, 9:16, 1:1 |
| duration | string | 5 | Video duration in seconds (3-15s). enum: 3-15 |
| elements | array | false | Elements (characters/objects) to include. Reference as @Element1, @Element2. |
| image_urls | array | false | Reference images for style/appearance. Reference as @Image1, @Image2. |
| keep_audio | boolean | true | Whether to keep the original audio from the reference video. |
| prompt | string | false | Text prompt. Reference video as @Video1. |
| shot_type | string | customize | Multi-shot video generation type. enum: customize |
| video_url | string | false | Reference video URL. Only .mp4/.mov, 3-10s duration, 720-2160px. |

## Examples

**Style transfer from reference image:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-pro-video-to-video-reference",
    "version": "0.0.1",
    "input": {
      "prompt": "Transform @Video1 to match the anime style shown in @Image1",
      "video_url": "https://example.com/walking-scene.mp4",
      "image_urls": ["https://example.com/anime-reference.jpg"],
      "duration": "8",
      "aspect_ratio": "16:9"
    }
  }'
```

**Video transformation without audio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-pro-video-to-video-reference",
    "version": "0.0.1",
    "input": {
      "prompt": "Recreate @Video1 with a cyberpunk aesthetic using @Image1 as color reference",
      "video_url": "https://example.com/city-drive.mp4",
      "image_urls": ["https://example.com/cyberpunk-palette.jpg"],
      "duration": "10",
      "keep_audio": false
    }
  }'
```

## Related Models

- [kling-o3-standard-video-to-video-reference](../kling-o3-standard-video-to-video-reference/) - Standard tier video to video reference
- [kling-o3-pro-video-to-video-edit](../kling-o3-pro-video-to-video-edit/) - Pro video to video editing
- [kling-o3-pro-text-to-video](../kling-o3-pro-text-to-video/) - Pro text to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
