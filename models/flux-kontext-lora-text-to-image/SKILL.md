---
name: "Flux Kontext Lora Text to Image"
description: "Generate images from text using Flux Kontext with LoRA support. Trigger: Use when the user wants to create images using Flux Kontext, or requests 'flux kontext', 'kontext text to image', or 'generate image with kontext lora'."
allowed-tools: ["Bash"]
---

# Flux Kontext Lora | Text to Image

Generate images from text prompts using Flux Kontext with optional LoRA weights. Features adjustable generation speed via acceleration modes.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-kontext-lora-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A mystical forest clearing with bioluminescent mushrooms and fireflies",
      "image_size": "landscape_4_3",
      "num_images": 1,
      "guidance_scale": 2.5,
      "num_inference_steps": 30,
      "output_format": "png"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `acceleration` | string | `none` | Generation speed. Options: `none`, `regular`, `high` |
| `enable_safety_checker` | boolean | `true` | If set to true, the safety checker will be enabled |
| `guidance_scale` | number | `2.5` | CFG scale controlling prompt adherence |
| `image_size` | string | `landscape_4_3` | Size of the generated image. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9` |
| `loras` | array | `false` | The LoRAs to use for image generation with custom weights |
| `num_images` | integer | `1` | The number of images to generate |
| `num_inference_steps` | integer | `30` | The number of inference steps to perform |
| `output_format` | string | `png` | Output format. Options: `jpeg`, `png` |
| `prompt` | string | (empty) | The prompt to generate the image with |
| `seed` | integer | (empty) | Random seed for reproducible generation |

## Output

- **Type:** image

## Examples

### Fantasy Art with LoRA
```json
{
  "model": "flux-kontext-lora-text-to-image",
  "version": "0.0.1",
  "input": {
    "prompt": "An epic dragon perched on a crumbling castle tower at sunset",
    "image_size": "landscape_16_9",
    "loras": [{"path": "https://example.com/fantasy-lora.safetensors", "scale": 0.85}],
    "guidance_scale": 3.0,
    "num_inference_steps": 30,
    "output_format": "png"
  }
}
```

### Fast Product Mockup
```json
{
  "model": "flux-kontext-lora-text-to-image",
  "version": "0.0.1",
  "input": {
    "prompt": "A sleek smartphone mockup on a marble desk with plants in soft studio lighting",
    "image_size": "square_hd",
    "acceleration": "high",
    "guidance_scale": 2.5,
    "num_inference_steps": 20,
    "seed": 77
  }
}
```

## Related Models

- [Juggernaut Flux Lora](../juggernaut-flux-lora/SKILL.md) - Flux-based image generation with LoRA
- [Flux Krea Lora Image to Image](../flux-krea-lora-image-to-image/SKILL.md) - Image-to-image with LoRA
- [Seedream V4 Text to Image](../seedream-v4-text-to-image/SKILL.md) - Text-to-image generation

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
