---
name: kling-v2-1-master-text-to-video
description: "Kling v2.1 | Master | Text to Video. Generate premium videos from text using Kling v2.1 Master. The highest quality Kling text-to-video model. Triggers: kling master text to video, kling v2.1, kling master, premium text to video kling, kling video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Kling v2.1 | Master | Text to Video

Generate premium-quality videos from text prompts using Kling v2.1 Master. The highest quality tier in the Kling v2.1 family, with control over aspect ratio, duration, CFG scale, and negative prompting.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-1-master-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A dancer performing ballet on a moonlit rooftop, flowing white dress, city lights twinkling below",
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
| negative_prompt | string | - | Text describing what to avoid |
| prompt | string | - | Text prompt for video generation |

## Examples

**Dramatic nature scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-1-master-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A lightning storm over the Grand Canyon, dramatic clouds illuminated by bolts of electricity, time-lapse style",
      "aspect_ratio": "16:9",
      "duration": 5,
      "cfg_scale": 0.5,
      "negative_prompt": "blurry, low quality, distorted, watermark"
    }
  }'
```

**Vertical social media content:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-1-master-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A barista creating intricate latte art, top-down close-up shot, creamy milk swirling into coffee",
      "aspect_ratio": "9:16",
      "duration": 5
    }
  }'
```

## Related Models

- [Kling v2.1 | Master | Image to Video](../kling-v2-1-master-image-to-video/) - Master image-to-video
- [Kling v2.1 | Standard | Image to Video](../kling-v2-1-standard-image-to-video/) - Standard tier
- [Google Veo 3](../veo-3/) - Google's premium text-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
