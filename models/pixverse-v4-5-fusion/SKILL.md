---
name: "PixVerse v4.5 Fusion"
description: "Generate videos by fusing multiple reference images using PixVerse v4.5. Trigger: Use when the user wants to fuse images into a video, or requests 'pixverse fusion', 'image fusion video', or 'combine images into video'."
allowed-tools: ["Bash"]
---

# PixVerse v4.5 | Fusion

Generate videos by fusing multiple reference images together, guided by a text prompt. Combine elements from different images into a cohesive video.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v4-5-fusion",
    "version": "0.0.1",
    "input": {
      "prompt": "A character from the first image walking through the landscape from the second image",
      "image_references": ["https://example.com/character.jpg", "https://example.com/landscape.jpg"],
      "aspect_ratio": "16:9",
      "duration": 5,
      "quality": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | `16:9` | Aspect ratio. Options: `16:9`, `4:3`, `1:1`, `3:4`, `9:16` |
| `duration` | integer | `5` | Duration of the video |
| `image_references` | array | `false` | Reference images to fuse |
| `prompt` | string | `false` | Text prompt guiding the fusion |
| `quality` | string | `540p` | Resolution quality. Options: `360p`, `540p`, `720p`, `1080p` |
| `seed` | integer | `false` | Random seed for reproducibility |

## Output

- **Type:** video

## Examples

### Character in Environment
```json
{
  "model": "pixverse-v4-5-fusion",
  "version": "0.0.1",
  "input": {
    "prompt": "The character walks confidently through the futuristic city",
    "image_references": ["https://example.com/hero-character.jpg", "https://example.com/scifi-city.jpg"],
    "aspect_ratio": "16:9",
    "duration": 5,
    "quality": "1080p"
  }
}
```

### Multi-Element Composition
```json
{
  "model": "pixverse-v4-5-fusion",
  "version": "0.0.1",
  "input": {
    "prompt": "A mystical scene combining the elements from all reference images",
    "image_references": ["https://example.com/castle.jpg", "https://example.com/dragon.jpg", "https://example.com/wizard.jpg"],
    "aspect_ratio": "16:9",
    "duration": 5,
    "quality": "720p",
    "seed": 42
  }
}
```

## Related Models

- [PixVerse v5 Text to Video](../pixverse-v5-text-to-video/SKILL.md) - Generate videos from text
- [PixVerse v5 Image to Video](../pixverse-v5-image-to-video/SKILL.md) - Animate single images
- [PixVerse v5 Transition](../pixverse-v5-transition/SKILL.md) - Create transitions between images

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
