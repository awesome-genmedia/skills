---
name: veo3-1-image-to-video
description: "Veo 3.1 | Image to Video. Animate images into videos with audio using Google Veo 3.1. Triggers: veo, image to video, veo 3.1, animate image, google veo"
allowed-tools: Bash(curl *), WebFetch
---

# Veo 3.1 | Image to Video

Animate still images into dynamic videos with optional audio generation using Google Veo 3.1. Supports configurable duration, resolution, and automatic content policy fixing.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/landscape-photo.jpg",
      "prompt": "Camera slowly pans across the landscape as golden hour light shifts across the hills",
      "duration": 8,
      "resolution": "720p",
      "generate_audio": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video. enum: 9:16, 16:9 |
| auto_fix | boolean | false | Whether to automatically fix prompts that fail content policy |
| duration | integer | 8 | The duration of the generated video in seconds |
| generate_audio | boolean | true | Whether to generate audio. If false, 33% less credits used |
| image_url | string | | URL of the input image to animate (720p or higher recommended) |
| prompt | string | | The text prompt describing the video |
| resolution | string | 720p | Resolution of the generated video. enum: 720p, 1080p |

## Examples

**1080p animated portrait:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "prompt": "The person turns to the camera and speaks warmly about their day",
      "duration": 8,
      "resolution": "1080p",
      "generate_audio": true,
      "aspect_ratio": "9:16"
    }
  }'
```

**Silent landscape animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/ocean-cliff.jpg",
      "prompt": "Waves crash against the cliff, seagulls fly overhead in slow motion",
      "duration": 8,
      "resolution": "720p",
      "generate_audio": false,
      "auto_fix": true
    }
  }'
```

## Related Models

- [veo3-1-image-to-video-fast](../veo3-1-image-to-video-fast/) - Fast image to video
- [veo3-1-text-to-video](../veo3-1-text-to-video/) - Text to video
- [veo3-1-first-last-frame-to-video](../veo3-1-first-last-frame-to-video/) - First/last frame to video
- [veo3-1-reference-to-video](../veo3-1-reference-to-video/) - Reference to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
