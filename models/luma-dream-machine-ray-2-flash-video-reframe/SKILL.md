---
name: luma-dream-machine-ray-2-flash-video-reframe
description: "Luma Dream Machine | Ray 2 Flash | Video Reframe. Fast video reframing to different aspect ratios using Luma Ray 2 Flash. Triggers: video reframe fast, luma flash reframe, ray 2 flash reframe, quick video reframe, fast aspect ratio change"
allowed-tools: Bash(curl *), WebFetch
---

# Luma Dream Machine | Ray 2 Flash | Video Reframe

Fast video reframing using Luma Dream Machine Ray 2 Flash. A faster variant of the Ray 2 reframe model, optimized for speed while maintaining quality when converting videos between aspect ratios.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "luma-dream-machine-ray-2-flash-video-reframe",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/horizontal-clip.mp4",
      "aspect_ratio": "9:16"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 9:16 | Target aspect ratio. Options: `1:1`, `16:9`, `9:16`, `4:3`, `3:4`, `21:9`, `9:21` |
| grid_position_x | integer | - | X position of the grid for reframing |
| grid_position_y | integer | - | Y position of the grid for reframing |
| image_url | string | - | Optional URL of the first frame image for reframing |
| prompt | string | - | Optional prompt for reframing |
| video_url | string | - | URL of the input video to reframe |
| x_end | integer | - | End X coordinate for reframing |
| x_start | integer | - | Start X coordinate for reframing |
| y_end | integer | - | End Y coordinate for reframing |
| y_start | integer | - | Start Y coordinate for reframing |

## Examples

**Quick vertical reframe for TikTok/Reels:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "luma-dream-machine-ray-2-flash-video-reframe",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/product-demo.mp4",
      "aspect_ratio": "9:16",
      "prompt": "Focus on the product in the center"
    }
  }'
```

**Square crop for Instagram:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "luma-dream-machine-ray-2-flash-video-reframe",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/interview.mp4",
      "aspect_ratio": "1:1"
    }
  }'
```

## Related Models

- [Luma Dream Machine | Ray 2 | Video Reframe](../luma-dream-machine-ray-2-video-reframe/) - Higher quality variant with more detail
- [PixVerse v4.5 | Extend](../pixverse-v4-5-extend/) - Extend video duration
- [Faceswap | Video](../faceswap-video/) - Swap faces in videos

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
