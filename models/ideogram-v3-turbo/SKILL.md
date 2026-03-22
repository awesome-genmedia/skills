---
name: ideogram-v3-turbo
description: "Ideogram V3 | Turbo. Generate images with accurate text rendering using Ideogram V3 Turbo. Fast AI image generation with excellent typography. Triggers: ideogram, ideogram v3, text in image, typography image, ideogram turbo, generate image with text, ai text rendering"
allowed-tools: Bash(curl *), WebFetch
---

# Ideogram V3 | Turbo

Generate images with accurate text rendering using Ideogram V3 Turbo. Known for excellent typography and text rendering in generated images, with support for inpainting, magic prompt enhancement, multiple style types, and fine-grained resolution control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ideogram-v3-turbo",
    "version": "0.0.1",
    "input": {
      "prompt": "A neon sign that reads \"OPEN 24 HOURS\" glowing in a rainy city street at night",
      "aspect_ratio": "16:9",
      "style_type": "Realistic"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | Image aspect ratio. Options: `1:3`, `3:1`, `1:2`, `2:1`, `9:16`, `16:9`, `10:16`, `16:10`, `2:3`, `3:2`, `3:4`, `4:3`, `4:5`, `5:4`, `1:1` |
| image | string | - | Input image for inpainting (must also provide a mask) |
| magic_prompt_option | string | Auto | Prompt enhancement. Options: `Auto`, `On`, `Off` |
| mask | string | - | Black and white mask image. Black pixels are inpainted, white pixels are preserved |
| prompt | string | - | Text prompt for image generation |
| resolution | string | None | Specific resolution (many options available, e.g., `1024x1024`, `1920:1080`). Use `None` for automatic |
| seed | integer | - | Random seed for reproducible generation |
| style_type | string | None | Visual style. Options: `None`, `Auto`, `General`, `Realistic`, `Design` |

## Examples

**Logo with text:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ideogram-v3-turbo",
    "version": "0.0.1",
    "input": {
      "prompt": "A minimalist logo design for a coffee shop called \"BREW & CO\" with a coffee cup icon, clean typography, modern design",
      "aspect_ratio": "1:1",
      "style_type": "Design",
      "magic_prompt_option": "On"
    }
  }'
```

**Realistic photo with text overlay:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ideogram-v3-turbo",
    "version": "0.0.1",
    "input": {
      "prompt": "A vintage movie poster for a film called \"THE LAST FRONTIER\" with a cowboy silhouette against a sunset, Western typography",
      "aspect_ratio": "2:3",
      "style_type": "Realistic",
      "seed": 42
    }
  }'
```

**Inpainting text into an image:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ideogram-v3-turbo",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/storefront.jpg",
      "mask": "https://example.com/sign-mask.png",
      "prompt": "A store sign that reads \"FRESH MARKET\" in elegant gold lettering"
    }
  }'
```

## Related Models

- [Qwen Image](../qwen-image/) - Qwen text-to-image
- [Imagen 4 | Fast](../imagen-4-fast/) - Google's fast image generation
- [Seedream V3 | Text to Image](../seedream-v3-text-to-image/) - ByteDance text-to-image

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
