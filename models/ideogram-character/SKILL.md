---
name: "Ideogram Character"
description: "Generate character-consistent images using Ideogram with optional inpainting. Trigger: Use when the user wants to create character images, or requests 'ideogram character', 'consistent character', or 'ideogram image generation'."
allowed-tools: ["Bash"]
---

# Ideogram | Character

Generate images with consistent character appearance using Ideogram. Supports character reference images, inpainting with masks, multiple style types, and a wide range of resolutions.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ideogram-character",
    "version": "0.0.1",
    "input": {
      "prompt": "A heroic fantasy warrior standing on a cliff overlooking a vast kingdom",
      "aspect_ratio": "4:3",
      "style_type": "Fiction",
      "rendering_speed": "Default"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | `1:1` | Aspect ratio. Options: `1:3`, `3:1`, `1:2`, `2:1`, `9:16`, `16:9`, `10:16`, `16:10`, `2:3`, `3:2`, `3:4`, `4:3`, `4:5`, `5:4`, `1:1` |
| `character_reference_image` | string | (empty) | An image to use as a character reference |
| `image` | string | (empty) | An image file for inpainting. Must also use a mask |
| `magic_prompt_option` | string | `Auto` | Prompt enhancement. Options: `Auto`, `On`, `Off` |
| `mask` | string | (empty) | A black and white image. Black pixels are inpainted, white pixels are preserved |
| `prompt` | string | (empty) | Text prompt for image generation |
| `rendering_speed` | string | `Default` | Rendering speed. Options: `Default`, `Turbo`, `Quality` |
| `resolution` | string | `None` | Specific resolution. Options: `None` (auto), plus many specific resolutions from `512x1536` to `1536x640` |
| `seed` | integer | (empty) | Random seed for reproducible generation |
| `style_type` | string | `Auto` | Visual style. Options: `Auto`, `Fiction`, `Realistic` |

## Output

- **Type:** image

## Examples

### Character with Reference
```json
{
  "model": "ideogram-character",
  "version": "0.0.1",
  "input": {
    "prompt": "A detective investigating a crime scene in a noir-style alley",
    "character_reference_image": "https://example.com/my-character.jpg",
    "aspect_ratio": "16:9",
    "style_type": "Realistic",
    "rendering_speed": "Quality"
  }
}
```

### Fiction Art
```json
{
  "model": "ideogram-character",
  "version": "0.0.1",
  "input": {
    "prompt": "An elven archer in an enchanted forest with glowing runes",
    "aspect_ratio": "3:4",
    "style_type": "Fiction",
    "magic_prompt_option": "On",
    "seed": 42
  }
}
```

### Inpainting
```json
{
  "model": "ideogram-character",
  "version": "0.0.1",
  "input": {
    "prompt": "A smiling woman in a red dress",
    "image": "https://example.com/scene.jpg",
    "mask": "https://example.com/mask.png",
    "rendering_speed": "Default"
  }
}
```

## Related Models

- [Imagen 4 Preview](../imagen4-preview/SKILL.md) - Google's image generation model
- [Seedream V4 Text to Image](../seedream-v4-text-to-image/SKILL.md) - ByteDance text-to-image
- [Minimax Subject Reference](../minimax-subject-reference/SKILL.md) - Subject-consistent image generation

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
