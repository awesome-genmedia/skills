---
name: flux-2-klein-4b-base-edit
description: "Flux 2 | Klein | 4B | Base | Edit. Edit images with a lightweight 4B parameter Flux model. Triggers: image editing, flux edit, quick edit, ai modify image"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2 | Klein | 4B | Base | Edit

Edit images using the lightweight Flux 2 Klein 4B Base model. A faster alternative to the 9B variant with fewer inference steps required, ideal for quick image modifications.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-4b-base-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Change the wall color to a warm terracotta",
      "image_urls": ["https://example.com/room.jpg"],
      "image_size": "landscape_4_3",
      "num_inference_steps": 4,
      "output_format": "png"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled. |
| image_size | string | landscape_4_3 | The size of the generated image. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9` |
| image_urls | array | - | The URLs of the images for editing. A maximum of 4 images are allowed. |
| num_images | integer | 1 | The number of images to generate. |
| num_inference_steps | integer | 4 | The number of inference steps to perform. |
| output_format | string | png | The format of the generated image. Options: `jpeg`, `png`, `webp` |
| prompt | string | - | The prompt to edit the image. |
| seed | integer | - | The seed to use for the generation. If not provided, a random seed will be used. |

## Examples

**Quick image edit:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-4b-base-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Add sunglasses to the person",
      "image_urls": ["https://example.com/selfie.jpg"]
    }
  }'
```

**Edit with specific output settings:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-4b-base-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Turn the daytime scene into a snowy winter landscape",
      "image_urls": ["https://example.com/park.jpg"],
      "image_size": "landscape_16_9",
      "num_inference_steps": 6,
      "output_format": "jpeg",
      "seed": 777
    }
  }'
```

## Related Models

- [Flux 2 | Klein | 4B | Base | Text to Image](../flux-2-klein-4b-base-text-to-image/) - Generate images from text with the 4B model
- [Flux 2 | Klein | 9B | Base | Edit](../flux-2-klein-9b-base-edit/) - Higher quality 9B variant for editing
- [Flux 2 | Klein | 4B | Edit](../flux-2-klein-4b-edit/) - Enhanced 4B edit variant with acceleration support

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
