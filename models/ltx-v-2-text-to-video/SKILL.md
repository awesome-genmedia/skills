---
name: ltx-v-2-text-to-video
description: "Ltx v2 | Text to Video. Generate videos from text prompts with audio using the LTX V2 model. Triggers: ltx, text to video, video generation, ltx video"
allowed-tools: Bash(curl *), WebFetch
---

# Ltx v2 | Text to Video

Generate videos from text descriptions with optional audio using the LTX V2 model. Supports configurable duration, resolution up to 2160p, and adjustable frame rate.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ltx-v-2-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A cozy coffee shop on a rainy day, steam rising from a cup, people chatting in the background",
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
| prompt | string | | The prompt to generate the video from |
| resolution | string | 1080p | The resolution of the generated video. enum: 1080p, 1440p, 2160p |

## Examples

**4K nature video with sound:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ltx-v-2-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A river flowing through an autumn forest with leaves falling from the trees",
      "duration": 10,
      "resolution": "2160p",
      "fps": 30,
      "generate_audio": true
    }
  }'
```

**Short silent animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ltx-v-2-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Geometric shapes transforming and morphing in a dark void, neon colors",
      "duration": 6,
      "resolution": "1440p",
      "generate_audio": false
    }
  }'
```

## Related Models

- [ltx-v-2-text-to-video-fast](../ltx-v-2-text-to-video-fast/) - Fast text to video
- [ltx-v-2-image-to-video](../ltx-v-2-image-to-video/) - Image to video
- [ltx-v-2-image-to-video-fast](../ltx-v-2-image-to-video-fast/) - Fast image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
