---
name: wan-v2-6-image-to-image
description: "Wan | v2.6 | Image to Image. Edit and transform images using reference images with the Wan v2.6 model. Triggers: image to image, image editing, wan edit, style transfer"
allowed-tools: Bash(curl *), WebFetch
---

# Wan | v2.6 | Image to Image

Edit and transform images using reference images with the Wan v2.6 model. Supports LLM prompt expansion, multiple reference images, and Chinese/English prompts for versatile image editing.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-image-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Transform this photo into an oil painting style with vivid autumn colors",
      "image_urls": ["https://example.com/landscape.jpg"],
      "image_size": "square_hd",
      "enable_prompt_expansion": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| enable_prompt_expansion | boolean | true | Enable LLM prompt optimization. Significantly improves results for simple prompts. |
| enable_safety_checker | boolean | true | Enable content moderation for input and output. |
| image_size | string | square_hd | Output image size. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9` |
| image_urls | array | - | Reference images for editing (1-3 images required). Order matters. |
| negative_prompt | string | - | Content to avoid in the generated image. Max 500 characters. |
| num_images | integer | 1 | Number of images to generate (1-4). |
| prompt | string | - | Text prompt describing the desired image. Supports Chinese and English. Max 2000 characters. |
| seed | integer | - | Random seed for reproducibility (0-2147483647). |

## Examples

**Simple style transfer:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-image-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Convert to anime style illustration",
      "image_urls": ["https://example.com/portrait.jpg"]
    }
  }'
```

**Multi-reference editing with negative prompt:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-image-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Combine the style of the first image with the composition of the second",
      "image_urls": ["https://example.com/style-ref.jpg", "https://example.com/composition-ref.jpg"],
      "negative_prompt": "blurry, low quality, distorted",
      "num_images": 2,
      "image_size": "landscape_16_9",
      "seed": 42
    }
  }'
```

## Related Models

- [Wan | v2.6 | Text to Image](../wan-v2-6-text-to-image/) - Generate images from text with Wan v2.6
- [Wan | v2.6 | Image to Video](../wan-v2-6-image-to-video/) - Generate video from images with Wan v2.6
- [Wan | v2.6 | Text to Video](../wan-v2-6-text-to-video/) - Generate video from text with Wan v2.6

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
