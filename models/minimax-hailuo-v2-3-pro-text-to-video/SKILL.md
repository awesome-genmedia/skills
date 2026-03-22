---
name: minimax-hailuo-v2-3-pro-text-to-video
description: "Minimax Hailuo V2.3 | Pro | Text to Video. Generate high-quality videos from text prompts using the Minimax Hailuo V2.3 Pro model. Triggers: minimax, hailuo, text to video, video generation, hailuo pro"
allowed-tools: Bash(curl *), WebFetch
---

# Minimax Hailuo V2.3 | Pro | Text to Video

Generate high-quality videos from text descriptions using the Minimax Hailuo V2.3 Pro model. This professional-tier model produces detailed, coherent video content with optional prompt optimization.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-3-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A golden retriever running through a sunlit meadow with wildflowers swaying in the breeze",
      "prompt_optimizer": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| prompt | string | | Text prompt for video generation |
| prompt_optimizer | boolean | true | Whether to use the model's prompt optimizer |

## Examples

**Cinematic nature scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-3-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Aerial drone shot of a turquoise ocean coastline with waves crashing against rocky cliffs at sunset",
      "prompt_optimizer": true
    }
  }'
```

**Urban time-lapse without prompt optimization:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-3-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Time-lapse of a busy Tokyo intersection at night with neon lights reflecting on wet pavement, cinematic 4K quality",
      "prompt_optimizer": false
    }
  }'
```

## Related Models

- [minimax-hailuo-v2-3-standard-text-to-video](../minimax-hailuo-v2-3-standard-text-to-video/) - Standard tier text to video with duration control
- [minimax-hailuo-v2-3-standard-image-to-video](../minimax-hailuo-v2-3-standard-image-to-video/) - Standard tier image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
