---
name: pixverse-v5-5-image-to-video
description: "Pixverse v5.5 | Image to Video. Animate images into videos with multiple styles and resolutions. Triggers: image to video, pixverse, animation, i2v, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Pixverse v5.5 | Image to Video

Animate a static image into a video with support for multiple artistic styles, resolutions up to 1080p, and multi-clip generation with dynamic camera changes.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-5-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/landscape.jpg",
      "prompt": "gentle wind blowing through the trees, birds flying",
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
| generate_audio_switch | boolean | false | Enable audio generation (BGM, SFX, dialogue). |
| generate_multi_clip_switch | boolean | false | Enable multi-clip generation with dynamic camera changes. |
| image_url | string | | URL of the image to use as the first frame. |
| negative_prompt | string | | Negative prompt to be used for the generation. |
| prompt | string | | Text prompt describing the desired motion. |
| resolution | string | 720p | The resolution of the generated video. enum: 360p, 540p, 720p, 1080p |
| seed | integer | | The same seed and prompt produce the same output. |
| style | string | | The style of the generated video. enum: anime, 3d_animation, clay, comic, cyberpunk |
| thinking_type | string | | Prompt optimization mode. enum: enabled, disabled |

## Examples

**Anime-style image animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-5-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/anime-scene.jpg",
      "prompt": "character turns around and smiles, hair flowing in the wind",
      "style": "anime",
      "duration": "8",
      "resolution": "1080p",
      "generate_audio_switch": true
    }
  }'
```

**Product showcase with multi-clip:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-5-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/product.jpg",
      "prompt": "camera slowly orbits around the product, revealing details from all angles",
      "aspect_ratio": "1:1",
      "duration": "10",
      "resolution": "720p",
      "generate_multi_clip_switch": true,
      "negative_prompt": "blurry, shaky, distorted"
    }
  }'
```

## Related Models

- [Pixverse v5.5 | Text to Video](../pixverse-v5-5-text-to-video/) - Generate video from text only
- [Pixverse v5.5 | Transition](../pixverse-v5-5-transition/) - Create transitions between two images

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
