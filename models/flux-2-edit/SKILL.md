---
name: flux-2-edit
description: "Flux 2 | Edit. Edit images with text prompts and configurable guidance. Triggers: image editing, flux, photo edit, inpainting"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2 | Edit

Edit images using text prompts with Flux 2. Supports up to 3 input images, configurable guidance scale, and acceleration levels.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "add a colorful hot air balloon to the sky",
      "image_urls": ["https://example.com/landscape.jpg"],
      "guidance_scale": 2.5,
      "image_size": "landscape_4_3"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | regular | The acceleration level to use. enum: none, regular, high |
| enable_prompt_expansion | boolean | false | If set to true, the prompt will be expanded for better results. |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled. |
| guidance_scale | number | 2.5 | Guidance Scale controls how closely the model follows your prompt. |
| image_size | string | square_hd | The size of the image to generate. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9 |
| image_urls | array | | The URLs of the images for editing. Maximum of 3 images. |
| num_images | integer | 1 | The number of images to generate. |
| num_inference_steps | integer | 28 | The number of inference steps to perform. |
| output_format | string | png | The format of the generated image. enum: jpeg, png, webp |
| prompt | string | | The prompt to edit the image. |
| seed | integer | | The seed to use for the generation. |

## Examples

**Object addition:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "add a small wooden bridge over the stream",
      "image_urls": ["https://example.com/garden.jpg"],
      "guidance_scale": 3.0,
      "image_size": "landscape_4_3",
      "output_format": "png",
      "num_inference_steps": 30
    }
  }'
```

**Fast editing with acceleration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "change the wall color to warm terracotta",
      "image_urls": ["https://example.com/room.jpg"],
      "acceleration": "high",
      "num_images": 2,
      "seed": 42
    }
  }'
```

## Related Models

- [Flux 2](../flux-2/) - Standard text-to-image generation
- [Flux 2 | Lora Edit](../flux-2-lora-edit/) - LoRA-based editing
- [Flux 2 Pro | Edit](../flux-2-pro-edit/) - Pro-tier editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
