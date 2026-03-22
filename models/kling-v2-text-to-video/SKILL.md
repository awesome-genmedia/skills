---
name: kling-v2-text-to-video
description: "Kling v2 | Text to Video. Generate videos from text descriptions using Kling v2 | Text to Video. Triggers: kling, text to video, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Kling v2 | Text to Video

Generate videos from text descriptions using Kling v2 | Text to Video. Supports multiple aspect ratios (16:9, 9:16, 1:1), configurable duration, negative prompt support, adjustable CFG scale.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A serene Japanese garden with cherry blossoms falling gently in the wind"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | 16:9 | Options: `16:9`, `9:16`, `1:1` |
| `cfg_scale` | number | 0.5 |  |
| `duration` | integer | 5 |  |
| `negative_prompt` | string |  |  |
| `prompt` | string |  |  |

## Examples

**Nature scene video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-text-to-video",
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
    "model": "kling-v2-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Cinematic drone shot flying over a misty mountain range at golden hour, volumetric lighting",
      "aspect_ratio": "9:16",
      "duration": 8,
      "negative_prompt": "blurry, distorted, low quality, watermark",
      "cfg_scale": 0.7
    }
  }'
```

## Related Models

- [Kling v1.6 | Pro | Elements](../kling-v1-6-pro-elements/) - Generate creative element-based videos using Kling v1.6 | Pro | Elements.
- [Kling v1.6 | Standard | Elements](../kling-v1-6-standard-elements/) - Generate creative element-based videos using Kling v1.6 | Standard | Elements.
- [Kling v1.6 | Standard | Effects](../kling-v1-6-standart-effects/) - Apply visual effects to images and generate videos using Kling v1.6 | Standard | Effects.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
