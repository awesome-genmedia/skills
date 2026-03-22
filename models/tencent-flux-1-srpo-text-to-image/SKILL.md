---
name: tencent-flux-1-srpo-text-to-image
description: "Tencent | Flux 1 | Srpo | Text to Image. Generate images from text prompts using Tencent Flux 1 SRPO with default acceleration. Triggers: tencent, flux 1, srpo, text to image, image generation"
allowed-tools: Bash(curl *), WebFetch
---

# Tencent | Flux 1 | Srpo | Text to Image

Generate high-quality images from text descriptions using the Tencent Flux 1 SRPO model. Comes with regular acceleration by default for faster generation, configurable guidance scale, multiple image sizes, and adjustable inference steps.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "tencent-flux-1-srpo-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A cozy cabin in the woods during winter, snow falling, warm light from the windows, photorealistic",
      "image_size": "landscape_4_3",
      "num_images": 1,
      "output_format": "jpeg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | regular | Generation speed. enum: none, regular, high |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled |
| guidance_scale | number | 4.5 | CFG scale for prompt adherence |
| image_size | string | landscape_4_3 | The size of the generated image. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9 |
| num_images | integer | 1 | The number of images to generate |
| num_inference_steps | integer | 28 | The number of inference steps to perform |
| output_format | string | jpeg | The format of the generated image. enum: jpeg, png |
| prompt | string | | The prompt to generate an image from |
| seed | string | | Seed for reproducible results |

## Examples

**Detailed art generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "tencent-flux-1-srpo-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A steampunk clockwork dragon made of brass gears and copper pipes, breathing golden flame, highly detailed concept art",
      "image_size": "square_hd",
      "guidance_scale": 5.0,
      "num_inference_steps": 35,
      "output_format": "png"
    }
  }'
```

**Fast batch generation with high acceleration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "tencent-flux-1-srpo-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Product photography of a luxury perfume bottle on a marble surface with rose petals",
      "image_size": "portrait_16_9",
      "acceleration": "high",
      "num_images": 4,
      "output_format": "jpeg",
      "seed": "7890"
    }
  }'
```

## Related Models

- [tencent-flux-srpo-text-to-image](../tencent-flux-srpo-text-to-image/) - Tencent Flux SRPO text to image
- [tencent-flux-srpo-image-to-image](../tencent-flux-srpo-image-to-image/) - Image to image transformation
- [hunyuan-image-v3-text-to-image](../hunyuan-image-v3-text-to-image/) - Hunyuan text to image

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
