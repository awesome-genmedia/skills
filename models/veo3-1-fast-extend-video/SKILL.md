---
name: veo3-1-fast-extend-video
description: "Veo 3.1 | Fast | Extend Video. Quickly extend an existing video with AI-generated continuation. Triggers: extend video fast, video extension, veo fast, quick extend"
allowed-tools: Bash(curl *), WebFetch
---

# Veo 3.1 | Fast | Extend Video

Quickly extend an existing video using Google's Veo 3.1 Fast model. A faster alternative to the standard Veo 3.1 Extend Video, with the same feature set including audio generation and auto-fix.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-fast-extend-video",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/clip.mp4",
      "prompt": "The scene transitions to a wide shot as the sun begins to set",
      "duration": "7",
      "generate_audio": true,
      "resolution": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | auto | The aspect ratio of the generated video. Options: `auto`, `16:9`, `9:16` |
| auto_fix | boolean | false | Whether to automatically attempt to fix prompts that fail content policy. |
| duration | string | 7 | The duration of the generated video. Options: `7` |
| generate_audio | boolean | true | Whether to generate audio for the video. |
| prompt | string | - | The text prompt describing how the video should be extended. |
| resolution | string | 720p | The resolution of the generated video. Options: `720p` |
| video_url | string | - | URL of the video to extend. The video should be 720p or 1080p resolution in 16:9 or 9:16. |

## Examples

**Quick video extension:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-fast-extend-video",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/action-scene.mp4",
      "prompt": "The car speeds around the corner and disappears down the highway"
    }
  }'
```

**Extension with auto-fix:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-fast-extend-video",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/tutorial-video.mp4",
      "prompt": "The presenter gestures toward the screen and the animation plays",
      "auto_fix": true,
      "generate_audio": true,
      "aspect_ratio": "16:9"
    }
  }'
```

## Related Models

- [Veo 3.1 | Extend Video](../veo3-1-extend-video/) - Standard quality video extension
- [Veo 3.1 | Text to Video | Fast](../veo3-1-text-to-video-fast/) - Fast text to video generation
- [Veo 3.1 | Image to Video | Fast](../veo3-1-image-to-video-fast/) - Fast image to video generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
