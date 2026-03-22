---
name: minimax-hailuo-v2-standard-text-to-video
description: "Minimax Hailuo V2 | Standard | Text to Video. Generate videos from text prompts using Minimax Hailuo V2 Standard. AI text-to-video generation. Triggers: hailuo text to video, minimax t2v, hailuo v2 standard video, minimax text to video, text to video hailuo"
allowed-tools: Bash(curl *), WebFetch
---

# Minimax Hailuo V2 | Standard | Text to Video

Generate videos from text descriptions using Minimax Hailuo V2 Standard. Create dynamic video content from text prompts with configurable duration and built-in prompt optimization.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-standard-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A hot air balloon rising above a misty valley at sunrise, cinematic aerial shot",
      "duration": 6
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| duration | integer | 6 | Video duration in seconds |
| prompt | string | - | Text prompt for video generation |
| prompt_optimizer | boolean | true | Whether to use the model's prompt optimizer |

## Examples

**Cinematic nature scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-standard-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A majestic eagle soaring over snow-capped mountains, wings spread wide, dramatic aerial cinematography",
      "duration": 6,
      "prompt_optimizer": true
    }
  }'
```

**Urban time-lapse:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-standard-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Time-lapse of a busy city intersection at night, headlights and taillights creating light trails, buildings illuminated",
      "duration": 6
    }
  }'
```

## Related Models

- [Minimax Hailuo V2 | Pro | Text to Video](../minimax-hailuo-v2-pro-text-to-video/) - Higher quality Pro variant
- [Minimax Hailuo V2 | Standard | Image to Video](../minimax-hailuo-v2-standard-image-to-video/) - Image-to-video standard
- [Google Veo 3 | Fast](../veo-3-fast/) - Google's fast text-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
