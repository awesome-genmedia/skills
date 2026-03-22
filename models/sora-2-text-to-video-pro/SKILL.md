---
name: sora-2-text-to-video-pro
description: "Sora 2 | Text to Video | Pro. Generate high-quality videos from text prompts using OpenAI Sora 2 Pro. Triggers: sora, text to video, sora 2, sora pro, video generation, openai sora"
allowed-tools: Bash(curl *), WebFetch
---

# Sora 2 | Text to Video | Pro

Generate high-quality videos from text descriptions using OpenAI Sora 2 Pro. Supports configurable duration, aspect ratio, and resolution up to 1080p.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sora-2-text-to-video-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "A professional chef plating a gourmet dish in a Michelin-star restaurant kitchen, slow motion, warm lighting",
      "duration": 4,
      "aspect_ratio": "16:9",
      "resolution": "1080p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video. enum: 9:16, 16:9 |
| duration | integer | 4 | Duration of the generated video in seconds |
| prompt | string | | The text prompt describing the video |
| resolution | string | 720p | The resolution of the generated video. enum: 720p, 1080p |

## Examples

**Cinematic widescreen scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sora-2-text-to-video-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "A vintage train steaming through a snowy mountain pass at golden hour, aerial view, cinematic quality",
      "duration": 4,
      "resolution": "1080p",
      "aspect_ratio": "16:9"
    }
  }'
```

**Vertical social media content:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sora-2-text-to-video-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "Colorful paint being poured onto a canvas, abstract art creation process, close-up shot",
      "duration": 4,
      "aspect_ratio": "9:16",
      "resolution": "720p"
    }
  }'
```

## Related Models

- [sora-2-image-to-video-pro](../sora-2-image-to-video-pro/) - Pro image to video
- [sora-2-text-to-video](../sora-2-text-to-video/) - Standard text to video
- [sora-2-image-to-video](../sora-2-image-to-video/) - Standard image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
