---
name: veo3-1-first-last-frame-to-video-fast
description: "Veo 3.1 | First Last Frame to Video | Fast. Quickly generate videos from first and last frames using Veo 3.1 Fast. Triggers: veo, first last frame, fast video, frame interpolation, veo fast"
allowed-tools: Bash(curl *), WebFetch
---

# Veo 3.1 | First Last Frame to Video | Fast

Quickly generate videos by specifying first and last frame images using the Veo 3.1 Fast model. Creates smooth transitions with optional audio, optimized for speed.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-first-last-frame-to-video-fast",
    "version": "0.0.1",
    "input": {
      "first_frame_url": "https://example.com/closed-flower.jpg",
      "last_frame_url": "https://example.com/open-flower.jpg",
      "prompt": "A flower blooms open in a time-lapse, petals unfurling gracefully",
      "duration": "8",
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
| duration | string | 8 | The duration of the generated video in seconds. enum: 4, 6, 8 |
| first_frame_url | string | | URL of the first frame of the video |
| generate_audio | boolean | true | Whether to generate audio. If false, 33% less credits used |
| last_frame_url | string | | URL of the last frame of the video |
| prompt | string | | The text prompt describing the video |
| resolution | string | 720p | Resolution of the generated video. enum: 720p, 1080p |

## Examples

**Short transition clip:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-first-last-frame-to-video-fast",
    "version": "0.0.1",
    "input": {
      "first_frame_url": "https://example.com/day-city.jpg",
      "last_frame_url": "https://example.com/night-city.jpg",
      "prompt": "City transitions from day to night as lights turn on one by one",
      "duration": "4",
      "resolution": "1080p",
      "generate_audio": true
    }
  }'
```

**Vertical format transformation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-first-last-frame-to-video-fast",
    "version": "0.0.1",
    "input": {
      "first_frame_url": "https://example.com/before-makeover.jpg",
      "last_frame_url": "https://example.com/after-makeover.jpg",
      "prompt": "Dramatic makeover transformation reveal",
      "duration": "6",
      "resolution": "720p",
      "aspect_ratio": "9:16",
      "generate_audio": false
    }
  }'
```

## Related Models

- [veo3-1-first-last-frame-to-video](../veo3-1-first-last-frame-to-video/) - Standard quality first/last frame to video
- [veo3-1-image-to-video-fast](../veo3-1-image-to-video-fast/) - Fast image to video
- [veo3-1-text-to-video-fast](../veo3-1-text-to-video-fast/) - Fast text to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
