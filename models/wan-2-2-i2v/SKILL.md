---
name: wan-2-2-i2v
description: "Wan 2.2 | Image to Video. Convert images to videos using Wan 2.2 AI model. Animate still images into dynamic video content. Triggers: wan image to video, image to video, animate image, wan 2.2, i2v, image animation, still to video"
allowed-tools: Bash(curl *), WebFetch
---

# Wan 2.2 | Image to Video

Convert still images into dynamic videos using Wan 2.2. Provide an image and a text prompt to guide the animation, with control over aspect ratio, resolution, and content safety.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-2-2-i2v",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/sunset-landscape.jpg",
      "prompt": "Clouds drifting slowly across the sky, gentle breeze moving the grass",
      "resolution": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | auto | Aspect ratio of the output video. Options: `auto`, `16:9`, `9:16`, `1:1` |
| enable_safety_checker | boolean | false | Enable content safety checking |
| image_url | string | - | URL of the input image to animate |
| negative_prompt | string | - | Text describing what to avoid in the video |
| prompt | string | - | Text prompt to guide the animation |
| resolution | string | 720p | Output resolution. Options: `480p`, `720p` |

## Examples

**Animate a nature scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-2-2-i2v",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/waterfall.jpg",
      "prompt": "Water cascading down the rocks, mist rising, birds flying overhead",
      "aspect_ratio": "16:9",
      "resolution": "720p"
    }
  }'
```

**Animate a portrait:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-2-2-i2v",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "prompt": "Person slowly turning their head and smiling, hair blowing in the wind",
      "aspect_ratio": "9:16",
      "negative_prompt": "blurry, distorted, low quality"
    }
  }'
```

## Related Models

- [Google Veo 3 | Image to Video](../veo-3-image-to-video/) - Google's image-to-video model
- [Kling v2.1 | Master | Image to Video](../kling-v2-1-master-image-to-video/) - Kling's premium image-to-video
- [Seedance V1 | Pro | Image to Video](../seedance-v1-pro-image-to-video/) - Seedance image-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
