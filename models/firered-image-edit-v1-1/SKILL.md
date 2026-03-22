---
name: firered-image-edit-v1-1
description: "Firered Image | Edit | v1.1. Edit images with text instructions, multi-image reference, and configurable quality settings. Triggers: image edit, firered, edit image, inpaint, modify"
allowed-tools: Bash(curl *), WebFetch
---

# Firered Image | Edit | v1.1

Edit images using text-based instructions with support for multi-image reference, negative prompts, configurable inference steps, and multiple output formats.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "firered-image-edit-v1-1",
    "version": "0.0.1",
    "input": {
      "prompt": "Change the sky to a dramatic sunset with orange and purple clouds",
      "image_urls": ["https://example.com/landscape.jpg"],
      "image_size": "landscape_16_9",
      "num_inference_steps": 30,
      "guidance_scale": 4
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | regular | Inference speed optimization level. enum: none, regular, high |
| enable_safety_checker | boolean | true | Enable the safety checker for generated images. |
| guidance_scale | number | 4 | Classifier-free guidance scale. Higher values follow the prompt more closely. |
| image_size | string | square_hd | Size of the generated image. If None, uses input image dimensions. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9 |
| image_urls | array | | URLs of the images to edit. Supports single and multi-image reference. |
| negative_prompt | string | | Negative prompt to exclude unwanted content. |
| num_images | integer | 1 | Number of images to generate. |
| num_inference_steps | integer | 30 | Number of inference steps. More steps = higher quality but slower. |
| output_format | string | png | Output image format. enum: jpeg, png |
| prompt | string | | Editing instruction describing what changes to make. |
| seed | string | | Random seed for reproducible results. |

## Examples

**Edit a landscape photo:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "firered-image-edit-v1-1",
    "version": "0.0.1",
    "input": {
      "prompt": "Add a rainbow arching across the sky",
      "image_urls": ["https://example.com/countryside.jpg"],
      "image_size": "landscape_16_9",
      "guidance_scale": 5,
      "num_inference_steps": 40
    }
  }'
```

**Generate multiple variations:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "firered-image-edit-v1-1",
    "version": "0.0.1",
    "input": {
      "prompt": "Transform the room interior to a modern minimalist style",
      "image_urls": ["https://example.com/room.jpg"],
      "negative_prompt": "cluttered, messy, dark",
      "num_images": 3,
      "output_format": "jpeg"
    }
  }'
```

**Fast edit with high acceleration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "firered-image-edit-v1-1",
    "version": "0.0.1",
    "input": {
      "prompt": "Replace the car with a bicycle",
      "image_urls": ["https://example.com/street.jpg"],
      "acceleration": "high",
      "num_inference_steps": 15,
      "seed": "42"
    }
  }'
```

## Related Models

- [p-image-edit-lora-image-edit](../p-image-edit-lora-image-edit/) - Image editing with LoRA weights
- [nano-banana-2-edit](../nano-banana-2-edit/) - Nano Banana image editing
- [xai-grok-imagine-image-edit](../xai-grok-imagine-image-edit/) - Grok image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
