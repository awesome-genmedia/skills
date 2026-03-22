---
name: pixverse-v5-6-text-to-video
description: "Pixverse v5.6 | Text to Video. Generate videos from text with style presets, audio, and prompt optimization. Triggers: text to video, pixverse, video generation, t2v"
allowed-tools: Bash(curl *), WebFetch
---

# Pixverse v5.6 | Text to Video

Generate videos from text prompts using Pixverse v5.6 with style presets, audio generation, prompt optimization, and up to 1080p resolution.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-6-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A robot walking through a neon-lit cyberpunk city at night",
      "duration": "5",
      "aspect_ratio": "16:9",
      "resolution": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio. enum: 16:9, 4:3, 1:1, 3:4, 9:16 |
| duration | string | 5 | Duration in seconds. 1080p limited to 5 or 8. enum: 5, 8, 10 |
| generate_audio_switch | boolean | false | Enable audio generation (BGM, SFX, dialogue). |
| negative_prompt | string | | Negative prompt to avoid unwanted content. |
| prompt | string | | Text prompt for video generation. |
| resolution | string | 720p | Video resolution. enum: 360p, 540p, 720p, 1080p |
| seed | integer | | Random seed for reproducible results. |
| style | string | | Video style. enum: anime, 3d_animation, clay, comic, cyberpunk |
| thinking_type | string | | Prompt optimization mode. enum: enabled, disabled, auto |

## Examples

**Cyberpunk-style video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-6-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Flying cars zooming through a futuristic megacity with holographic ads",
      "duration": "8",
      "aspect_ratio": "16:9",
      "style": "cyberpunk",
      "resolution": "1080p",
      "generate_audio_switch": true
    }
  }'
```

**Anime video with prompt optimization:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-6-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A magical girl transformation sequence with sparkles and ribbons",
      "duration": "5",
      "aspect_ratio": "9:16",
      "style": "anime",
      "thinking_type": "enabled",
      "negative_prompt": "blurry, deformed, static"
    }
  }'
```

**Clay animation style:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-6-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A cute dinosaur eating leaves from a tall tree",
      "duration": "5",
      "aspect_ratio": "1:1",
      "style": "clay",
      "resolution": "720p",
      "seed": 7777
    }
  }'
```

## Related Models

- [pixverse-v5-6-image-to-video](../pixverse-v5-6-image-to-video/) - Pixverse v5.6 image to video
- [pixverse-v5-6-transition](../pixverse-v5-6-transition/) - Pixverse v5.6 transitions

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
