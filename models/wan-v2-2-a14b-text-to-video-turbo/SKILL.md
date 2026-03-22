---
name: "Wan v2.2 A14B Text to Video Turbo"
description: "Fast text-to-video generation using Wan v2.2 A14B Turbo. Trigger: Use when the user wants fast video from text, or requests 'wan text to video turbo', 'fast video generation', or 'quick text to video'."
allowed-tools: ["Bash"]
---

# Wan | v2.2 A14B | Text to Video | Turbo

Generate videos from text prompts using the Turbo variant of Wan v2.2 for faster output. Supports multiple resolutions and aspect ratios.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-2-a14b-text-to-video-turbo",
    "version": "0.0.1",
    "input": {
      "prompt": "A golden retriever running through a meadow chasing butterflies",
      "resolution": "720p",
      "aspect_ratio": "16:9"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `acceleration` | string | `none` | Acceleration level. Options: `none`, `regular` |
| `aspect_ratio` | string | `16:9` | Aspect ratio. Options: `16:9`, `9:16`, `1:1` |
| `enable_prompt_expansion` | boolean | `false` | Whether to expand the prompt using an LLM |
| `enable_safety_checker` | boolean | `false` | If true, input data will be checked for safety |
| `prompt` | string | `false` | The text prompt to guide video generation |
| `resolution` | string | `720p` | Resolution. Options: `480p`, `580p`, `720p` |
| `seed` | integer | `false` | Random seed for reproducibility |

## Output

- **Type:** video

## Examples

### Nature Scene
```json
{
  "model": "wan-v2-2-a14b-text-to-video-turbo",
  "version": "0.0.1",
  "input": {
    "prompt": "A serene lake reflecting autumn trees, with a gentle breeze creating ripples on the water surface",
    "resolution": "720p",
    "aspect_ratio": "16:9",
    "acceleration": "regular"
  }
}
```

### Vertical Social Content
```json
{
  "model": "wan-v2-2-a14b-text-to-video-turbo",
  "version": "0.0.1",
  "input": {
    "prompt": "A dancer performing graceful ballet moves in a dimly lit studio",
    "resolution": "720p",
    "aspect_ratio": "9:16",
    "seed": 123
  }
}
```

## Related Models

- [Wan v2.2 A14B Image to Video Turbo](../wan-v2-2-a14b-image-to-video-turbo/SKILL.md) - Fast image-to-video
- [Wan v2.2 A14B Image to Video](../wan-v2-2-a14b-image-to-video/SKILL.md) - Full-featured image-to-video
- [Runway Gen4 Aleph](../runway-gen4-aleph/SKILL.md) - Alternative text-to-video

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
