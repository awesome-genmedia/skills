---
name: flux-kontext-dev
description: "Flux Kontext Dev. Edit images using Flux Kontext with prompt-based instructions and configurable LoRA-like controls. Triggers: flux, kontext, image edit, flux edit, image editing"
allowed-tools: Bash(curl *), WebFetch
---

# Flux Kontext Dev

Edit images using Flux Kontext with prompt-based instructions. Supports acceleration modes, configurable inference steps, guidance scale, multiple output formats, and flexible resolution modes.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-kontext-dev",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/photo.jpg",
      "prompt": "Change the person's shirt color to bright red",
      "num_images": 1,
      "output_format": "jpeg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | none | Generation speed. enum: none, regular, high |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled |
| enhance_prompt | boolean | false | Whether to enhance the prompt for better results |
| guidance_scale | number | 2.5 | CFG scale for prompt adherence |
| image_url | string | | The URL of the image to edit |
| num_images | integer | 1 | The number of images to generate |
| num_inference_steps | integer | 28 | The number of inference steps to perform |
| output_format | string | jpeg | Output format. enum: jpeg, png |
| prompt | string | | The prompt to edit the image |
| resolution_mode | string | match_input | How output resolution is set. enum: auto, match_input, 1:1, 16:9, 21:9, 3:2, 2:3, 4:5, 5:4, 3:4, 4:3, 9:16, 9:21 |
| seed | string | | Seed for reproducible results |

## Examples

**Object replacement with acceleration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-kontext-dev",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/desk-setup.jpg",
      "prompt": "Replace the laptop with a vintage typewriter",
      "acceleration": "regular",
      "num_images": 1,
      "guidance_scale": 3.0,
      "output_format": "png"
    }
  }'
```

**Style transformation with multiple outputs:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-kontext-dev",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/cityscape.jpg",
      "prompt": "Transform into a Studio Ghibli anime art style with soft pastel colors",
      "num_images": 3,
      "acceleration": "high",
      "enhance_prompt": true,
      "resolution_mode": "16:9",
      "seed": "12345"
    }
  }'
```

## Related Models

- [qwen-image-edit-plus](../qwen-image-edit-plus/) - Qwen-based image editing
- [qwen-ai-image-edit](../qwen-ai-image-edit/) - Standard Qwen image editing
- [reve-edit](../reve-edit/) - Reve image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
