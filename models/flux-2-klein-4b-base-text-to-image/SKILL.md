---
name: flux-2-klein-4b-base-text-to-image
description: "Flux 2 | Klein | 4B | Base | Text to Image. Generate images from text with a fast lightweight 4B model. Triggers: text to image, fast image generation, flux generate, ai art"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2 | Klein | 4B | Base | Text to Image

Generate images from text prompts using the lightweight Flux 2 Klein 4B Base model. Optimized for speed with only 4 inference steps by default, making it ideal for rapid prototyping and iteration.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-4b-base-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A cozy coffee shop interior with warm lighting and bookshelves",
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
| image_size | string | landscape_4_3 | The size of the image to generate. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9` |
| num_images | integer | 1 | The number of images to generate. |
| num_inference_steps | integer | 4 | The number of inference steps to perform. |
| output_format | string | png | The format of the generated image. Options: `jpeg`, `png`, `webp` |
| prompt | string | - | The prompt to generate an image from. |
| seed | integer | - | The seed to use for the generation. If not provided, a random seed will be used. |

## Examples

**Quick generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-4b-base-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Abstract geometric patterns in blue and gold, digital art"
    }
  }'
```

**Square HD with reproducible seed:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-4b-base-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Photorealistic macro shot of a dewdrop on a leaf",
      "image_size": "square_hd",
      "num_inference_steps": 6,
      "output_format": "webp",
      "seed": 42
    }
  }'
```

## Related Models

- [Flux 2 | Klein | 4B | Base | Edit](../flux-2-klein-4b-base-edit/) - Edit images with the same 4B model
- [Flux 2 | Klein | 9B | Base | Text to Image](../flux-2-klein-9b-base-text-to-image/) - Higher quality 9B variant
- [Flux 2 | Klein | 4B | Text to Image](../flux-2-klein-4b-text-to-image/) - Enhanced 4B variant with guidance and acceleration

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
