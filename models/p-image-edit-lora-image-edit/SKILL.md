---
name: p-image-edit-lora-image-edit
description: "Pruna | P-Image Edit LoRA | Image Editing. Edit images using custom LoRA weights with prompt-based instructions. Triggers: image edit, lora, pruna, edit image, image editing"
allowed-tools: Bash(curl *), WebFetch
---

# Pruna | P-Image Edit LoRA | Image Editing

Edit images using custom LoRA weights trained with p-image-edit-trainer. Supports multi-image editing with prompt-based instructions and configurable LoRA strength.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "p-image-edit-lora-image-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Make image 1 look like a watercolor painting",
      "images": ["https://example.com/photo.jpg"],
      "lora_weights": "https://huggingface.co/my-org/my-edit-lora",
      "lora_scale": 1,
      "aspect_ratio": "match_input_image"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | match_input_image | Output aspect ratio. enum: match_input_image, 1:1, 16:9, 9:16, 4:3, 3:4, 3:2, 2:3 |
| disable_safety_checker | boolean | false | Disable safety checker for generated images. |
| hf_api_token | string | false | HuggingFace API token for accessing private LoRA repositories. |
| images | array | false | Array of 1-5 image URLs for editing. |
| lora_scale | number | 1 | LoRA strength (-1 to 3). Default 1 for edit LoRAs. |
| lora_weights | string | false | HuggingFace URL to LoRA weights. Must be trained with p-image-edit-trainer. |
| prompt | string | false | Text prompt describing the edit. Refer to images as image 1, image 2, etc. |
| seed | integer | false | Random seed for reproducible generation. |
| turbo | boolean | true | Faster optimizations. Set false for complex tasks. |

## Examples

**Basic image edit with LoRA:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "p-image-edit-lora-image-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Apply a vintage film look to image 1",
      "images": ["https://example.com/landscape.jpg"],
      "lora_weights": "https://huggingface.co/my-org/vintage-lora",
      "lora_scale": 0.8
    }
  }'
```

**Multi-image edit with custom aspect ratio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "p-image-edit-lora-image-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Combine the style of image 1 with the subject of image 2",
      "images": ["https://example.com/style.jpg", "https://example.com/subject.jpg"],
      "lora_weights": "https://huggingface.co/my-org/style-transfer-lora",
      "lora_scale": 1.2,
      "aspect_ratio": "16:9",
      "turbo": false,
      "seed": 42
    }
  }'
```

**High LoRA strength edit:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "p-image-edit-lora-image-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Transform image 1 into a cartoon character",
      "images": ["https://example.com/portrait.jpg"],
      "lora_weights": "https://huggingface.co/my-org/cartoon-lora",
      "lora_scale": 2.5,
      "disable_safety_checker": false
    }
  }'
```

## Related Models

- [p-image-lora-text-to-image](../p-image-lora-text-to-image/) - Text to image generation with LoRA weights
- [p-image-edit](../p-image-edit/) - Image editing without LoRA
- [p-image-text-to-image](../p-image-text-to-image/) - Standard text to image generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
