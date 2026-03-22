---
name: flux-2-lora-edit
description: "Flux 2 | Lora Edit. Edit images using LoRA weights for specialized styles. Triggers: image editing, flux, lora, style transfer, fine-tuned editing"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2 | Lora Edit

Edit images using up to 3 LoRA weights for specialized style control. Combines Flux 2's editing capabilities with LoRA-based fine-tuning for targeted modifications.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-lora-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "transform into a vintage film photograph style",
      "image_urls": ["https://example.com/photo.jpg"],
      "loras": [{"path": "https://example.com/vintage-lora.safetensors", "scale": 0.8}],
      "guidance_scale": 2.5,
      "image_size": "square_hd"
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
| image_urls | array | | The URLs of the images for editing. |
| loras | array | | List of LoRA weights to apply (maximum 3). |
| num_images | integer | 1 | The number of images to generate. |
| num_inference_steps | integer | 28 | The number of inference steps to perform. |
| output_format | string | png | The format of the generated image. enum: jpeg, png, webp |
| prompt | string | | The prompt to generate an image from. |
| seed | integer | | The seed to use for the generation. |

## Examples

**LoRA-guided style edit:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-lora-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "apply anime illustration style to the portrait",
      "image_urls": ["https://example.com/portrait.jpg"],
      "loras": [{"path": "https://example.com/anime-lora.safetensors", "scale": 0.9}],
      "guidance_scale": 3.0,
      "num_inference_steps": 30,
      "output_format": "png"
    }
  }'
```

**Multi-LoRA editing with acceleration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-lora-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "enhance with cinematic lighting and film grain",
      "image_urls": ["https://example.com/scene.jpg"],
      "loras": [
        {"path": "https://example.com/cinematic-lora.safetensors", "scale": 0.7},
        {"path": "https://example.com/film-grain-lora.safetensors", "scale": 0.5}
      ],
      "acceleration": "high",
      "num_images": 2,
      "seed": 42
    }
  }'
```

## Related Models

- [Flux 2 | Text to Image Lora](../flux-2-lora/) - LoRA-based text-to-image generation
- [Flux 2 | Edit](../flux-2-edit/) - Standard image editing without LoRA

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
