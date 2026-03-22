---
name: minimax-t2v-01
description: "Minimax Hailuo V1 | Text to Video. Generate videos from text descriptions using Minimax Hailuo V1 | Text to Video. Triggers: minimax, text to video, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Minimax Hailuo V1 | Text to Video

Generate videos from text descriptions using Minimax Hailuo V1 | Text to Video. Supports optional prompt optimization.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-t2v-01",
    "version": "0.0.1",
    "input": {
      "prompt": "A serene Japanese garden with cherry blossoms falling gently in the wind"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `prompt` | string |  | Prompt |
| `prompt_optimizer` | boolean | True | Prompt Optimizer |

## Examples

**Nature scene video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-t2v-01",
    "version": "0.0.1",
    "input": {
      "prompt": "A serene Japanese garden with cherry blossoms falling gently in the wind"
    }
  }'
```

**Cinematic aerial shot:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-t2v-01",
    "version": "0.0.1",
    "input": {
      "prompt": "Cinematic drone shot flying over a misty mountain range at golden hour, volumetric lighting",
      "prompt_optimizer": true
    }
  }'
```

## Related Models

- [Minimax Hailuo V1 | Subject to Video](../minimax-s2v-01/) - Generate videos from subject reference images using Minimax Hailuo V1 | Subject to Video.
- [Minimax | Text to Image](../minimax-text-to-image/) - Generate images from text prompts using Minimax | Text to Image.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
