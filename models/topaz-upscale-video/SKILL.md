---
name: topaz-upscale-video
description: "Topaz Upscale Video. Upscale videos with optional frame interpolation. Triggers: video upscaling, topaz, enhance, super resolution, upscale"
allowed-tools: Bash(curl *), WebFetch
---

# Topaz Upscale Video

Upscale videos with configurable scale factor and optional frame interpolation for smoother playback. Supports H264 and H265 output codecs.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "topaz-upscale-video",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/low-res-video.mp4",
      "upscale_factor": 2
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| H264_output | boolean | false | Whether to use H264 codec for output video. Default is H265. |
| target_fps | integer | | Target FPS for frame interpolation. If set, frame interpolation will be enabled. |
| upscale_factor | number | 2 | Factor to upscale the video by (e.g. 2.0 doubles width and height). |
| video_url | string | | URL of the video to upscale. |

## Examples

**2x upscale with frame interpolation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "topaz-upscale-video",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/video-720p.mp4",
      "upscale_factor": 2,
      "target_fps": 60
    }
  }'
```

**H264 compatible upscale:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "topaz-upscale-video",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/old-footage.mp4",
      "upscale_factor": 4,
      "H264_output": true
    }
  }'
```

## Related Models

- [Flux Vision Upscaler](../flux-vision-upscaler/) - Image upscaling
- [Topaz Upscale Image](../topaz-upscale-image/) - Image upscaling with Topaz

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
