---
name: motion-video-1-3b
description: "Motion Video | 1.3B. Generate videos from images with the lightweight 1.3B model. Triggers: video generation, image to video, motion video, animate, fast video"
allowed-tools: Bash(curl *), WebFetch
---

# Motion Video | 1.3B

Generate videos from images and reference videos using the lightweight Motion Video 1.3B model. A faster alternative to the 14B variant while maintaining good quality, with image and pose guidance support.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "motion-video-1-3b",
    "version": "0.0.1",
    "input": {
      "prompt": "Ocean waves crashing on a rocky coastline",
      "image_url": "https://example.com/coastline.jpg",
      "resolution": "480p",
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

**Quick image animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "motion-video-1-3b",
    "version": "0.0.1",
    "input": {
      "prompt": "Clouds drifting across a mountain landscape",
      "image_url": "https://example.com/mountain.jpg"
    }
  }'
```

**Video with pose reference:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "motion-video-1-3b",
    "version": "0.0.1",
    "input": {
      "prompt": "A person waving hello and smiling",
      "image_url": "https://example.com/person-standing.jpg",
      "video_url": "https://example.com/wave-reference.mp4",
      "pose_guidance_scale": 2.0,
      "image_guidance_scale": 2.5,
      "negative_prompt": "blurry, artifacts",
      "resolution": "720p"
    }
  }'
```

## Related Models

- [Motion Video | 14B](../motion-video-14b/) - Higher quality 14B variant
- [Motion | Fast](../motion-fast/) - Fast motion generation with turbo mode

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
