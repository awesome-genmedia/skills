---
name: veo3-1-extend-video
description: "Veo 3.1 | Extend Video. Extend an existing video with AI-generated continuation. Triggers: extend video, video extension, veo, lengthen video, continue video"
allowed-tools: Bash(curl *), WebFetch
---

# Veo 3.1 | Extend Video

Extend an existing video with AI-generated continuation using Google's Veo 3.1 model. Supports audio generation, auto-fix for content policy issues, and 720p output resolution.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-extend-video",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/original-clip.mp4",
      "prompt": "The camera continues to pan right, revealing a bustling marketplace",
      "duration": "7",
      "generate_audio": true,
      "resolution": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | auto | The aspect ratio of the generated video. Options: `auto`, `16:9`, `9:16` |
| auto_fix | boolean | false | Whether to automatically attempt to fix prompts that fail content policy. |
| duration | string | 7 | The duration of the generated video. Options: `7` |
| generate_audio | boolean | true | Whether to generate audio for the video. |
| prompt | string | - | The text prompt describing how the video should be extended. |
| resolution | string | 720p | The resolution of the generated video. Options: `720p` |
| video_url | string | - | URL of the video to extend. The video should be 720p or 1080p resolution in 16:9 or 9:16. |

## Examples

**Basic video extension:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-extend-video",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/nature-scene.mp4",
      "prompt": "The bird takes flight from the branch and soars over the forest"
    }
  }'
```

**Extension with auto-fix and no audio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-extend-video",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/product-demo.mp4",
      "prompt": "The product rotates to show the back panel and side details",
      "auto_fix": true,
      "generate_audio": false,
      "aspect_ratio": "16:9"
    }
  }'
```

## Related Models

- [Veo 3.1 | Fast | Extend Video](../veo3-1-fast-extend-video/) - Faster video extension variant
- [Veo 3.1 | Text to Video](../veo3-1-text-to-video/) - Generate videos from text with Veo 3.1
- [Veo 3.1 | Image to Video](../veo3-1-image-to-video/) - Generate videos from images with Veo 3.1

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
