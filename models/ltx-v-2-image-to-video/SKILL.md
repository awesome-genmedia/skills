---
name: ltx-v-2-image-to-video
description: "Ltx v2 | Image to Video. Animate images into videos with audio using the LTX V2 model. Triggers: ltx, image to video, animate image, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Ltx v2 | Image to Video

Animate still images into videos with optional audio generation using the LTX V2 model. Supports configurable duration, resolution up to 2160p, and adjustable frame rate.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ltx-v-2-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/beach-sunset.jpg",
      "prompt": "Waves gently rolling onto the shore as the sun sets on the horizon",
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
| duration | integer | 6 | The duration of the generated video in seconds |
| fps | integer | 25 | The frames per second of the generated video |
| generate_audio | boolean | true | Whether to generate audio for the generated video |
| image_url | string | | URL of the image to generate the video from |
| prompt | string | | The prompt to generate the video from |
| resolution | string | 1080p | The resolution of the generated video. enum: 1080p, 1440p, 2160p |

## Examples

**4K video with audio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ltx-v-2-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/forest-path.jpg",
      "prompt": "Walking through the forest path with leaves rustling and birds chirping",
      "duration": 10,
      "resolution": "2160p",
      "fps": 30,
      "generate_audio": true
    }
  }'
```

**Quick animation without audio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ltx-v-2-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait-photo.jpg",
      "prompt": "Person slowly looks up and smiles warmly",
      "duration": 6,
      "resolution": "1080p",
      "generate_audio": false
    }
  }'
```

## Related Models

- [ltx-v-2-image-to-video-fast](../ltx-v-2-image-to-video-fast/) - Fast image to video
- [ltx-v-2-text-to-video](../ltx-v-2-text-to-video/) - Text to video
- [ltx-v-2-text-to-video-fast](../ltx-v-2-text-to-video-fast/) - Fast text to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
