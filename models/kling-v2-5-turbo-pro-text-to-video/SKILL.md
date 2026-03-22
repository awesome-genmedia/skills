---
name: kling-v2-5-turbo-pro-text-to-video
description: "Kling v2.5 | Turbo | Pro | Text to Video. Generate videos from text prompts using Kling v2.5 Turbo Pro. Triggers: kling, text to video, kling pro, kling turbo, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Kling v2.5 | Turbo | Pro | Text to Video

Generate high-quality videos from text descriptions using the Kling v2.5 Turbo Pro model. Supports aspect ratio control, CFG scale for prompt adherence, and negative prompts for quality control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-5-turbo-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A majestic eagle soaring above snow-capped mountains at golden hour, cinematic aerial shot",
      "aspect_ratio": "16:9",
      "duration": "5",
      "cfg_scale": 0.5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video. enum: 16:9, 9:16, 1:1 |
| cfg_scale | number | 0.5 | CFG (Classifier Free Guidance) scale for prompt adherence |
| duration | string | 5 | The duration of the generated video in seconds. enum: 5, 10 |
| negative_prompt | string | blur, distort, and low quality | Negative prompt to avoid unwanted content |
| prompt | string | | Text prompt describing the desired video |

## Examples

**Square format social media video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-5-turbo-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Colorful fireworks exploding over a city skyline reflected in a calm river",
      "aspect_ratio": "1:1",
      "duration": "5",
      "cfg_scale": 0.6
    }
  }'
```

**Extended vertical video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-5-turbo-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A waterfall cascading down a lush tropical cliff, camera tilting upward slowly",
      "aspect_ratio": "9:16",
      "duration": "10",
      "cfg_scale": 0.5,
      "negative_prompt": "blur, distort, low quality, artifacts, jitter"
    }
  }'
```

## Related Models

- [kling-v2-5-turbo-pro-image-to-video](../kling-v2-5-turbo-pro-image-to-video/) - Pro image to video with tail image support
- [kling-v2-5-turbo-standard-image-to-video](../kling-v2-5-turbo-standard-image-to-video/) - Standard tier image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
