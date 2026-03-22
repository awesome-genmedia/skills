---
name: z-image-turbo-controlnet-lora
description: "Z Image | Turbo | Controlnet | Lora. Generate images with ControlNet guidance and LoRA weights. Triggers: controlnet, lora, guided generation, z image, pose to image, depth"
allowed-tools: Bash(curl *), WebFetch
---

# Z Image | Turbo | Controlnet | Lora

Generate images with ControlNet-guided generation and LoRA weight support. Use canny edges, depth maps, or pose detection from reference images combined with custom LoRA models for precise control over composition and style.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-controlnet-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "A futuristic robot in the same pose, metallic chrome finish",
      "image_url": "https://example.com/person-pose.jpg",
      "preprocess": "pose",
      "loras": [{"path": "https://example.com/scifi-lora.safetensors", "scale": 0.8}],
      "control_scale": 0.9,
      "image_size": "auto",
      "output_format": "png"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | none | The acceleration level to use. Options: `none`, `regular`, `high` |
| control_end | number | 0.4 | The end of the controlnet conditioning. |
| control_scale | number | 0.9 | The scale of the controlnet conditioning. |
| control_start | number | 0 | The start of the controlnet conditioning. |
| enable_prompt_expansion | boolean | false | Whether to enable prompt expansion. |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled. |
| image_size | string | auto | The size of the generated image. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9`, `auto` |
| image_url | string | - | URL of Image for ControlNet generation. |
| loras | array | - | List of LoRA weights to apply. |
| num_images | integer | 1 | The number of images to generate. |
| num_inference_steps | integer | 8 | The number of inference steps to perform. |
| output_format | string | png | The format of the generated image. Options: `jpeg`, `png`, `webp` |
| preprocess | string | none | Preprocessing to apply to the image. Options: `none`, `canny`, `depth`, `pose` |
| prompt | string | - | The prompt to generate an image from. |
| seed | integer | - | Seed for reproducible generation. |

## Examples

**Canny edge-guided generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-controlnet-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "Elegant architectural rendering, glass and steel",
      "image_url": "https://example.com/building-sketch.jpg",
      "preprocess": "canny",
      "loras": [{"path": "https://example.com/architecture-lora.safetensors", "scale": 0.7}]
    }
  }'
```

**Depth-guided with fine-tuned control:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-controlnet-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "An enchanted forest scene with magical creatures",
      "image_url": "https://example.com/forest-photo.jpg",
      "preprocess": "depth",
      "loras": [{"path": "https://example.com/fantasy-lora.safetensors", "scale": 0.9}],
      "control_scale": 0.7,
      "control_start": 0,
      "control_end": 0.6,
      "acceleration": "regular",
      "num_images": 2,
      "seed": 42
    }
  }'
```

## Related Models

- [Z Image | Turbo | Lora](../z-image-turbo-lora/) - Text-to-image with LoRA
- [Z Image | Turbo | Image to Image | Lora](../z-image-turbo-image-to-image-lora/) - Image-to-image with LoRA
- [Z Image | Turbo | Controlnet](../z-image-turbo-controlnet/) - ControlNet without LoRA

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
