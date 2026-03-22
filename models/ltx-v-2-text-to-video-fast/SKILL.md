---
name: ltx-v-2-text-to-video-fast
description: "Ltx v2 | Text to Video | Fast. Quickly generate videos from text prompts with audio using LTX V2 Fast model. Triggers: ltx, text to video, fast video, video generation, ltx fast"
allowed-tools: Bash(curl *), WebFetch
---

# Ltx v2 | Text to Video | Fast

Quickly generate videos from text descriptions with optional audio using the LTX V2 Fast model. Supports 6-20 second duration, resolution up to 2160p, and adjustable frame rate.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ltx-v-2-text-to-video-fast",
    "version": "0.0.1",
    "input": {
      "prompt": "A spaceship launching from a desert planet with twin suns in the sky",
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
| prompt | string | | The prompt to generate the video from |
| resolution | string | 1080p | The resolution of the generated video. enum: 1080p, 1440p, 2160p |

## Examples

**High-resolution cinematic scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ltx-v-2-text-to-video-fast",
    "version": "0.0.1",
    "input": {
      "prompt": "A medieval knight riding through a misty forest at dawn, cinematic lighting, epic atmosphere",
      "duration": 12,
      "resolution": "2160p",
      "fps": 30,
      "generate_audio": true
    }
  }'
```

**Quick silent clip:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ltx-v-2-text-to-video-fast",
    "version": "0.0.1",
    "input": {
      "prompt": "Abstract colorful liquid swirling and mixing in slow motion",
      "duration": 6,
      "resolution": "1080p",
      "generate_audio": false
    }
  }'
```

## Related Models

- [ltx-v-2-text-to-video](../ltx-v-2-text-to-video/) - Standard speed text to video
- [ltx-v-2-image-to-video-fast](../ltx-v-2-image-to-video-fast/) - Fast image to video
- [ltx-v-2-image-to-video](../ltx-v-2-image-to-video/) - Standard image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
