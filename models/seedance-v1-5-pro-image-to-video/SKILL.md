---
name: seedance-v1-5-pro-image-to-video
description: "Seedance V1.5 | Pro | Image to Video. Generate videos from images with audio, camera control, and end-frame support. Triggers: image to video, video generation, seedance, animate image"
allowed-tools: Bash(curl *), WebFetch
---

# Seedance V1.5 | Pro | Image to Video

Generate videos from images using the Seedance V1.5 Pro model. Features audio generation, camera position control, configurable duration, and support for end-frame images for guided transitions.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-5-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/landscape.jpg",
      "prompt": "Camera slowly pans across the scenic valley, birds flying overhead",
      "resolution": "720p",
      "duration": 5,
      "generate_audio": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video. Options: `21:9`, `16:9`, `4:3`, `1:1`, `3:4`, `9:16` |
| camera_fixed | boolean | false | Whether to fix the camera position. |
| duration | integer | 5 | Duration of the video in seconds. |
| end_image_url | string | - | The URL of the image the video ends with. |
| generate_audio | boolean | true | Whether to generate audio for the video. |
| image_url | string | - | The URL of the image used to generate video. |
| prompt | string | - | The text prompt used to generate the video. |
| resolution | string | 720p | Video resolution. Options: `480p`, `720p`, `1080p` |
| seed | integer | - | Random seed to control video generation. Use -1 for random. |

## Examples

**Basic image to video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-5-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/sunset-beach.jpg",
      "prompt": "Waves gently rolling onto the shore as the sun sets"
    }
  }'
```

**With end frame and fixed camera:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-5-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/flower-bud.jpg",
      "end_image_url": "https://example.com/flower-bloom.jpg",
      "prompt": "A flower gradually blooming in timelapse",
      "camera_fixed": true,
      "duration": 5,
      "resolution": "1080p",
      "aspect_ratio": "1:1",
      "generate_audio": false,
      "seed": 42
    }
  }'
```

## Related Models

- [Seedance V1.5 | Pro | Text to Video](../seedance-v1-5-pro-text-to-video/) - Generate videos from text with Seedance V1.5
- [Wan | v2.6 | Image to Video](../wan-v2-6-image-to-video/) - Wan-based image to video
- [Kandinsky 5 | Pro | Image to Video](../kandinsky5-pro-image-to-video/) - Kandinsky-based image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
