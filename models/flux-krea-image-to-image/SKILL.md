---
name: "Flux Krea Image to Image"
description: "Transform images using Flux Krea with text guidance. Trigger: Use when the user wants to transform an image into a new style, or requests 'flux krea image to image', 'transform image', or 'restyle image with flux'."
allowed-tools: ["Bash"]
---

# Flux Krea | Image to Image

Transform an existing image guided by a text prompt. Control the transformation intensity with the strength parameter and speed with the acceleration setting.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-krea-image-to-image",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/photo.jpg",
      "prompt": "Transform into a detailed oil painting with rich textures",
      "strength": 0.85,
      "guidance_scale": 4.5,
      "num_inference_steps": 40
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `acceleration` | string | `none` | Generation speed. Options: `none`, `regular`, `high` |
| `enable_safety_checker` | boolean | `true` | If set to true, the safety checker will be enabled |
| `guidance_scale` | number | `4.5` | CFG scale controlling how closely the output matches the prompt |
| `image_url` | string | (empty) | The URL of the image to generate an image from |
| `num_images` | integer | `1` | The number of images to generate |
| `num_inference_steps` | integer | `40` | The number of inference steps to perform |
| `output_format` | string | `jpeg` | Output format. Options: `jpeg`, `png` |
| `prompt` | string | (empty) | The prompt to generate an image from |
| `seed` | string | (empty) | Random seed for reproducible generation |
| `strength` | number | `0.95` | Strength of the initial image influence. Higher values keep more of the prompt |

## Output

- **Type:** image

## Examples

### Artistic Style Transfer
```json
{
  "model": "flux-krea-image-to-image",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/cityscape.jpg",
    "prompt": "A vibrant impressionist painting of a city at dusk",
    "strength": 0.8,
    "guidance_scale": 5.0,
    "num_inference_steps": 40,
    "output_format": "png"
  }
}
```

### Fast Image Enhancement
```json
{
  "model": "flux-krea-image-to-image",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/portrait.jpg",
    "prompt": "Enhanced professional headshot with studio lighting and bokeh background",
    "strength": 0.6,
    "guidance_scale": 4.0,
    "num_inference_steps": 30,
    "acceleration": "high"
  }
}
```

## Related Models

- [Flux Krea Lora Image to Image](../flux-krea-lora-image-to-image/SKILL.md) - Image to image with LoRA support
- [Seedream V4 Edit](../seedream-v4-edit/SKILL.md) - Text-driven image editing
- [Juggernaut Flux Lora](../juggernaut-flux-lora/SKILL.md) - Text-to-image with LoRA

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
