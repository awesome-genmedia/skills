---
name: p-video
description: "P video. Generate videos from text or images with audio support, draft mode, and configurable resolution. Triggers: video generation, p-video, text to video, image to video"
allowed-tools: Bash(curl *), WebFetch
---

# P video

Generate videos from text prompts or images with optional audio conditioning, draft preview mode, and up to 1080p resolution. Supports text-to-video and image-to-video workflows.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "p-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A timelapse of clouds moving over a mountain range at golden hour",
      "duration": 9,
      "aspect_ratio": "16:9",
      "resolution": "1080p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio. enum: 16:9, 9:16, 4:3, 3:4, 3:2, 2:3, 1:1 |
| audio | string | | Input audio URL to condition video generation. Supports flac, mp3, wav. |
| draft | boolean | false | Draft mode. Generates a lower-quality preview of the video. |
| duration | integer | 9 | Duration of the video in seconds (1-10). Ignored when audio is provided. |
| fps | integer | 24 | Frames per second. |
| image | string | | Input image URL for image-to-video generation. Supports jpg, jpeg, png, webp. |
| prompt | string | | Text prompt for video generation. |
| prompt_upsampling | boolean | true | Use prompt upsampling to enhance the prompt. |
| resolution | string | 720p | Video resolution. enum: 720p, 1080p |
| save_audio | boolean | true | Save the video with audio. |
| seed | integer | | Random seed for reproducible generation. |

## Examples

**Text to video with high resolution:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "p-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A butterfly emerging from a cocoon in a lush garden",
      "duration": 7,
      "aspect_ratio": "16:9",
      "resolution": "1080p",
      "prompt_upsampling": true
    }
  }'
```

**Image to video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "p-video",
    "version": "0.0.1",
    "input": {
      "prompt": "The scene comes to life with gentle wind blowing through the trees",
      "image": "https://example.com/forest-scene.jpg",
      "duration": 5,
      "resolution": "720p"
    }
  }'
```

**Quick draft preview:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "p-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A city street at night with rain and neon reflections",
      "duration": 5,
      "aspect_ratio": "9:16",
      "draft": true,
      "seed": 99
    }
  }'
```

## Related Models

- [kling-v3-standard-text-to-video](../kling-v3-standard-text-to-video/) - Kling v3 text to video
- [pixverse-v5-6-text-to-video](../pixverse-v5-6-text-to-video/) - Pixverse text to video
- [xai-grok-imagine-text-to-video](../xai-grok-imagine-text-to-video/) - Grok text to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
