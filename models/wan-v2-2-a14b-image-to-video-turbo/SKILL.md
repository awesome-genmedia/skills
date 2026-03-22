---
name: "Wan v2.2 A14B Image to Video Turbo"
description: "Fast image-to-video generation using Wan v2.2 A14B Turbo. Trigger: Use when the user wants fast image animation, or requests 'wan turbo image to video', 'fast image animation', or 'quick video from image'."
allowed-tools: ["Bash"]
---

# Wan | v2.2 A14B | Image to Video | Turbo

Quickly animate a still image into a video using the Turbo variant of Wan v2.2. Faster generation with simplified controls compared to the standard version.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-2-a14b-image-to-video-turbo",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/scene.jpg",
      "prompt": "Camera slowly zooms in as leaves fall gently",
      "resolution": "720p",
      "aspect_ratio": "16:9"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `acceleration` | string | `regular` | Acceleration level. Options: `none`, `regular` |
| `aspect_ratio` | string | `auto` | Aspect ratio. `auto` derives from input. Options: `auto`, `16:9`, `9:16`, `1:1` |
| `enable_prompt_expansion` | boolean | `false` | Whether to expand the prompt using an LLM |
| `enable_safety_checker` | boolean | `false` | If true, input data will be checked for safety |
| `end_image_url` | string | `false` | URL of the end image for interpolation |
| `image_url` | string | (empty) | URL of the input image |
| `prompt` | string | (empty) | The text prompt to guide video generation |
| `resolution` | string | `720p` | Resolution. Options: `480p`, `580p`, `720p` |
| `seed` | integer | (empty) | Random seed for reproducibility |

## Output

- **Type:** video

## Examples

### Quick Landscape Animation
```json
{
  "model": "wan-v2-2-a14b-image-to-video-turbo",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/mountain-view.jpg",
    "prompt": "Clouds drift slowly across the sky, gentle breeze through the trees",
    "resolution": "720p",
    "aspect_ratio": "16:9"
  }
}
```

### Portrait Animation
```json
{
  "model": "wan-v2-2-a14b-image-to-video-turbo",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/portrait-photo.jpg",
    "prompt": "Subtle hair movement and blinking, natural head sway",
    "resolution": "720p",
    "aspect_ratio": "9:16",
    "seed": 42
  }
}
```

## Related Models

- [Wan v2.2 A14B Image to Video](../wan-v2-2-a14b-image-to-video/SKILL.md) - Full-featured image-to-video with more controls
- [Wan v2.2 A14B Text to Video Turbo](../wan-v2-2-a14b-text-to-video-turbo/SKILL.md) - Fast text-to-video generation
- [PixVerse v5 Image to Video](../pixverse-v5-image-to-video/SKILL.md) - Alternative image-to-video

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
