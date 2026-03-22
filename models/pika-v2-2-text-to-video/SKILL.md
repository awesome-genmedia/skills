---
name: pika-v2-2-text-to-video
description: "Pika | v2.2 | Text to Video. Generate videos from text prompts with Pika v2.2. Triggers: text to video, pika, video generation, t2v"
allowed-tools: Bash(curl *), WebFetch
---

# Pika | v2.2 | Text to Video

Generate videos from text prompts using Pika v2.2 with configurable aspect ratio, duration, and resolution up to 1080p.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pika-v2-2-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "a golden retriever running through a field of wildflowers",
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
| negative_prompt | string | ugly, bad, terrible | A negative prompt to guide the model. |
| prompt | string | | Text prompt describing the desired video. |
| resolution | string | 720p | The resolution of the generated video. enum: 1080p, 720p |
| seed | integer | | The seed for the random number generator. |

## Examples

**Cinematic scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pika-v2-2-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "cinematic drone shot over a medieval castle at dawn, fog rolling in",
      "aspect_ratio": "16:9",
      "duration": 5,
      "resolution": "1080p",
      "negative_prompt": "blurry, shaky, low quality, distorted"
    }
  }'
```

**Vertical social media content:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pika-v2-2-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "a colorful smoothie being blended, ingredients falling in slow motion",
      "aspect_ratio": "9:16",
      "duration": 5,
      "resolution": "720p",
      "seed": 42
    }
  }'
```

## Related Models

- [Pika | v2.2 | Image to Video](../pika-v2-2-image-to-video/) - Image-to-video generation
- [Pika | v2.2 | PikaScenes](../pika-v2-2-pikascenes/) - Multi-image scene composition
- [Pika | v2 | Turbo | Text to Video](../pika-v2-turbo-text-to-video/) - Faster text-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
