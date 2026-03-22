---
name: flux-kontext-dev-lora
description: "Flux.1 Kontext Dev Lora. Generate and edit images using Flux Kontext Dev with custom LoRA weights. Fine-tuned image generation with custom styles. Triggers: flux kontext lora, flux dev lora, kontext lora, custom style image, lora image generation, flux lora"
allowed-tools: Bash(curl *), WebFetch
---

# Flux.1 Kontext Dev Lora

Generate and edit images using Flux Kontext Dev with custom LoRA (Low-Rank Adaptation) weights. Apply custom fine-tuned styles by providing a LoRA weights URL along with a prompt and optional reference image.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-kontext-dev-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "A futuristic city skyline at sunset in the style of TOK",
      "lora_path": "https://example.com/my-custom-lora.safetensors",
      "lora_weight": 1
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| enable_safety_checker | boolean | false | Enable content safety checking |
| image_url | string | - | URL of an input image for image-to-image editing |
| lora_path | string | - | URL or path to the LoRA weights file |
| lora_weight | number | 1 | Strength of the LoRA effect (0 to 1+) |
| prompt | string | - | Text prompt for generation |
| seed | integer | - | Random seed for reproducible results |

## Examples

**Generate with custom LoRA style:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-kontext-dev-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "A majestic lion portrait in the style of TOK, highly detailed",
      "lora_path": "https://huggingface.co/user/model/resolve/main/lora.safetensors",
      "lora_weight": 0.8,
      "seed": 42
    }
  }'
```

**Edit an image with LoRA style:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-kontext-dev-lora",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/photo.jpg",
      "prompt": "Transform this photo into the style of TOK, vibrant colors",
      "lora_path": "https://example.com/art-style-lora.safetensors",
      "lora_weight": 1.2
    }
  }'
```

## Related Models

- [Flux.1 Kontext | Pro](../flux-kontext-pro/) - Flux Kontext Pro without LoRA
- [Flux.1 Kontext | Max](../flux-kontext-max/) - Highest quality Flux Kontext
- [Flux Multi Image Kontext](../multi-image-kontext/) - Multi-image Flux Kontext

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
