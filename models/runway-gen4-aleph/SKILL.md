---
name: "Runway Gen4 Aleph"
description: "Generate videos using Runway Gen4 Aleph from text and optional reference images or video. Trigger: Use when the user wants to create a video with Runway, or requests 'runway gen4', 'runway aleph', 'AI video generation', or 'generate video from prompt'."
allowed-tools: ["Bash"]
---

# Runway Gen4 | Aleph

Generate high-quality videos from text prompts with optional reference images or input video. Supports multiple aspect ratios and reproducible generation with seeds.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "runway-gen4-aleph",
    "version": "0.0.1",
    "input": {
      "prompt": "A cinematic aerial shot of a futuristic city at night with neon lights reflecting on wet streets",
      "aspect_ratio": "1280:720"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | `1280:720` | Video aspect ratio. Options: `1280:720`, `720:1280`, `1104:832`, `832:1104`, `960:960`, `1584:672` |
| `prompt` | string | (empty) | Text prompt for video generation. Max length 1000 |
| `public_figure_moderation` | string | `auto` | Public figure moderation level. Options: `auto`, `low` |
| `reference_images` | array | (empty) | Reference image to influence the style or content of the output |
| `seed` | integer | (empty) | Random seed for reproducible generation |
| `video_url` | string | (empty) | Input video to generate from. Videos must be less than 16MB. Only 5s of the input is used |

## Output

- **Type:** video

## Examples

### Cinematic Scene
```json
{
  "model": "runway-gen4-aleph",
  "version": "0.0.1",
  "input": {
    "prompt": "A lone astronaut walking across a red desert planet with two suns setting on the horizon, cinematic lighting",
    "aspect_ratio": "1280:720",
    "seed": 42
  }
}
```

### Portrait Video with Reference
```json
{
  "model": "runway-gen4-aleph",
  "version": "0.0.1",
  "input": {
    "prompt": "A person walking through a field of wildflowers in slow motion, warm afternoon light",
    "aspect_ratio": "720:1280",
    "reference_images": ["https://example.com/style-reference.jpg"]
  }
}
```

### Video to Video
```json
{
  "model": "runway-gen4-aleph",
  "version": "0.0.1",
  "input": {
    "prompt": "Transform into an anime-style animation with vibrant colors",
    "video_url": "https://example.com/input-clip.mp4",
    "aspect_ratio": "1280:720"
  }
}
```

## Related Models

- [Runway Act-Two](../runway-act-two/SKILL.md) - Performance-driven character animation
- [Moonvalley Marey Text to Video](../moonvalley-marey-text-to-video/SKILL.md) - Alternative text-to-video generation
- [Pixverse v5 Text to Video](../pixverse-v5-text-to-video/SKILL.md) - PixVerse video generation

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
