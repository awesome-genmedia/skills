---
name: veo-3-image-to-video
description: "Google Veo 3 | Image to Video. Convert images to high-quality videos with audio using Google Veo 3. Triggers: veo 3 image to video, google image to video, veo i2v, animate image veo 3, image to video with audio, veo 3"
allowed-tools: Bash(curl *), WebFetch
---

# Google Veo 3 | Image to Video

Convert still images into high-quality videos with optional audio generation using Google Veo 3. The flagship image-to-video model from Google, producing premium quality animations from a single image and text prompt.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo-3-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/mountain-cabin.jpg",
      "prompt": "Smoke rising from the chimney, snow gently falling, warm light glowing from the windows",
      "aspect_ratio": "16:9",
      "generate_audio": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio of the generated video. Options: `16:9`, `9:16` |
| generate_audio | boolean | true | Whether to generate audio along with the video |
| image_url | string | - | URL of the image used to generate video |
| prompt | string | - | Text prompt for video generation |
| resolution | string | 720p | Resolution of the generated video. Options: `720p`, `1080p` |

## Examples

**Cinematic landscape animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo-3-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/desert-dunes.jpg",
      "prompt": "Wind blowing sand across the dunes, dramatic shadows shifting as clouds pass overhead",
      "aspect_ratio": "16:9",
      "resolution": "1080p",
      "generate_audio": true
    }
  }'
```

**Portrait animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo-3-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/street-scene.jpg",
      "prompt": "People walking past, cars driving by, camera slowly panning right",
      "aspect_ratio": "9:16",
      "resolution": "720p"
    }
  }'
```

## Related Models

- [Google Veo 3 Fast | Image to Video](../veo-3-fast-image-to-video/) - Faster variant for quicker results
- [Google Veo 3](../veo-3/) - Text-to-video generation
- [Google Veo 2 | Image to Video](../veo-2-image-to-video/) - Previous generation model

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
