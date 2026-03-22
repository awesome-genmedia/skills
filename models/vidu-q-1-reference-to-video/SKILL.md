---
name: vidu-q-1-reference-to-video
description: "Vidu Q1 | Reference to Video. Generate videos from reference images using Vidu Q1 AI. Create dynamic videos using up to 4 reference images with prompt guidance. Triggers: vidu reference to video, vidu q1, reference to video, image reference video, multi image video, vidu video"
allowed-tools: Bash(curl *), WebFetch
---

# Vidu Q1 | Reference to Video

Generate videos from reference images using Vidu Q1. Provide up to 4 reference images and a text prompt to create dynamic videos with control over duration, aspect ratio, movement amplitude, and resolution.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-q-1-reference-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/character.jpg",
      "prompt": "The character walks through a magical forest, looking around in wonder",
      "duration": 5,
      "aspect_ratio": "16:9"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio of the output video. Options: `16:9`, `9:16`, `1:1` |
| bgm | boolean | false | Enable background music generation |
| duration | integer | 5 | Duration of the output video in seconds |
| image_url | string | - | Primary reference image URL (png, jpeg, jpg, webp) |
| image_url2 | string | - | Second reference image URL |
| image_url3 | string | - | Third reference image URL |
| image_url4 | string | - | Fourth reference image URL |
| movement_amplitude | string | auto | Movement intensity. Options: `auto`, `small`, `medium`, `large` |
| prompt | string | - | Text prompt for video generation (max length varies) |
| resolution | string | - | Video resolution. Options: `1080p` |
| seed | integer | - | Random seed for reproducible results |

## Examples

**Character animation with reference:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-q-1-reference-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/anime-character.png",
      "prompt": "The character smiles and waves at the camera, cherry blossoms falling around them",
      "duration": 5,
      "aspect_ratio": "9:16",
      "movement_amplitude": "medium"
    }
  }'
```

**Multi-reference video with background music:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-q-1-reference-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/person.jpg",
      "image_url2": "https://example.com/background-scene.jpg",
      "prompt": "The person stands on a cliff overlooking the ocean, wind blowing their hair",
      "duration": 5,
      "aspect_ratio": "16:9",
      "bgm": true,
      "resolution": "1080p"
    }
  }'
```

## Related Models

- [Google Veo 3 | Image to Video](../veo-3-image-to-video/) - Google's image-to-video model
- [Seedance V1 | Pro | Image to Video](../seedance-v1-pro-image-to-video/) - Seedance image-to-video
- [Kling v2.1 | Master | Image to Video](../kling-v2-1-master-image-to-video/) - Kling's image-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
