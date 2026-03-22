---
name: wan-2-1-i2v-720p
description: "Wan 2.1 | Image to Video | 720P. Generate videos from images using Wan 2.1 | Image to Video | 720P. Triggers: image to video, video generation, wan"
allowed-tools: Bash(curl *), WebFetch
---

# Wan 2.1 | Image to Video | 720P

Generate videos from images using Wan 2.1 | Image to Video | 720P. Supports reproducible results via seed.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-2-1-i2v-720p",
    "version": "0.0.1",
    "input": {
      "prompt": "Slow camera pan with gentle wind movement"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `fast_mode` | string | Off | An enumeration.. Options: `Off`, `Balanced`, `Fast`, `Ultra-fast` |
| `frames_per_second` | integer | 16 | Frames per second. Note that the pricing of this model is based on the video dur |
| `image` | string |  | Input image to start generating from |
| `max_area` | string | 1280x720 | An enumeration.. Options: `1280x720`, `720x1280` |
| `num_frames` | integer | 81 | Number of video frames |
| `prompt` | string |  | Prompt for video generation |
| `sample_guide_scale` | number | 5 | Higher guide scale makes prompt adherence better, but can reduce variation |
| `sample_shift` | number | 5 | Sample shift factor |
| `sample_steps` | integer | 30 | Number of generation steps. Fewer steps means faster generation, at the expensiv |
| `seed` | integer |  | Random seed. Leave blank for random |

## Examples

**Animate an image:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-2-1-i2v-720p",
    "version": "0.0.1",
    "input": {
      "prompt": "Slow camera pan with gentle wind movement"
    }
  }'
```

**Dynamic animation with controls:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-2-1-i2v-720p",
    "version": "0.0.1",
    "input": {
      "prompt": "Dynamic camera zoom with dramatic lighting changes",
      "seed": 42
    }
  }'
```

## Related Models

- [Wan 2.1 | Image to Video | 480P](../wan-2-1-i2v-480p/) - Generate videos from images using Wan 2.1 | Image to Video | 480P.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
