---
name: kling-v1-pro-text-to-video
description: "Kling v1 | Pro | Text to Video. Generate high-quality videos from text using Kling v1 Pro. Professional Kling text-to-video generation. Triggers: kling v1 pro text to video, kling pro video, kling v1 pro t2v, kling pro text to video"
allowed-tools: Bash(curl *), WebFetch
---

# Kling v1 | Pro | Text to Video

Generate high-quality videos from text prompts using Kling v1 Pro. The professional tier of Kling v1 for text-to-video, offering improved quality over Standard with control over duration, aspect ratio, and CFG scale.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A skilled blacksmith hammering red-hot metal on an anvil, sparks flying, dramatic workshop lighting",
      "aspect_ratio": "16:9",
      "duration": 5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio. Options: `16:9`, `9:16`, `1:1` |
| cfg_scale | number | 0.5 | Classifier-free guidance scale |
| duration | integer | 5 | Video duration in seconds |
| negative_prompt | string | blur, distort, and low quality | Things to avoid in generation |
| prompt | string | - | Text prompt for video generation |

## Examples

**Cinematic scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A lone surfer riding a massive wave at sunset, golden light backlighting the spray, slow motion cinematic",
      "aspect_ratio": "16:9",
      "duration": 5,
      "negative_prompt": "blur, distort, and low quality"
    }
  }'
```

**Vertical content:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A magician performing a card trick, cards floating in the air, dramatic spotlight",
      "aspect_ratio": "9:16",
      "cfg_scale": 0.5
    }
  }'
```

## Related Models

- [Kling v1 | Standard | Text to Video](../kling-v1-standard-text-to-video/) - Standard tier with camera control
- [Kling v2.1 | Master | Text to Video](../kling-v2-1-master-text-to-video/) - Latest generation Master
- [Kling v1 | Pro | Image to Video](../kling-v1-pro-image-to-video/) - Pro image-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
