---
name: "PixVerse v5 Extend"
description: "Extend existing videos using PixVerse v5. Trigger: Use when the user wants to extend a video, or requests 'pixverse extend', 'extend video', 'make video longer', or 'continue video'."
allowed-tools: ["Bash"]
---

# PixVerse v5 | Extend

Extend an existing video by generating additional frames. Control duration, quality, and visual style of the extension.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-extend",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/short-clip.mp4",
      "prompt": "Continue the scene with the camera panning right to reveal a garden",
      "duration": 8,
      "quality": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `duration` | integer | `8` | Duration of the extended video |
| `motion_mode` | string | `normal` | Motion mode. Options: `normal` |
| `negative_prompt` | string | `false` | Things to avoid in the video |
| `prompt` | string | `false` | Text prompt guiding the extension |
| `quality` | string | `720p` | Resolution quality. Options: `360p`, `540p`, `720p`, `1080p` |
| `seed` | integer | `false` | Random seed for reproducibility |
| `style` | string | `false` | Visual style. Options: `anime`, `3d_animation`, `clay`, `comic`, `cyberpunk` |
| `video_url` | string | `false` | URL of the video to extend |

## Output

- **Type:** video

## Examples

### Extend with Action
```json
{
  "model": "pixverse-v5-extend",
  "version": "0.0.1",
  "input": {
    "video_url": "https://example.com/car-driving.mp4",
    "prompt": "The car accelerates and speeds through a winding mountain road",
    "duration": 8,
    "quality": "1080p"
  }
}
```

### Extend with Style
```json
{
  "model": "pixverse-v5-extend",
  "version": "0.0.1",
  "input": {
    "video_url": "https://example.com/character-scene.mp4",
    "prompt": "The character turns and walks into the sunset",
    "duration": 8,
    "quality": "720p",
    "style": "anime",
    "seed": 42
  }
}
```

## Related Models

- [PixVerse v5 Text to Video](../pixverse-v5-text-to-video/SKILL.md) - Generate videos from text
- [PixVerse v5 Image to Video](../pixverse-v5-image-to-video/SKILL.md) - Generate videos from images
- [PixVerse v5 Transition](../pixverse-v5-transition/SKILL.md) - Create transitions between images

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
