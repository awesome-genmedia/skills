---
name: veo-3-fast-image-to-video
description: "Google Veo 3 Fast | Image to Video. Convert images to videos with audio using Google Veo 3 Fast. Triggers: veo 3 fast image to video, google image to video, veo i2v fast, animate image veo, veo 3 fast, image to video with audio"
allowed-tools: Bash(curl *), WebFetch
---

# Google Veo 3 Fast | Image to Video

Convert still images into videos with optional audio generation using Google Veo 3 Fast. This faster variant of Veo 3 produces high-quality video from an input image and text prompt, with built-in audio generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo-3-fast-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/forest-path.jpg",
      "prompt": "Camera slowly moving forward along the forest path, birds chirping, sunlight filtering through the canopy",
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

**Nature scene with audio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo-3-fast-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/ocean-waves.jpg",
      "prompt": "Waves crashing on the shore, seagulls flying overhead, ocean breeze sounds",
      "aspect_ratio": "16:9",
      "resolution": "1080p",
      "generate_audio": true
    }
  }'
```

**Vertical video without audio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo-3-fast-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/city-skyline.jpg",
      "prompt": "Time lapse of clouds moving over the city, lights turning on as evening approaches",
      "aspect_ratio": "9:16",
      "generate_audio": false
    }
  }'
```

## Related Models

- [Google Veo 3 | Image to Video](../veo-3-image-to-video/) - Higher quality variant (slower)
- [Google Veo 3 | Fast](../veo-3-fast/) - Text-to-video with Veo 3 Fast
- [Google Veo 2 | Image to Video](../veo-2-image-to-video/) - Previous generation image-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
