---
name: bfl-flux-lora
description: "Flux Lora. Generate images with LoRA weights from BFL. Triggers: text to image, flux, lora, bfl, image generation, fine-tuned"
allowed-tools: Bash(curl *), WebFetch
---

# Flux Lora

Generate images from text prompts using Black Forest Labs Flux with LoRA weights. Fine-tune output style with custom LoRA models and configurable guidance.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bfl-flux-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "a beautiful mountain landscape at sunset, photorealistic",
      "loras": [{"path": "https://example.com/landscape-lora.safetensors", "scale": 0.8}],
      "image_size": "landscape_4_3",
      "guidance_scale": 3.5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled. |
| guidance_scale | number | 3.5 | The CFG scale controls how closely the model follows the prompt. |
| image_size | string | landscape_4_3 | The size of the generated image. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9 |
| loras | array | | The LoRAs to use for image generation. Multiple LoRAs supported. |
| num_images | integer | 1 | The number of images to generate. Always 1 for streaming output. |
| num_inference_steps | integer | 28 | The number of inference steps to perform. |
| output_format | string | jpeg | The format of the generated image. enum: jpeg, png |
| prompt | string | | The prompt to generate an image from. |
| seed | integer | | The same seed and prompt produce the same output. |

## Examples

**Portrait with LoRA style:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bfl-flux-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "cinematic portrait of a woman in a garden, soft natural light",
      "loras": [{"path": "https://example.com/portrait-lora.safetensors", "scale": 0.9}],
      "image_size": "portrait_4_3",
      "guidance_scale": 4.0,
      "num_inference_steps": 30,
      "output_format": "png"
    }
  }'
```

**Multi-LoRA generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bfl-flux-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "vintage car parked on a coastal road, golden hour",
      "loras": [
        {"path": "https://example.com/vintage-lora.safetensors", "scale": 0.7},
        {"path": "https://example.com/film-lora.safetensors", "scale": 0.5}
      ],
      "image_size": "landscape_16_9",
      "seed": 42
    }
  }'
```

## Related Models

- [Black Forest Labs | Flux Dev Lora](../black-forest-labs-flux-dev-lora/) - Dev variant with LoRA
- [Flux 2 | Text to Image Lora](../flux-2-lora/) - Flux 2 with LoRA support

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
