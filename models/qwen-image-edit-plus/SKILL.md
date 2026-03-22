---
name: qwen-image-edit-plus
description: "Qwen | Image Edit Plus. Edit images using AI with advanced controls and multi-image support. Triggers: qwen, image edit, edit image, image editing, qwen edit plus"
allowed-tools: Bash(curl *), WebFetch
---

# Qwen | Image Edit Plus

Edit images using the Qwen Image Edit Plus model with advanced controls including guidance scale, inference steps, safety checker, and multi-image editing support. Produces high-quality edits with configurable output sizes and formats.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "qwen-image-edit-plus",
    "version": "0.0.1",
    "input": {
      "prompt": "Change the background to a tropical beach at sunset",
      "image_urls": ["https://example.com/portrait.jpg"],
      "image_size": "landscape_16_9",
      "num_images": 1,
      "output_format": "png"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | regular | Acceleration level for image generation. enum: none, regular |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled |
| guidance_scale | number | 4 | CFG (Classifier Free Guidance) scale for prompt adherence |
| image_size | string | square_hd | The size of the generated image. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9 |
| image_urls | array | | The URLs of the images to edit |
| negative_prompt | string | | The negative prompt for the generation |
| num_images | integer | 1 | The number of images to generate |
| num_inference_steps | integer | 50 | The number of inference steps to perform |
| output_format | string | png | The format of the generated image. enum: jpeg, png |
| prompt | string | | The prompt to generate the image with |
| seed | integer | | Seed for reproducible results |

## Examples

**Background replacement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "qwen-image-edit-plus",
    "version": "0.0.1",
    "input": {
      "prompt": "Replace the background with a modern office interior",
      "image_urls": ["https://example.com/headshot.jpg"],
      "image_size": "square_hd",
      "guidance_scale": 5,
      "num_inference_steps": 50,
      "output_format": "png"
    }
  }'
```

**Style transfer with multiple outputs:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "qwen-image-edit-plus",
    "version": "0.0.1",
    "input": {
      "prompt": "Transform into a watercolor painting style with soft pastel colors",
      "image_urls": ["https://example.com/landscape.jpg"],
      "image_size": "landscape_16_9",
      "num_images": 3,
      "guidance_scale": 4,
      "negative_prompt": "blurry, low quality, distorted",
      "seed": 42
    }
  }'
```

## Related Models

- [qwen-ai-image-edit](../qwen-ai-image-edit/) - Standard Qwen image editing
- [reve-edit](../reve-edit/) - Reve image editing
- [flux-kontext-dev](../flux-kontext-dev/) - Flux Kontext image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
