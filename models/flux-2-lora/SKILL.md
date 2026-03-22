---
name: flux-2-lora
description: "Flux 2 | Text to Image Lora. Generate images using LoRA weights for specialized styles. Triggers: text to image, flux, lora, fine-tuned, style generation"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2 | Text to Image Lora

Generate images from text prompts with up to 3 LoRA weights for specialized style control. Supports URL, HuggingFace, and other LoRA sources.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "a mystical forest with glowing mushrooms, fantasy art",
      "loras": [{"path": "https://example.com/fantasy-lora.safetensors", "scale": 0.8}],
      "image_size": "square_hd",
      "guidance_scale": 2.5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | none | The acceleration level to use. enum: none, regular, high |
| enable_prompt_expansion | boolean | false | If set to true, the prompt will be expanded for better results. |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled. |
| guidance_scale | number | 2.5 | Guidance Scale controls how closely the model follows your prompt. |
| image_size | string | square_hd | The size of the generated image. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9 |
| loras | array | | List of LoRA weights to apply (maximum 3). URL, HuggingFace repo, or other sources. |
| num_images | integer | 1 | The number of images to generate. |
| num_inference_steps | integer | 28 | The number of inference steps to perform. |
| output_format | string | png | The format of the generated image. enum: jpeg, png, webp |
| prompt | string | | The prompt to generate an image from. |
| seed | integer | | The seed to use for the generation. |

## Examples

**Single LoRA generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "professional headshot, studio lighting, clean background",
      "loras": [{"path": "https://example.com/portrait-lora.safetensors", "scale": 0.9}],
      "image_size": "portrait_4_3",
      "output_format": "jpeg",
      "num_inference_steps": 30
    }
  }'
```

**Multi-LoRA with acceleration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "vintage car on a coastal highway, golden hour",
      "loras": [
        {"path": "https://example.com/vintage-lora.safetensors", "scale": 0.7},
        {"path": "https://example.com/automotive-lora.safetensors", "scale": 0.6}
      ],
      "acceleration": "high",
      "image_size": "landscape_16_9",
      "num_images": 3,
      "seed": 42
    }
  }'
```

## Related Models

- [Flux 2 | Lora Edit](../flux-2-lora-edit/) - LoRA-based image editing
- [Flux 2](../flux-2/) - Standard text-to-image generation
- [BFL Flux Lora](../bfl-flux-lora/) - Alternative Flux LoRA model

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
