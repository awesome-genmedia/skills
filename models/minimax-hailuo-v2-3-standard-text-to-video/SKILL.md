---
name: minimax-hailuo-v2-3-standard-text-to-video
description: "Minimax Hailuo V2.3 | Standard | Text to Video. Generate videos from text prompts using the Minimax Hailuo V2.3 Standard model. Triggers: minimax, hailuo, text to video, video generation, hailuo standard"
allowed-tools: Bash(curl *), WebFetch
---

# Minimax Hailuo V2.3 | Standard | Text to Video

Generate videos from text descriptions using the Minimax Hailuo V2.3 Standard model. Supports configurable duration and optional prompt optimization for better results.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-3-standard-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A cat playing with a ball of yarn in a cozy living room with warm afternoon light",
      "duration": "6",
      "prompt_optimizer": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| duration | string | 6 | The duration of the video in seconds. enum: 6, 10 |
| prompt | string | | Text prompt for video generation |
| prompt_optimizer | boolean | true | Whether to use the model's prompt optimizer |

## Examples

**Short scene generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-3-standard-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Rain falling on a window with city lights blurred in the background",
      "duration": "6",
      "prompt_optimizer": true
    }
  }'
```

**Extended video with custom prompt:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-3-standard-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A chef preparing sushi in a traditional Japanese restaurant, detailed hand movements, warm lighting, cinematic composition",
      "duration": "10",
      "prompt_optimizer": false
    }
  }'
```

## Related Models

- [minimax-hailuo-v2-3-pro-text-to-video](../minimax-hailuo-v2-3-pro-text-to-video/) - Pro tier text to video
- [minimax-hailuo-v2-3-standard-image-to-video](../minimax-hailuo-v2-3-standard-image-to-video/) - Standard tier image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
