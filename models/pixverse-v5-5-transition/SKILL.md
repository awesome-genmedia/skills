---
name: pixverse-v5-5-transition
description: "Pixverse v5.5 | Transition. Create video transitions between two images with customizable styles. Triggers: video transition, pixverse, morph, image transition, animation"
allowed-tools: Bash(curl *), WebFetch
---

# Pixverse v5.5 | Transition

Create smooth video transitions between two images. Supports various styles including anime, 3D animation, clay, comic, and cyberpunk with configurable resolution up to 1080p.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-5-transition",
    "version": "0.0.1",
    "input": {
      "first_image_url": "https://example.com/scene1.jpg",
      "end_image_url": "https://example.com/scene2.jpg",
      "prompt": "smooth cinematic transition with light particles",
      "duration": "5",
      "resolution": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video. enum: 16:9, 4:3, 1:1, 3:4, 9:16 |
| duration | string | 5 | The duration of the generated video in seconds. enum: 5, 8, 10 |
| end_image_url | string | | URL of the image to use as the last frame. |
| first_image_url | string | | URL of the image to use as the first frame. |
| generate_audio_switch | boolean | false | Enable audio generation (BGM, SFX, dialogue). |
| negative_prompt | string | | Negative prompt to be used for the generation. |
| prompt | string | | The prompt for the transition. |
| resolution | string | 720p | The resolution of the generated video. enum: 360p, 540p, 720p, 1080p |
| seed | integer | | The same seed and prompt produce the same output. |
| style | string | | The style of the generated video. enum: anime, 3d_animation, clay, comic, cyberpunk |
| thinking_type | string | | Prompt optimization mode. enum: enabled, disabled |

## Examples

**Anime-style transition with audio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-5-transition",
    "version": "0.0.1",
    "input": {
      "first_image_url": "https://example.com/spring.jpg",
      "end_image_url": "https://example.com/winter.jpg",
      "prompt": "magical seasonal transformation with falling leaves",
      "style": "anime",
      "duration": "8",
      "resolution": "1080p",
      "generate_audio_switch": true
    }
  }'
```

**Cyberpunk vertical transition:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-5-transition",
    "version": "0.0.1",
    "input": {
      "first_image_url": "https://example.com/old-city.jpg",
      "end_image_url": "https://example.com/future-city.jpg",
      "prompt": "neon lights flickering as city transforms",
      "style": "cyberpunk",
      "aspect_ratio": "9:16",
      "duration": "5",
      "negative_prompt": "blurry, low quality"
    }
  }'
```

## Related Models

- [Pixverse v5.5 | Text to Video](../pixverse-v5-5-text-to-video/) - Generate videos from text
- [Pixverse v5.5 | Image to Video](../pixverse-v5-5-image-to-video/) - Generate videos from a single image

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
