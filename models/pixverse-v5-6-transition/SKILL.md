---
name: pixverse-v5-6-transition
description: "Pixverse v5.6 | Transition. Create video transitions between two images with style controls and up to 1080p. Triggers: transition, pixverse, video, morph, image transition"
allowed-tools: Bash(curl *), WebFetch
---

# Pixverse v5.6 | Transition

Create smooth video transitions between two images with style controls, negative prompts, and up to 1080p resolution.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-6-transition",
    "version": "0.0.1",
    "input": {
      "prompt": "A smooth cinematic transition between the two scenes",
      "first_image_url": "https://example.com/scene-a.jpg",
      "end_image_url": "https://example.com/scene-b.jpg",
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
| end_image_url | string | | URL of the image for the last frame. |
| first_image_url | string | | URL of the image for the first frame. |
| negative_prompt | string | | Negative prompt to avoid unwanted content. |
| prompt | string | | The prompt for the transition. |
| resolution | string | 720p | Video resolution. enum: 360p, 540p, 720p, 1080p |
| seed | integer | | Random seed for reproducible results. |
| style | string | | Video style. enum: anime, 3d_animation, clay, comic, cyberpunk |

## Examples

**Cinematic scene transition:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-6-transition",
    "version": "0.0.1",
    "input": {
      "prompt": "A magical transformation morphing from summer to winter",
      "first_image_url": "https://example.com/summer-park.jpg",
      "end_image_url": "https://example.com/winter-park.jpg",
      "duration": "8",
      "aspect_ratio": "16:9",
      "resolution": "1080p"
    }
  }'
```

**Anime-style transition:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-6-transition",
    "version": "0.0.1",
    "input": {
      "prompt": "Characters morph between forms with dramatic energy effects",
      "first_image_url": "https://example.com/character-a.jpg",
      "end_image_url": "https://example.com/character-b.jpg",
      "duration": "5",
      "style": "anime",
      "negative_prompt": "blurry, low quality",
      "seed": 42
    }
  }'
```

**Vertical transition for social media:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-6-transition",
    "version": "0.0.1",
    "input": {
      "prompt": "A dreamy dissolve between two outfits",
      "first_image_url": "https://example.com/outfit1.jpg",
      "end_image_url": "https://example.com/outfit2.jpg",
      "duration": "5",
      "aspect_ratio": "9:16",
      "resolution": "720p"
    }
  }'
```

## Related Models

- [pixverse-v5-6-text-to-video](../pixverse-v5-6-text-to-video/) - Pixverse v5.6 text to video
- [pixverse-v5-6-image-to-video](../pixverse-v5-6-image-to-video/) - Pixverse v5.6 image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
