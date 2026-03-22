---
name: pika-v2-turbo-text-to-video
description: "Pika | v2 | Turbo | Text to Video. Fast text-to-video generation with Pika Turbo. Triggers: text to video, pika, turbo, fast, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Pika | v2 | Turbo | Text to Video

Generate videos from text prompts at turbo speed using Pika v2. Optimized for fast generation with configurable aspect ratio and resolution.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pika-v2-turbo-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "a rocket launching into space, dramatic clouds, epic cinematic",
      "aspect_ratio": "16:9",
      "duration": 5,
      "resolution": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video. enum: 16:9, 9:16, 1:1, 4:5, 5:4, 3:2, 2:3 |
| duration | integer | 5 | The duration of the generated video in seconds. |
| negative_prompt | string | | A negative prompt to guide the model. |
| prompt | string | | Text prompt describing the desired video. |
| resolution | string | 720p | The resolution of the generated video. enum: 720p, 1080p |
| seed | integer | | The seed for the random number generator. |

## Examples

**Action scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pika-v2-turbo-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "a sports car drifting around a mountain curve, sunset, dust trail",
      "aspect_ratio": "16:9",
      "duration": 5,
      "resolution": "1080p",
      "negative_prompt": "blurry, low quality, static"
    }
  }'
```

**Vertical content:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pika-v2-turbo-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "raindrops falling on a window, cozy interior lights blurred behind",
      "aspect_ratio": "9:16",
      "duration": 5,
      "resolution": "720p",
      "seed": 42
    }
  }'
```

## Related Models

- [Pika | v2 | Turbo | Image to Video](../pika-v2-turbo-image-to-video/) - Turbo image-to-video
- [Pika | v2.2 | Text to Video](../pika-v2-2-text-to-video/) - Higher quality text-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
