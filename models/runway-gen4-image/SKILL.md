---
name: runway-gen4-image
description: "Runway | Gen4 | Image. Generate images from text prompts using Runway Gen4. AI image generation with reference image support and multiple aspect ratios. Triggers: runway gen4 image, runway image, gen4 image, runway generate image, ai image generation runway"
allowed-tools: Bash(curl *), WebFetch
---

# Runway | Gen4 | Image

Generate images from text prompts using Runway Gen4. Supports up to 3 reference images for style and content guidance, with a wide range of aspect ratios and public figure moderation controls.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "runway-gen4-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A mystical underwater temple with bioluminescent coral and ancient stone pillars",
      "aspect_ratio": "1920:1080"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1024:1024 | Output dimensions. Options: `1920:1080`, `1080:1920`, `1024:1024`, `1360:768`, `1080:1080`, `1168:880`, `1440:1080`, `1080:1440`, `1808:768`, `2112:912`, `1280:720`, `720:1280`, `720:720`, `960:720`, `720:960`, `1680:720` |
| prompt | string | - | Text prompt for image generation |
| public_figure_moderation | string | auto | Public figure handling. Options: `auto`, `low` |
| reference_image_1 | string | - | First reference image URL |
| reference_image_2 | string | - | Second reference image URL |
| reference_image_3 | string | - | Third reference image URL |
| seed | integer | - | Random seed for reproducible results |

## Examples

**Widescreen landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "runway-gen4-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A vast alien desert with twin suns setting, purple and orange sky, crystalline rock formations",
      "aspect_ratio": "1920:1080",
      "seed": 42
    }
  }'
```

**Image with reference style:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "runway-gen4-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A cozy coffee shop interior in the same style as the reference",
      "reference_image_1": "https://example.com/style-reference.jpg",
      "aspect_ratio": "1360:768"
    }
  }'
```

## Related Models

- [Runway | Gen4 | Turbo](../gen4-turbo/) - Generate videos with Runway Gen4
- [Qwen Image](../qwen-image/) - Qwen text-to-image
- [Imagen 4 | Fast](../imagen-4-fast/) - Google's fast image generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
