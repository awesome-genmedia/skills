---
name: luma-dream-machine-ray-2-video-reframe
description: "Luma Dream Machine | Ray 2 | Video Reframe. Reframe videos to different aspect ratios using Luma Ray 2 AI. Triggers: video reframe, luma reframe, ray 2 reframe, change aspect ratio, reframe video, video crop ai, luma dream machine"
allowed-tools: Bash(curl *), WebFetch
---

# Luma Dream Machine | Ray 2 | Video Reframe

Reframe videos to different aspect ratios using Luma Dream Machine Ray 2. Intelligently reframes video content while preserving key subjects and composition, with optional prompt guidance for creative control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "luma-dream-machine-ray-2-video-reframe",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/landscape-video.mp4",
      "aspect_ratio": "9:16"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 9:16 | The aspect ratio of the reframed video. Options: `1:1`, `16:9`, `9:16`, `4:3`, `3:4`, `21:9`, `9:21` |
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

**Reframe landscape video to vertical for social media:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "luma-dream-machine-ray-2-video-reframe",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/travel-vlog.mp4",
      "aspect_ratio": "9:16",
      "prompt": "Keep the person centered in frame"
    }
  }'
```

**Reframe to cinematic widescreen:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "luma-dream-machine-ray-2-video-reframe",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/nature-scene.mp4",
      "aspect_ratio": "21:9"
    }
  }'
```

**Reframe with custom coordinates:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "luma-dream-machine-ray-2-video-reframe",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/group-video.mp4",
      "aspect_ratio": "1:1",
      "x_start": 100,
      "y_start": 50,
      "x_end": 500,
      "y_end": 450
    }
  }'
```

## Related Models

- [Luma Dream Machine | Ray 2 Flash | Video Reframe](../luma-dream-machine-ray-2-flash-video-reframe/) - Faster variant for quick reframes
- [PixVerse v4.5 | Extend](../pixverse-v4-5-extend/) - Extend video duration
- [Google Veo 3](../veo-3/) - Text-to-video generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
