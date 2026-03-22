---
name: merge-videos
description: "Merge Videos. Merge multiple videos into a single video with configurable resolution and FPS. Triggers: merge videos, combine videos, join videos, video merge, concatenate videos"
allowed-tools: Bash(curl *), WebFetch
---

# Merge Videos

Merge multiple videos into a single output video. Supports configurable resolution and target FPS for the final output.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "merge-videos",
    "version": "0.0.1",
    "input": {
      "video_urls": [
        "https://example.com/clip1.mp4",
        "https://example.com/clip2.mp4",
        "https://example.com/clip3.mp4"
      ],
      "resolution": "landscape_16_9",
      "target_fps": 30
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| resolution | string | | Resolution of the final video. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9 |
| target_fps | integer | | Target FPS for the output video. If not provided, uses the lowest FPS from input videos |
| video_urls | array | | List of video URLs to merge in order |

## Examples

**Merge two clips in widescreen:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "merge-videos",
    "version": "0.0.1",
    "input": {
      "video_urls": [
        "https://example.com/intro.mp4",
        "https://example.com/main-content.mp4"
      ],
      "resolution": "landscape_16_9",
      "target_fps": 24
    }
  }'
```

**Merge vertical clips for social media:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "merge-videos",
    "version": "0.0.1",
    "input": {
      "video_urls": [
        "https://example.com/scene1.mp4",
        "https://example.com/scene2.mp4",
        "https://example.com/scene3.mp4",
        "https://example.com/outro.mp4"
      ],
      "resolution": "portrait_16_9"
    }
  }'
```

## Related Models

- [veo3-1-text-to-video](../veo3-1-text-to-video/) - Generate video clips to merge
- [heygen-video-translate](../heygen-video-translate/) - Translate merged videos

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
