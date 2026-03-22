---
name: sora-2-image-to-video
description: "Sora 2 | Image to Video. Animate images into videos using OpenAI Sora 2. Triggers: sora, image to video, sora 2, animate image, openai sora"
allowed-tools: Bash(curl *), WebFetch
---

# Sora 2 | Image to Video

Animate images into videos using OpenAI Sora 2. Supports configurable duration and aspect ratio for versatile video output.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sora-2-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/autumn-park.jpg",
      "prompt": "Leaves fall gently from the trees, a person walks along the path with an umbrella",
      "duration": 4,
      "aspect_ratio": "16:9"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video. enum: 9:16, 16:9 |
| duration | integer | 4 | Duration of the generated video in seconds |
| image_url | string | | The URL of the image to use as the first frame |
| prompt | string | | The text prompt describing the video |

## Examples

**Landscape animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sora-2-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/mountain-lake.jpg",
      "prompt": "Water ripples across the lake surface, clouds drift slowly overhead",
      "duration": 4,
      "aspect_ratio": "16:9"
    }
  }'
```

**Portrait video for social media:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sora-2-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/studio-portrait.jpg",
      "prompt": "Person smiles and waves at the camera, natural subtle movement",
      "duration": 4,
      "aspect_ratio": "9:16"
    }
  }'
```

## Related Models

- [sora-2-image-to-video-pro](../sora-2-image-to-video-pro/) - Pro tier with resolution control
- [sora-2-text-to-video](../sora-2-text-to-video/) - Text to video
- [sora-2-text-to-video-pro](../sora-2-text-to-video-pro/) - Pro text to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
