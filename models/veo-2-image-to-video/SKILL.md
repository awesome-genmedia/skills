---
name: veo-2-image-to-video
description: "Google Veo 2 | Image to Video. Convert images to videos using Google Veo 2. AI-powered image animation with configurable duration and aspect ratio. Triggers: veo 2 image to video, google veo 2, veo 2 i2v, image to video google, veo 2 animate image"
allowed-tools: Bash(curl *), WebFetch
---

# Google Veo 2 | Image to Video

Convert still images into videos using Google Veo 2. Provide an image and a text prompt to generate dynamic videos with configurable aspect ratio and duration from 5 to 8 seconds.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo-2-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/garden.jpg",
      "prompt": "Flowers swaying in a gentle breeze, butterflies landing on petals",
      "duration": "5s",
      "aspect_ratio": "16:9"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | auto | Aspect ratio. Options: `auto`, `auto_prefer_portrait`, `16:9`, `9:16` |
| duration | string | 5s | Video duration. Options: `5s`, `6s`, `7s`, `8s` |
| image_url | string | - | URL of the input image |
| prompt | string | - | Text prompt for video generation |

## Examples

**Animate a landscape photo:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo-2-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/autumn-forest.jpg",
      "prompt": "Leaves gently falling from trees, sunlight streaming through the canopy, a light breeze rustling the foliage",
      "duration": "8s",
      "aspect_ratio": "16:9"
    }
  }'
```

**Portrait video with auto aspect ratio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo-2-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait-photo.jpg",
      "prompt": "The person blinks and smiles softly, hair moving slightly",
      "duration": "5s",
      "aspect_ratio": "auto_prefer_portrait"
    }
  }'
```

## Related Models

- [Google Veo 3 | Image to Video](../veo-3-image-to-video/) - Newer generation with audio
- [Google Veo 3 Fast | Image to Video](../veo-3-fast-image-to-video/) - Fast Veo 3 variant
- [Wan 2.2 | Image to Video](../wan-2-2-i2v/) - Alternative image-to-video model

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
