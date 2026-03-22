---
name: hunyuan-image-v3-text-to-image
description: "Hunyuan Image v3 | Text to Image. Generate images from text prompts using Tencent Hunyuan Image v3. Triggers: hunyuan, text to image, image generation, tencent hunyuan"
allowed-tools: Bash(curl *), WebFetch
---

# Hunyuan Image v3 | Text to Image

Generate high-quality images from text descriptions using Tencent Hunyuan Image v3. Supports configurable guidance scale, inference steps, negative prompts, and multiple output sizes and formats.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "hunyuan-image-v3-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A serene Japanese zen garden with raked sand patterns, moss-covered rocks, and a small maple tree with red leaves",
      "image_size": "landscape_16_9",
      "num_images": 1,
      "output_format": "png"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled |
| guidance_scale | number | 3.5 | Controls how much the model adheres to the prompt |
| image_size | string | square_hd | The desired size. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9 |
| negative_prompt | string | | Negative prompt to guide away from certain concepts |
| num_images | integer | 1 | The number of images to generate |
| num_inference_steps | integer | 28 | Number of denoising steps |
| output_format | string | png | The format of the generated image. enum: jpeg, png |
| prompt | string | | The text prompt for image generation |
| seed | integer | | Random seed for reproducible results |

## Examples

**Detailed art with high guidance:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "hunyuan-image-v3-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Photorealistic portrait of a cyberpunk samurai in neon-lit rain, detailed armor with LED accents",
      "negative_prompt": "blurry, low quality, deformed, ugly",
      "image_size": "portrait_16_9",
      "guidance_scale": 5.0,
      "num_inference_steps": 40,
      "num_images": 1,
      "output_format": "png"
    }
  }'
```

**Multiple variations with seed:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "hunyuan-image-v3-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Minimalist flat illustration of a mountain landscape with geometric shapes and soft gradient sky",
      "image_size": "landscape_4_3",
      "num_images": 4,
      "guidance_scale": 3.5,
      "output_format": "jpeg",
      "seed": 42
    }
  }'
```

## Related Models

- [reve-text-to-image](../reve-text-to-image/) - Reve text to image
- [wan-2-5-preview-text-to-image](../wan-2-5-preview-text-to-image/) - Wan text to image
- [tencent-flux-srpo-text-to-image](../tencent-flux-srpo-text-to-image/) - Tencent Flux SRPO text to image

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
