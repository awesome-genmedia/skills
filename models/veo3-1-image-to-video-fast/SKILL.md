---
name: veo3-1-image-to-video-fast
description: "Veo 3.1 | Image to Video | Fast. Quickly animate images into videos with audio using Veo 3.1 Fast. Triggers: veo, image to video, fast video, veo fast, animate image"
allowed-tools: Bash(curl *), WebFetch
---

# Veo 3.1 | Image to video | Fast

Quickly animate still images into dynamic videos with optional audio using the Veo 3.1 Fast model. Optimized for faster generation while maintaining quality.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-image-to-video-fast",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/street-scene.jpg",
      "prompt": "People walk along the street, cars pass by, leaves blow in the wind",
      "duration": 8,
      "resolution": "720p",
      "generate_audio": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video. enum: 9:16, 16:9 |
| auto_fix | boolean | false | Whether to automatically fix prompts that fail content policy |
| duration | integer | 8 | The duration of the generated video in seconds |
| generate_audio | boolean | true | Whether to generate audio. If false, 33% less credits used |
| image_url | string | | URL of the input image to animate (720p or higher recommended) |
| prompt | string | | The text prompt describing the video |
| resolution | string | 720p | Resolution of the generated video. enum: 720p, 1080p |

## Examples

**Quick product animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-image-to-video-fast",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/product-hero.jpg",
      "prompt": "Camera slowly orbits around the product on a clean white backdrop",
      "duration": 8,
      "resolution": "1080p",
      "generate_audio": false
    }
  }'
```

**Vertical social media animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-image-to-video-fast",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/food-plate.jpg",
      "prompt": "Steam rises from the fresh dish, sauce is drizzled on top in slow motion",
      "duration": 8,
      "resolution": "720p",
      "aspect_ratio": "9:16",
      "generate_audio": true,
      "auto_fix": true
    }
  }'
```

## Related Models

- [veo3-1-image-to-video](../veo3-1-image-to-video/) - Standard quality image to video
- [veo3-1-text-to-video-fast](../veo3-1-text-to-video-fast/) - Fast text to video
- [veo3-1-first-last-frame-to-video-fast](../veo3-1-first-last-frame-to-video-fast/) - Fast first/last frame to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
