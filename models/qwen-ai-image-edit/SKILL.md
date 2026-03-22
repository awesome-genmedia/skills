---
name: qwen-ai-image-edit
description: "Qwen Image Edit. Edit images using AI with prompt-based instructions using the Qwen model. Triggers: qwen, image edit, edit image, image editing, qwen edit"
allowed-tools: Bash(curl *), WebFetch
---

# Qwen Image Edit

Edit images with prompt-based instructions using the Qwen model. Supports acceleration modes, configurable guidance scale, inference steps, negative prompts, and multiple output sizes and formats.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "qwen-ai-image-edit",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/room-photo.jpg",
      "prompt": "Change the furniture to mid-century modern style",
      "image_size": "landscape_16_9",
      "output_format": "png"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | regular | Acceleration level. enum: none, regular, high |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled |
| guidance_scale | number | 4 | CFG scale for prompt adherence |
| image_size | string | | The size of the generated image. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9 |
| image_url | string | | The URL of the image to edit |
| negative_prompt | string | | The negative prompt for the generation |
| num_images | integer | 1 | The number of images to generate |
| num_inference_steps | integer | 30 | The number of inference steps to perform |
| output_format | string | png | The format of the generated image. enum: jpeg, png |
| prompt | string | | The prompt to generate the image with |
| seed | integer | | Seed for reproducible results |

## Examples

**Object modification with high acceleration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "qwen-ai-image-edit",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/car-photo.jpg",
      "prompt": "Change the car color to metallic blue",
      "acceleration": "high",
      "guidance_scale": 5,
      "num_inference_steps": 30,
      "output_format": "jpeg"
    }
  }'
```

**Detailed edit with negative prompt:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "qwen-ai-image-edit",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/garden.jpg",
      "prompt": "Add a wooden bench under the large tree",
      "image_size": "landscape_4_3",
      "negative_prompt": "blurry, low quality, distorted",
      "num_images": 2,
      "guidance_scale": 4,
      "seed": 42
    }
  }'
```

## Related Models

- [qwen-image-edit-plus](../qwen-image-edit-plus/) - Advanced Qwen image editing with multi-image support
- [flux-kontext-dev](../flux-kontext-dev/) - Flux-based image editing
- [reve-edit](../reve-edit/) - Reve image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
