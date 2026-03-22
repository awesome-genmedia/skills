---
name: "Minimax Subject Reference"
description: "Generate images with consistent subject appearance using Minimax. Trigger: Use when the user wants to generate images with a consistent character, or requests 'minimax subject reference', 'consistent character image', or 'subject reference generation'."
allowed-tools: ["Bash"]
---

# Minimax | Subject Reference

Generate images with consistent subject appearance by providing a reference image. Create new scenes with the same character maintaining visual consistency.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-subject-reference",
    "version": "0.0.1",
    "input": {
      "prompt": "The character standing on a mountain top at sunrise",
      "image_url": "https://example.com/character-reference.jpg",
      "aspect_ratio": "16:9",
      "num_images": 1
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | `1:1` | Aspect ratio. Options: `1:1`, `16:9`, `4:3`, `3:2`, `2:3`, `3:4`, `9:16`, `21:9` |
| `image_url` | string | `false` | URL of the subject reference image for consistent character appearance |
| `num_images` | integer | `1` | Number of images to generate |
| `prompt` | string | `false` | Text prompt for image generation |
| `prompt_optimizer` | boolean | `false` | Enable automatic prompt optimization |

## Output

- **Type:** image

## Examples

### Character in New Scene
```json
{
  "model": "minimax-subject-reference",
  "version": "0.0.1",
  "input": {
    "prompt": "The character sitting at a cafe in Paris with the Eiffel Tower in the background",
    "image_url": "https://example.com/my-character.jpg",
    "aspect_ratio": "16:9",
    "num_images": 2,
    "prompt_optimizer": true
  }
}
```

### Portrait with Reference
```json
{
  "model": "minimax-subject-reference",
  "version": "0.0.1",
  "input": {
    "prompt": "Professional headshot in a modern office, warm lighting",
    "image_url": "https://example.com/person-photo.jpg",
    "aspect_ratio": "3:4",
    "num_images": 1
  }
}
```

## Related Models

- [Ideogram Character](../ideogram-character/SKILL.md) - Character-consistent generation with Ideogram
- [Imagen 4 Preview](../imagen4-preview/SKILL.md) - General text-to-image generation
- [Seedream V4 Text to Image](../seedream-v4-text-to-image/SKILL.md) - High-quality text-to-image

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
