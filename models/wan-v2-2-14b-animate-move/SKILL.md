---
name: wan-v2-2-14b-animate-move
description: "Wan | v2.2 14B | Animate | Move. Animate images with motion transfer from reference video using Wan v2.2 14B. Triggers: wan, animate, move, motion transfer, image animation, wan 14b"
allowed-tools: Bash(curl *), WebFetch
---

# Wan | v2.2 14B | Animate | Move

Animate still images with motion patterns transferred from reference videos using the Wan v2.2 14B model. The subject in the image adopts the movement from the reference video.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-2-14b-animate-move",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/person-standing.jpg",
      "video_url": "https://example.com/dance-reference.mp4",
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
| image_url | string | | URL of the input image to animate |
| num_inference_steps | integer | 20 | Number of inference steps. Higher = better quality, slower |
| resolution | string | 480p | Resolution of the generated video. enum: 480p, 580p, 720p |
| seed | integer | | Random seed for reproducibility |
| shift | number | 5 | Shift value for the video (1.0 to 10.0) |
| video_quality | string | high | Output video quality. enum: low, medium, high, maximum |
| video_url | string | | URL of the reference motion video |
| video_write_mode | string | balanced | Output video write mode. enum: fast, balanced, small |

## Examples

**High-quality dance animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-2-14b-animate-move",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/character-portrait.jpg",
      "video_url": "https://example.com/choreography.mp4",
      "resolution": "720p",
      "num_inference_steps": 30,
      "video_quality": "maximum",
      "shift": 5,
      "seed": 42
    }
  }'
```

**Quick preview animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-2-14b-animate-move",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/figure.jpg",
      "video_url": "https://example.com/walking-motion.mp4",
      "resolution": "480p",
      "num_inference_steps": 15,
      "video_quality": "medium",
      "video_write_mode": "fast"
    }
  }'
```

## Related Models

- [wan-v2-2-14b-animate-replace](../wan-v2-2-14b-animate-replace/) - Animate with subject replacement
- [wan-2-5-preview-image-to-video](../wan-2-5-preview-image-to-video/) - Image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
