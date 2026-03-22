---
name: wan-v2-2-14b-animate-replace
description: "Wan | v2.2 14B | Animate | Replace. Replace subjects in video with image content using Wan v2.2 14B. Triggers: wan, animate, replace, subject replacement, video edit, wan 14b"
allowed-tools: Bash(curl *), WebFetch
---

# Wan | v2.2 14B | Animate | Replace

Replace subjects in a reference video with content from a still image using the Wan v2.2 14B model. The replacement subject adopts the motion and behavior from the original video.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-2-14b-animate-replace",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/new-character.jpg",
      "video_url": "https://example.com/original-video.mp4",
      "resolution": "720p",
      "num_inference_steps": 20,
      "video_quality": "high"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| enable_safety_checker | boolean | false | If true, input data will be checked for safety |
| image_url | string | | URL of the replacement image |
| num_inference_steps | integer | 20 | Number of inference steps. Higher = better quality, slower |
| resolution | string | 480p | Resolution of the generated video. enum: 480p, 580p, 720p |
| seed | integer | | Random seed for reproducibility |
| shift | number | 5 | Shift value for the video (1.0 to 10.0) |
| video_quality | string | high | Output video quality. enum: low, medium, high, maximum |
| video_url | string | | URL of the reference video for motion source |
| video_write_mode | string | balanced | Output video write mode. enum: fast, balanced, small |

## Examples

**Character replacement in video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-2-14b-animate-replace",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/anime-character.jpg",
      "video_url": "https://example.com/person-talking.mp4",
      "resolution": "720p",
      "num_inference_steps": 25,
      "video_quality": "maximum",
      "shift": 6,
      "seed": 42
    }
  }'
```

**Quick preview replacement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-2-14b-animate-replace",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/product-image.jpg",
      "video_url": "https://example.com/product-showcase.mp4",
      "resolution": "480p",
      "num_inference_steps": 15,
      "video_quality": "medium",
      "video_write_mode": "fast"
    }
  }'
```

## Related Models

- [wan-v2-2-14b-animate-move](../wan-v2-2-14b-animate-move/) - Animate with motion transfer
- [wan-2-5-preview-image-to-video](../wan-2-5-preview-image-to-video/) - Image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
