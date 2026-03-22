---
name: extract-frame
description: "Extract Frame. Extract the first, middle, or last frame from a video as an image. Triggers: extract frame, video frame, video to image, screenshot video, thumbnail"
allowed-tools: Bash(curl *), WebFetch
---

# Extract Frame

Extract a single frame from a video file. Choose to extract the first, middle, or last frame, returning it as an image.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "extract-frame",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/video-clip.mp4",
      "frame_type": "first"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| frame_type | string | first | Type of frame to extract. Options: `first`, `middle`, `last` |
| video_url | string | - | URL of the video file to extract a frame from. |

## Examples

**Extract first frame:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "extract-frame",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/presentation.mp4",
      "frame_type": "first"
    }
  }'
```

**Extract middle frame for thumbnail:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "extract-frame",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/music-video.mp4",
      "frame_type": "middle"
    }
  }'
```

**Extract last frame:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "extract-frame",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/timelapse.mp4",
      "frame_type": "last"
    }
  }'
```

## Related Models

- [Ffmpeg Api | Merge Audio Video](../ffmpeg-api-merge-audio-video/) - Merge audio and video tracks
- [Crop Image](../crop-image/) - Crop extracted frames

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
