---
name: motion-video-14b
description: "Motion Video | 14B. Generate videos from images with the high-quality 14B model. Triggers: video generation, image to video, motion video, animate, pose video"
allowed-tools: Bash(curl *), WebFetch
---

# Motion Video | 14B

Generate videos from images and reference videos using the high-quality Motion Video 14B model. Supports image guidance, pose guidance, and prompt-driven video generation with resolutions up to 720p.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "motion-video-14b",
    "version": "0.0.1",
    "input": {
      "prompt": "A person walking gracefully through a field of flowers",
      "image_url": "https://example.com/person.jpg",
      "resolution": "720p",
      "num_inference_steps": 30
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| image_guidance_scale | number | 2 | The image guidance scale to use for video generation. |
| image_url | string | - | The URL of the image to use as a reference for video generation. |
| negative_prompt | string | - | The negative prompt to generate the video from. |
| num_inference_steps | integer | 30 | The number of inference steps to use for video generation. |
| pose_guidance_scale | number | 1.5 | The pose guidance scale to use for video generation. |
| prompt | string | - | The prompt to generate the video from. |
| resolution | string | 480p | The resolution of the video to generate. Options: `480p`, `580p`, `720p` |
| video_url | string | - | The URL of the video to use as a reference for video generation. |

## Examples

**Image-driven video generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "motion-video-14b",
    "version": "0.0.1",
    "input": {
      "prompt": "Gentle wind blowing through hair, soft sunlight",
      "image_url": "https://example.com/portrait.jpg",
      "image_guidance_scale": 3,
      "resolution": "720p"
    }
  }'
```

**Video-referenced motion transfer:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "motion-video-14b",
    "version": "0.0.1",
    "input": {
      "prompt": "A dancer performing ballet moves in a studio",
      "image_url": "https://example.com/dancer.jpg",
      "video_url": "https://example.com/dance-reference.mp4",
      "pose_guidance_scale": 2.0,
      "negative_prompt": "blurry, distorted, low quality",
      "num_inference_steps": 40
    }
  }'
```

## Related Models

- [Motion Video | 1.3B](../motion-video-1-3b/) - Lightweight 1.3B variant for faster generation
- [Motion | Fast](../motion-fast/) - Fast motion generation with turbo mode

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
