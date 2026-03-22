---
name: wan-v2-6-text-to-image
description: "Wan | v2.6 | Text to Image. Generate images from text prompts with optional style reference. Triggers: text to image, image generation, wan generate, ai art"
allowed-tools: Bash(curl *), WebFetch
---

# Wan | v2.6 | Text to Image

Generate images from text prompts using the Wan v2.6 model. Supports optional reference images for style guidance, Chinese and English prompts, and content moderation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A mystical forest with bioluminescent mushrooms and fireflies at night",
      "image_size": "landscape_16_9"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| enable_safety_checker | boolean | true | Enable content moderation for input and output. |
| image_size | string | square_hd | Output image size. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9` |
| image_url | string | - | Optional reference image for style guidance. |
| max_images | integer | 1 | Maximum number of images to generate (1-5). |
| negative_prompt | string | - | Content to avoid in the generated image. Max 500 characters. |
| prompt | string | - | Text prompt describing the desired image. Supports Chinese and English. Max 2000 characters. |
| seed | integer | - | Random seed for reproducibility (0-2147483647). |

## Examples

**Simple generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A vintage Porsche 911 parked on a coastal road, cinematic lighting"
    }
  }'
```

**With style reference and multiple outputs:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A serene zen garden with raked sand and carefully placed stones",
      "image_url": "https://example.com/watercolor-style.jpg",
      "negative_prompt": "photorealistic, dark, gloomy",
      "max_images": 3,
      "image_size": "square_hd",
      "seed": 1234
    }
  }'
```

## Related Models

- [Wan | v2.6 | Image to Image](../wan-v2-6-image-to-image/) - Edit images with Wan v2.6
- [Wan | v2.6 | Text to Video](../wan-v2-6-text-to-video/) - Generate video from text with Wan v2.6
- [Wan | v2.6 | Image to Video](../wan-v2-6-image-to-video/) - Generate video from images with Wan v2.6

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
