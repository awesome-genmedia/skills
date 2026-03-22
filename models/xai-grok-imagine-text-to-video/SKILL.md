---
name: xai-grok-imagine-text-to-video
description: "XAI | Grok Imagine | Text to Video. Generate videos from text with configurable aspect ratio, duration, and resolution. Triggers: text to video, grok, xai, video generation, t2v"
allowed-tools: Bash(curl *), WebFetch
---

# XAI | Grok Imagine | Text to Video

Generate videos from text descriptions using xAI's Grok Imagine with configurable aspect ratios, duration, and up to 720p resolution.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-imagine-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A hot air balloon rising over a lavender field at sunrise",
      "duration": 6,
      "aspect_ratio": "16:9",
      "resolution": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio. enum: 16:9, 4:3, 3:2, 1:1, 2:3, 3:4, 9:16 |
| duration | integer | 6 | Video duration in seconds. |
| prompt | string | | Text description of the desired video. |
| resolution | string | 720p | Output resolution. enum: 480p, 720p |

## Examples

**Cinematic landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-imagine-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A thunderstorm rolling across a vast prairie, lightning illuminating the clouds",
      "duration": 8,
      "aspect_ratio": "16:9",
      "resolution": "720p"
    }
  }'
```

**Vertical short-form content:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-imagine-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A mixologist crafting a cocktail with dramatic flair, pouring from a height",
      "duration": 5,
      "aspect_ratio": "9:16",
      "resolution": "720p"
    }
  }'
```

**Quick square preview:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-imagine-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A goldfish swimming in a crystal-clear bowl with bubbles rising",
      "duration": 4,
      "aspect_ratio": "1:1",
      "resolution": "480p"
    }
  }'
```

## Related Models

- [xai-grok-imagine-image-to-video](../xai-grok-imagine-image-to-video/) - Grok image to video
- [xai-grok-imagine-edit-video](../xai-grok-imagine-edit-video/) - Grok video editing
- [xai-grok-imagine-text-to-image](../xai-grok-imagine-text-to-image/) - Grok text to image

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
