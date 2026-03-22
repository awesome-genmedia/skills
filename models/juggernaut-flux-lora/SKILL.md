---
name: "Juggernaut Flux Lora"
description: "Generate images using Juggernaut Flux with optional LoRA weights. Trigger: Use when the user wants to create images with Juggernaut Flux, or requests 'juggernaut flux', 'flux lora image', or 'generate image with lora'."
allowed-tools: ["Bash"]
---

# Juggernaut Flux Lora

Generate high-quality images using the Juggernaut Flux model with optional LoRA support for style customization. Fine-tune output with guidance scale, inference steps, and custom seeds.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "juggernaut-flux-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "A hyper-realistic portrait of a woman in golden hour light, shallow depth of field",
      "image_size": "portrait_4_3",
      "num_images": 1,
      "guidance_scale": 3.5,
      "num_inference_steps": 28,
      "output_format": "jpeg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `enable_safety_checker` | boolean | `true` | If set to true, the safety checker will be enabled |
| `guidance_scale` | number | `3.5` | CFG scale controlling how closely the output matches the prompt |
| `image_size` | string | `landscape_4_3` | The size of the generated image. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9` |
| `loras` | array | `false` | The LoRAs to use for image generation. Supports multiple LoRAs with custom weights |
| `num_images` | integer | `1` | The number of images to generate |
| `num_inference_steps` | integer | `28` | The number of inference steps to perform |
| `output_format` | string | `jpeg` | The format of the generated image. Options: `jpeg`, `png` |
| `prompt` | string | (empty) | The prompt to generate an image from |
| `seed` | integer | (empty) | Random seed for reproducible generation |

## Output

- **Type:** array

## Examples

### Photorealistic Portrait
```json
{
  "model": "juggernaut-flux-lora",
  "version": "0.0.1",
  "input": {
    "prompt": "A cinematic portrait of a man in a leather jacket, moody lighting, film grain",
    "image_size": "portrait_4_3",
    "guidance_scale": 4.0,
    "num_inference_steps": 30,
    "output_format": "png",
    "seed": 55
  }
}
```

### Landscape with LoRA
```json
{
  "model": "juggernaut-flux-lora",
  "version": "0.0.1",
  "input": {
    "prompt": "A vast cyberpunk cityscape at dusk with flying vehicles and holographic signs",
    "image_size": "landscape_16_9",
    "num_images": 2,
    "guidance_scale": 3.5,
    "num_inference_steps": 28,
    "loras": [{"path": "https://example.com/cyberpunk-lora.safetensors", "scale": 0.8}]
  }
}
```

## Related Models

- [Flux Kontext Lora Text to Image](../flux-kontext-lora-text-to-image/SKILL.md) - Kontext-based image generation with LoRA
- [Flux Krea Image to Image](../flux-krea-image-to-image/SKILL.md) - Image-to-image with Flux Krea
- [Nano Banana](../nano-banana/SKILL.md) - Fast image generation

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
