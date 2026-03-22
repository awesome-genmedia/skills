---
name: ovis-image
description: "Ovis Image. Generate images from text with guidance scale and negative prompts. Triggers: text to image, ovis, image generation, guided generation"
allowed-tools: Bash(curl *), WebFetch
---

# Ovis Image

Generate images from text prompts with fine-tuned control over guidance scale, negative prompts, and inference steps. Supports acceleration for faster generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ovis-image",
    "version": "0.0.1",
    "input": {
      "prompt": "a vibrant underwater coral reef, tropical fish, sunlight rays",
      "image_size": "landscape_4_3",
      "guidance_scale": 5,
      "num_inference_steps": 28
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | regular | The acceleration level to use. enum: none, regular, high |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled. |
| guidance_scale | number | 5 | The guidance scale to use for the image generation. |
| image_size | string | landscape_4_3 | The size of the generated image. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9 |
| negative_prompt | string | | The negative prompt to avoid unwanted elements. |
| num_images | integer | 1 | The number of images to generate. |
| num_inference_steps | integer | 28 | The number of inference steps to perform. |
| output_format | string | png | The format of the generated image. enum: jpeg, png, webp |
| prompt | string | | The prompt to generate an image from. |
| seed | integer | | The same seed and prompt produce the same output. |

## Examples

**Detailed portrait with negative prompt:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ovis-image",
    "version": "0.0.1",
    "input": {
      "prompt": "oil painting of a woman in a garden, impressionist style, soft light",
      "negative_prompt": "blurry, deformed, low quality, watermark",
      "image_size": "portrait_4_3",
      "guidance_scale": 7,
      "num_inference_steps": 35,
      "output_format": "png"
    }
  }'
```

**Fast generation with high acceleration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ovis-image",
    "version": "0.0.1",
    "input": {
      "prompt": "futuristic robot in a neon-lit alley, cinematic",
      "acceleration": "high",
      "image_size": "square_hd",
      "num_images": 3,
      "seed": 42
    }
  }'
```

## Related Models

- [Flux 2](../flux-2/) - Alternative text-to-image generation
- [Bytedance | Seedream | v4.5 | Text to Image](../bytedance-seedream-v4-5-text-to-image/) - Bytedance image generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
