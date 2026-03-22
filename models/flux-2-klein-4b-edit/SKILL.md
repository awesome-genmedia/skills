---
name: flux-2-klein-4b-edit
description: "Flux 2 | Klein | 4B | Edit. Edit images with the enhanced Flux Klein 4B model with acceleration support. Triggers: image editing, flux edit, fast edit, ai modify"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2 | Klein | 4B | Edit

Edit images using the enhanced Flux 2 Klein 4B model with acceleration support. Combines the speed of the 4B architecture with configurable acceleration levels for optimized performance.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-4b-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Remove the person from the background and fill with natural scenery",
      "image_urls": ["https://example.com/photo.jpg"],
      "image_size": "landscape_16_9",
      "num_inference_steps": 4,
      "output_format": "png"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | regular | The acceleration level to use for image generation. Options: `none`, `regular`, `high` |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled. |
| image_size | string | landscape_16_9 | The size of the generated image. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9` |
| image_urls | array | - | The URLs of the images for editing. A maximum of 4 images are allowed. |
| num_images | integer | 1 | The number of images to generate. |
| num_inference_steps | integer | 4 | The number of inference steps to perform. |
| output_format | string | png | The format of the generated image. Options: `jpeg`, `png`, `webp` |
| prompt | string | - | The prompt to edit the image. |
| seed | integer | - | The seed to use for the generation. If not provided, a random seed will be used. |

## Examples

**Fast edit with high acceleration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-4b-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Add fairy lights to the trees in the garden",
      "image_urls": ["https://example.com/garden.jpg"],
      "acceleration": "high"
    }
  }'
```

**Detailed edit with more steps:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-4b-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Transform the modern building into a medieval castle",
      "image_urls": ["https://example.com/building.jpg"],
      "acceleration": "none",
      "num_inference_steps": 8,
      "image_size": "square_hd",
      "output_format": "jpeg",
      "seed": 999
    }
  }'
```

## Related Models

- [Flux 2 | Klein | 4B | Text to Image](../flux-2-klein-4b-text-to-image/) - Generate images from text with the same 4B model
- [Flux 2 | Klein | 4B | Base | Edit](../flux-2-klein-4b-base-edit/) - Base variant without acceleration
- [Flux 2 | Klein | 9B | Base | Edit](../flux-2-klein-9b-base-edit/) - Higher quality 9B variant

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
