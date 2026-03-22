---
name: "Flux Krea Lora Image to Image"
description: "Transform images using Flux Krea with LoRA support. Trigger: Use when the user wants to apply LoRA-based style to an image, or requests 'flux krea lora', 'image to image with lora', or 'restyle image with custom lora'."
allowed-tools: ["Bash"]
---

# Flux Krea | Lora | Image to Image

Transform images using Flux Krea with custom LoRA weights for precise style control. Supports inpainting and image-to-image workflows.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-krea-lora-image-to-image",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/photo.jpg",
      "prompt": "A portrait in watercolor style with soft pastel colors",
      "guidance_scale": 3.5,
      "num_inference_steps": 28,
      "strength": 0.85
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `enable_safety_checker` | boolean | `true` | If set to true, the safety checker will be enabled |
| `guidance_scale` | number | `3.5` | CFG scale controlling prompt adherence |
| `image_size` | string | `square` | Size of the generated image. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9` |
| `image_url` | string | (empty) | URL of image to use for inpainting or img2img |
| `loras` | array | `false` | The LoRAs to use for image generation with custom weights |
| `num_images` | integer | `1` | The number of images to generate |
| `num_inference_steps` | integer | `28` | The number of inference steps to perform |
| `output_format` | string | `jpeg` | Output format. Options: `jpeg`, `png` |
| `prompt` | string | (empty) | The prompt to generate an image from |
| `seed` | integer | (empty) | Random seed for reproducible generation |
| `strength` | number | `0.85` | Strength for inpainting/image-to-image. Only used with image_url |

## Output

- **Type:** image

## Examples

### LoRA Style Transfer
```json
{
  "model": "flux-krea-lora-image-to-image",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/landscape.jpg",
    "prompt": "A scenic view in anime art style",
    "loras": [{"path": "https://example.com/anime-style-lora.safetensors", "scale": 0.9}],
    "strength": 0.8,
    "guidance_scale": 4.0,
    "num_inference_steps": 30,
    "output_format": "png"
  }
}
```

### Subtle Enhancement
```json
{
  "model": "flux-krea-lora-image-to-image",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/headshot.jpg",
    "prompt": "Professional studio portrait with perfect lighting",
    "strength": 0.5,
    "guidance_scale": 3.0,
    "image_size": "portrait_4_3",
    "seed": 88
  }
}
```

## Related Models

- [Flux Krea Image to Image](../flux-krea-image-to-image/SKILL.md) - Image to image without LoRA
- [Juggernaut Flux Lora](../juggernaut-flux-lora/SKILL.md) - Text-to-image with LoRA
- [Flux Kontext Lora Text to Image](../flux-kontext-lora-text-to-image/SKILL.md) - Text-to-image with Kontext LoRA

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
