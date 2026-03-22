---
name: kandinsky5-pro-text-to-video
description: "Kandinsky 5 | Pro | Text to Video. Generate videos from text prompts using Kandinsky 5 Pro. Triggers: text to video, video generation, kandinsky, ai video"
allowed-tools: Bash(curl *), WebFetch
---

# Kandinsky 5 | Pro | Text to Video

Generate videos from text prompts using the Kandinsky 5 Pro model. Supports configurable aspect ratios, resolutions up to 1024p, and acceleration for faster generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kandinsky5-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A drone shot flying over a vast green valley with a river winding through it",
      "aspect_ratio": "3:2",
      "resolution": "512P",
      "num_inference_steps": 28
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | regular | Acceleration level for faster generation. Options: `none`, `regular` |
| aspect_ratio | string | 3:2 | Aspect ratio of the generated video. Options: `3:2`, `1:1`, `2:3` |
| num_inference_steps | integer | 28 | The number of inference steps. |
| prompt | string | - | The text prompt to guide video generation. |
| resolution | string | 512P | Video resolution. Options: `512P`, `1024P` |

## Examples

**Quick text-to-video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kandinsky5-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A campfire crackling in the woods at night, sparks flying upward"
    }
  }'
```

**High resolution square video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kandinsky5-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Timelapse of flowers blooming in a garden, vibrant colors",
      "aspect_ratio": "1:1",
      "resolution": "1024P",
      "acceleration": "none",
      "num_inference_steps": 35
    }
  }'
```

## Related Models

- [Kandinsky 5 | Pro | Image to Video](../kandinsky5-pro-image-to-video/) - Generate videos from images with Kandinsky 5
- [Wan | v2.6 | Text to Video](../wan-v2-6-text-to-video/) - Wan-based text to video
- [Seedance V1.5 | Pro | Text to Video](../seedance-v1-5-pro-text-to-video/) - Seedance text to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
