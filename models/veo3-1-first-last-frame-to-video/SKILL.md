---
name: veo3-1-first-last-frame-to-video
description: "Veo 3.1 | First Last Frame to Video. Generate videos from first and last frame images using Veo 3.1. Triggers: veo, first last frame, frame interpolation, veo 3.1, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Veo 3.1 | First Last Frame to Video

Generate videos by specifying the first and last frame images using Veo 3.1. The model creates smooth transitions between the two frames with optional audio generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-first-last-frame-to-video",
    "version": "0.0.1",
    "input": {
      "first_frame_url": "https://example.com/sunrise.jpg",
      "last_frame_url": "https://example.com/sunset.jpg",
      "prompt": "Time-lapse of a day passing over a mountain landscape from sunrise to sunset",
      "duration": 8,
      "resolution": "720p",
      "generate_audio": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio of the generated video. enum: 9:16, 16:9 |
| auto_fix | boolean | false | Whether to automatically fix prompts that fail content policy |
| duration | integer | 8 | The duration of the generated video in seconds |
| first_frame_url | string | | URL of the first frame of the video |
| generate_audio | boolean | true | Whether to generate audio. If false, 33% less credits used |
| last_frame_url | string | | URL of the last frame of the video |
| prompt | string | | The text prompt describing the video |
| resolution | string | 720p | Resolution of the generated video. enum: 720p, 1080p |

## Examples

**Scene transformation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-first-last-frame-to-video",
    "version": "0.0.1",
    "input": {
      "first_frame_url": "https://example.com/empty-room.jpg",
      "last_frame_url": "https://example.com/furnished-room.jpg",
      "prompt": "Furniture appears piece by piece as the room transforms from empty to fully decorated",
      "duration": 8,
      "resolution": "1080p",
      "generate_audio": true
    }
  }'
```

**Character movement transition:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-first-last-frame-to-video",
    "version": "0.0.1",
    "input": {
      "first_frame_url": "https://example.com/person-standing.jpg",
      "last_frame_url": "https://example.com/person-sitting.jpg",
      "prompt": "Person walks across the room and sits down at the desk",
      "duration": 8,
      "resolution": "720p",
      "generate_audio": false,
      "aspect_ratio": "16:9"
    }
  }'
```

## Related Models

- [veo3-1-first-last-frame-to-video-fast](../veo3-1-first-last-frame-to-video-fast/) - Fast first/last frame to video
- [veo3-1-image-to-video](../veo3-1-image-to-video/) - Single image to video
- [veo3-1-text-to-video](../veo3-1-text-to-video/) - Text to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
