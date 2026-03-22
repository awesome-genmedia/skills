---
name: motion-fast
description: "Motion | Fast. Generate videos from images or videos with fast processing. Triggers: video generation, image to video, motion, animate image"
allowed-tools: Bash(curl *), WebFetch
---

# Motion | Fast

Generate videos from images or existing videos with fast processing. Supports multiple resolutions up to 720p, turbo quality enhancement, and configurable inference steps for balancing speed and quality.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "motion-fast",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/landscape.jpg",
      "resolution": "720p",
      "num_inference_steps": 20,
      "video_quality": "high"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| enable_safety_checker | boolean | false | If set to true, input data will be checked for safety before processing. |
| image_url | string | - | URL of the input image. If the input image does not match the chosen aspect ratio, it will be cropped. |
| num_inference_steps | integer | 20 | Number of inference steps for sampling. Higher values give better quality but take longer. |
| resolution | string | 480p | Resolution of the generated video. Options: `480p`, `580p`, `720p` |
| seed | integer | - | Random seed for reproducibility. If not provided, a random seed is chosen. |
| shift | number | 5 | Shift value for the video. Must be between 1.0 and 10.0. |
| use_turbo | boolean | false | If true, applies quality enhancement for faster generation with improved quality. |
| video_quality | string | high | The quality of the output video. Options: `low`, `medium`, `high`, `maximum` |
| video_url | string | - | URL of the input video. |
| video_write_mode | string | balanced | The write mode of the output video. Options: `fast`, `balanced`, `small` |

## Examples

**Image to video with turbo mode:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "motion-fast",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "use_turbo": true,
      "resolution": "480p",
      "video_quality": "high"
    }
  }'
```

**Video to video transformation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "motion-fast",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/input-clip.mp4",
      "resolution": "720p",
      "num_inference_steps": 25,
      "shift": 7.0,
      "video_write_mode": "small",
      "seed": 42
    }
  }'
```

**Maximum quality output:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "motion-fast",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/scenic-view.jpg",
      "resolution": "720p",
      "video_quality": "maximum",
      "num_inference_steps": 30,
      "video_write_mode": "balanced"
    }
  }'
```

## Related Models

- [Motion Video | 14B](../motion-video-14b/) - Higher quality 14B motion video model
- [Motion Video | 1.3B](../motion-video-1-3b/) - Lightweight 1.3B motion video model

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
