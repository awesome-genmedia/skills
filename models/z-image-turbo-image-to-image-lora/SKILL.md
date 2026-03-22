---
name: z-image-turbo-image-to-image-lora
description: "Z Image | Turbo | Image to Image | Lora. Transform images with LoRA weights using Z Image Turbo. Triggers: image to image, lora, style transfer, z image, ai transform"
allowed-tools: Bash(curl *), WebFetch
---

# Z Image | Turbo | Image to Image | Lora

Transform images using the Z Image Turbo model with LoRA weight support. Combine reference images with text prompts and custom LoRA models for precise style transfers and image-to-image generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-image-to-image-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "Transform into a watercolor painting style",
      "image_url": "https://example.com/photo.jpg",
      "loras": [{"path": "https://example.com/watercolor-lora.safetensors", "scale": 0.8}],
      "strength": 0.6,
      "image_size": "auto",
      "output_format": "png"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | none | The acceleration level to use. Options: `none`, `regular`, `high` |
| enable_prompt_expansion | boolean | false | Whether to enable prompt expansion. |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled. |
| image_size | string | auto | The size of the generated image. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9`, `auto` |
| image_url | string | - | URL of Image for Image-to-Image generation. |
| loras | array | - | List of LoRA weights to apply. |
| num_images | integer | 1 | The number of images to generate. |
| num_inference_steps | integer | 8 | The number of inference steps to perform. |
| output_format | string | png | The format of the generated image. Options: `jpeg`, `png`, `webp` |
| prompt | string | - | The prompt to generate an image from. |
| seed | integer | - | Seed for reproducible generation. |
| strength | number | 0.6 | The strength of the image-to-image conditioning. |

## Examples

**Basic image-to-image with LoRA:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-image-to-image-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "In the style of Studio Ghibli, soft pastel colors",
      "image_url": "https://example.com/landscape.jpg",
      "loras": [{"path": "https://example.com/ghibli-lora.safetensors", "scale": 1.0}]
    }
  }'
```

**Strong transformation with acceleration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-image-to-image-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "Convert to pixel art retro game style",
      "image_url": "https://example.com/character.jpg",
      "loras": [{"path": "https://example.com/pixel-art-lora.safetensors", "scale": 0.9}],
      "strength": 0.8,
      "acceleration": "high",
      "num_inference_steps": 10,
      "output_format": "webp",
      "seed": 42
    }
  }'
```

## Related Models

- [Z Image | Turbo | Lora](../z-image-turbo-lora/) - Text-to-image with LoRA
- [Z Image | Turbo | Controlnet | Lora](../z-image-turbo-controlnet-lora/) - ControlNet with LoRA
- [Z Image | Turbo | Image to Image](../z-image-turbo-image-to-image/) - Image-to-image without LoRA

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
