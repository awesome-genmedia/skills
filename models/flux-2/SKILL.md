---
name: flux-2
description: "Flux 2. Generate images from text prompts with configurable guidance and acceleration. Triggers: text to image, flux, image generation, fast"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2

Generate high-quality images from text prompts with Flux 2. Features configurable guidance scale, acceleration levels, and prompt expansion for optimal results.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2",
    "version": "0.0.1",
    "input": {
      "prompt": "a stunning architectural photograph of a modern glass building at twilight",
      "image_size": "landscape_4_3",
      "guidance_scale": 2.5,
      "num_inference_steps": 28
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
| image_size | string | landscape_4_3 | The size of the generated image. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9 |
| num_images | integer | 1 | The number of images to generate. |
| num_inference_steps | integer | 28 | The number of inference steps to perform. |
| output_format | string | png | The format of the generated image. enum: jpeg, png, webp |
| prompt | string | | The prompt to generate an image from. |
| seed | integer | | The seed to use for the generation. |

## Examples

**Detailed landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2",
    "version": "0.0.1",
    "input": {
      "prompt": "misty mountain lake at dawn, reflections on still water, photorealistic",
      "image_size": "landscape_16_9",
      "guidance_scale": 3.0,
      "num_inference_steps": 35,
      "output_format": "png",
      "seed": 42
    }
  }'
```

**Fast batch generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2",
    "version": "0.0.1",
    "input": {
      "prompt": "minimalist logo design for a coffee brand, clean lines, modern",
      "image_size": "square_hd",
      "acceleration": "high",
      "num_images": 4,
      "enable_prompt_expansion": true
    }
  }'
```

## Related Models

- [Flux 2 | Edit](../flux-2-edit/) - Image editing with Flux 2
- [Flux 2 Pro](../flux-2-pro/) - Pro-quality generation
- [Flux 2 | Text to Image Lora](../flux-2-lora/) - LoRA-enhanced generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
