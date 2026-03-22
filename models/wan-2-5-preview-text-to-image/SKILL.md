---
name: wan-2-5-preview-text-to-image
description: "Wan | 2.5 | Preview | Text to Image. Generate images from text prompts using the Wan 2.5 Preview model with prompt expansion. Triggers: wan, text to image, image generation, wan 2.5"
allowed-tools: Bash(curl *), WebFetch
---

# Wan | 2.5 | Preview | Text to Image

Generate high-quality images from text descriptions using the Wan 2.5 Preview model. Supports Chinese and English prompts, LLM-based prompt expansion for better results, and multiple output sizes.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-2-5-preview-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A cozy bookshop interior with warm lighting, tall wooden shelves filled with colorful books, a cat sleeping on an armchair",
      "image_size": "landscape_16_9",
      "num_images": 1,
      "enable_prompt_expansion": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| enable_prompt_expansion | boolean | true | Whether to enable LLM-based prompt rewriting for improved results |
| image_size | string | square_hd | The size of the generated image. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9 |
| negative_prompt | string | | Negative prompt to describe content to avoid (max 500 chars) |
| num_images | integer | 1 | Number of images to generate (1-4) |
| prompt | string | | The prompt for image generation. Supports Chinese and English (max 2000 chars) |
| seed | integer | | Random seed for reproducibility |

## Examples

**Detailed scene with negative prompt:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-2-5-preview-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Futuristic underwater city with bioluminescent buildings, transparent domes, and schools of colorful fish swimming between structures",
      "negative_prompt": "blurry, low quality, text, watermark, deformed",
      "image_size": "landscape_4_3",
      "num_images": 2,
      "enable_prompt_expansion": true
    }
  }'
```

**Chinese prompt with seed:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-2-5-preview-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A traditional Chinese mountain landscape in ink wash painting style with misty peaks and a small boat on the river",
      "image_size": "portrait_16_9",
      "num_images": 1,
      "seed": 88888,
      "enable_prompt_expansion": false
    }
  }'
```

## Related Models

- [wan-2-5-preview-image-to-image](../wan-2-5-preview-image-to-image/) - Image to image editing
- [wan-2-5-preview-text-to-video](../wan-2-5-preview-text-to-video/) - Text to video
- [wan-2-5-preview-image-to-video](../wan-2-5-preview-image-to-video/) - Image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
