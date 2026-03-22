---
name: sora-2-text-to-video
description: "Sora 2 | Text to Video. Generate videos from text prompts using OpenAI Sora 2. Triggers: sora, text to video, sora 2, video generation, openai sora"
allowed-tools: Bash(curl *), WebFetch
---

# Sora 2 | Text to Video

Generate videos from text descriptions using OpenAI Sora 2. Supports configurable duration and aspect ratio for versatile video output.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sora-2-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A golden retriever puppy chasing a red ball across a green lawn in slow motion, sunny day",
      "duration": 4,
      "aspect_ratio": "16:9"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video. enum: 9:16, 16:9 |
| duration | integer | 4 | Duration of the generated video in seconds |
| prompt | string | | The text prompt describing the video |

## Examples

**Cinematic landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sora-2-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Northern lights dancing across an Arctic sky above a frozen lake, slow camera pan, 4K quality",
      "duration": 4,
      "aspect_ratio": "16:9"
    }
  }'
```

**Vertical format content:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sora-2-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A latte being prepared at a coffee counter, overhead shot, creamy foam art forming",
      "duration": 4,
      "aspect_ratio": "9:16"
    }
  }'
```

## Related Models

- [sora-2-text-to-video-pro](../sora-2-text-to-video-pro/) - Pro tier with resolution control
- [sora-2-image-to-video](../sora-2-image-to-video/) - Image to video
- [sora-2-image-to-video-pro](../sora-2-image-to-video-pro/) - Pro image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
