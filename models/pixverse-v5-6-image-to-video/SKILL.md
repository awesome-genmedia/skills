---
name: pixverse-v5-6-image-to-video
description: "Pixverse v5.6 | Image to Video. Animate images into videos with style controls, audio generation, and prompt optimization. Triggers: image to video, pixverse, animate, i2v, video"
allowed-tools: Bash(curl *), WebFetch
---

# Pixverse v5.6 | Image to Video

Animate images into videos using Pixverse v5.6 with style presets, audio generation, prompt optimization, and up to 1080p resolution.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-6-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "The scene comes alive with gentle wind and moving clouds",
      "image_url": "https://example.com/landscape.jpg",
      "duration": "5",
      "resolution": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| duration | string | 5 | Duration in seconds. 1080p limited to 5 or 8. enum: 5, 8, 10 |
| generate_audio_switch | boolean | false | Enable audio generation (BGM, SFX, dialogue). |
| image_url | string | | URL of the image to use as the first frame. |
| negative_prompt | string | | Negative prompt to avoid unwanted content. |
| prompt | string | | Text prompt for the video. |
| resolution | string | 720p | Video resolution. enum: 360p, 540p, 720p, 1080p |
| seed | integer | | Random seed for reproducible results. |
| style | string | | Video style. enum: anime, 3d_animation, clay, comic, cyberpunk |
| thinking_type | string | | Prompt optimization mode. enum: enabled, disabled, auto |

## Examples

**Animate a landscape with audio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-6-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Waves crash against rocks as seagulls circle overhead",
      "image_url": "https://example.com/ocean-cliff.jpg",
      "duration": "8",
      "resolution": "1080p",
      "generate_audio_switch": true,
      "thinking_type": "enabled"
    }
  }'
```

**Anime-style animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-6-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "The character draws their sword with a dramatic swoosh",
      "image_url": "https://example.com/anime-warrior.jpg",
      "duration": "5",
      "style": "anime",
      "negative_prompt": "blurry, static, low quality",
      "seed": 1234
    }
  }'
```

**Quick low-res preview:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-6-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A gentle zoom into the portrait with soft lighting",
      "image_url": "https://example.com/portrait.jpg",
      "duration": "5",
      "resolution": "360p",
      "thinking_type": "disabled"
    }
  }'
```

## Related Models

- [pixverse-v5-6-text-to-video](../pixverse-v5-6-text-to-video/) - Pixverse v5.6 text to video
- [pixverse-v5-6-transition](../pixverse-v5-6-transition/) - Pixverse v5.6 transitions

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
