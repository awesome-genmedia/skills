---
name: z-image-turbo-text-to-image
description: "Z Image | Turbo | Text to Image. Generate images from text prompts with turbo speed. Triggers: text to image, image generation, turbo, fast generation"
allowed-tools: Bash(curl *), WebFetch
---

# Z Image | Turbo | Text to Image

Generate high-quality images from text prompts using turbo-speed inference. Supports multiple image sizes, output formats, and acceleration levels.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "a majestic mountain landscape at golden hour, photorealistic",
      "image_size": "landscape_4_3",
      "num_inference_steps": 8
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | none | The acceleration level to use. enum: none, regular, high |
| enable_prompt_expansion | boolean | false | Whether to enable prompt expansion. Increases price by 0.0025. |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled. |
| image_size | string | landscape_4_3 | The size of the generated image. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9 |
| num_images | integer | 1 | The number of images to generate. |
| num_inference_steps | integer | 8 | The number of inference steps to perform. |
| output_format | string | png | The format of the generated image. enum: jpeg, png, webp |
| prompt | string | | The prompt to generate an image from. |
| seed | integer | | The same seed and prompt produce the same output. |

## Examples

**Generate a portrait with acceleration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "professional headshot of a business executive, studio lighting, sharp focus",
      "image_size": "portrait_4_3",
      "acceleration": "high",
      "output_format": "jpeg"
    }
  }'
```

**Generate multiple images with a seed:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "a cozy coffee shop interior, warm lighting, watercolor style",
      "image_size": "square_hd",
      "num_images": 3,
      "seed": 42,
      "enable_prompt_expansion": true
    }
  }'
```

## Related Models

- [Z Image | Turbo | Image to Image](../z-image-turbo-image-to-image/) - Transform existing images
- [Z Image | Turbo | Controlnet](../z-image-turbo-controlnet/) - ControlNet-guided generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
