---
name: minimax-s2v-01
description: "Minimax Hailuo V1 | Subject to Video. Generate videos from subject reference images using Minimax Hailuo V1 | Subject to Video. Triggers: minimax, subject to video, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Minimax Hailuo V1 | Subject to Video

Generate videos from subject reference images using Minimax Hailuo V1 | Subject to Video. Supports optional prompt optimization.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-s2v-01",
    "version": "0.0.1",
    "input": {
      "prompt": "A character walking confidently through a neon-lit city street"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `prompt` | string |  |  |
| `prompt_optimizer` | boolean |  |  |
| `subject_image` | string |  | URL of the subject reference image to use for consistent subject appearance |

## Examples

**Subject-driven video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-s2v-01",
    "version": "0.0.1",
    "input": {
      "prompt": "A character walking confidently through a neon-lit city street"
    }
  }'
```

**Cinematic subject video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-s2v-01",
    "version": "0.0.1",
    "input": {
      "prompt": "A figure standing on a cliff edge overlooking a vast ocean at sunset"
    }
  }'
```

## Related Models

- [Minimax Hailuo V1 | Text to Video](../minimax-t2v-01/) - Generate videos from text descriptions using Minimax Hailuo V1 | Text to Video.
- [Minimax | Text to Image](../minimax-text-to-image/) - Generate images from text prompts using Minimax | Text to Image.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
