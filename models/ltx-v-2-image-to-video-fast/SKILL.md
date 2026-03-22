---
name: ltx-v-2-image-to-video-fast
description: "Ltx v2 | Image to Video | Fast. Quickly animate images into videos with audio using LTX V2 Fast model. Triggers: ltx, image to video, fast video, animate image, ltx fast"
allowed-tools: Bash(curl *), WebFetch
---

# Ltx v2 | Image to Video | Fast

Quickly animate still images into videos with optional audio generation using the LTX V2 Fast model. Supports configurable duration (6-20 seconds), resolution up to 2160p, and adjustable frame rate.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ltx-v-2-image-to-video-fast",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/cityscape.jpg",
      "prompt": "Cars driving through the city streets at dusk with headlights glowing",
      "duration": 8,
      "resolution": "1080p",
      "generate_audio": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video. enum: 16:9 |
| duration | integer | 6 | The duration of the generated video in seconds (6-20 sec) |
| fps | integer | 25 | The frames per second of the generated video |
| generate_audio | boolean | true | Whether to generate audio for the generated video |
| image_url | string | | URL of the image to generate the video from |
| prompt | string | | The prompt to generate the video from |
| resolution | string | 1080p | The resolution of the generated video. enum: 1080p, 1440p, 2160p |

## Examples

**High-resolution animated scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ltx-v-2-image-to-video-fast",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/waterfall.jpg",
      "prompt": "Water cascades down the rocks with mist rising, birds flying overhead",
      "duration": 10,
      "resolution": "2160p",
      "fps": 30,
      "generate_audio": true
    }
  }'
```

**Silent video animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ltx-v-2-image-to-video-fast",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/painting.jpg",
      "prompt": "Subtle movement brings the painting to life, leaves sway gently",
      "duration": 6,
      "resolution": "1080p",
      "generate_audio": false
    }
  }'
```

## Related Models

- [ltx-v-2-image-to-video](../ltx-v-2-image-to-video/) - Standard speed image to video
- [ltx-v-2-text-to-video-fast](../ltx-v-2-text-to-video-fast/) - Fast text to video
- [ltx-v-2-text-to-video](../ltx-v-2-text-to-video/) - Standard text to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
