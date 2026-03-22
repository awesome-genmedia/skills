---
name: qwen-image
description: "Qwen Image. Generate images from text prompts using the Qwen image generation model. Triggers: qwen image, generate image, text to image, ai image generation, qwen, create image from text"
allowed-tools: Bash(curl *), WebFetch
---

# Qwen Image

Generate images from text prompts using the Qwen image generation model. Supports multiple aspect ratios, output formats, and fine-tuned control over guidance and inference steps for high-quality results.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "qwen-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A serene Japanese garden with a koi pond, cherry blossoms in full bloom, soft morning light",
      "aspect_ratio": "16:9",
      "num_inference_steps": 50,
      "guidance": 4
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Image aspect ratio. Options: `1:1`, `16:9`, `9:16`, `4:3`, `3:4` |
| disable_safety_checker | boolean | false | Disable safety checker for generated images |
| go_fast | boolean | true | Run faster predictions with additional optimizations |
| guidance | number | 4 | Guidance scale. Lower values can give more realistic images |
| num_inference_steps | integer | 50 | Number of denoising steps. Recommended range is 28-50 |
| output_format | string | webp | Output format. Options: `webp`, `jpg`, `png` |
| output_quality | integer | 80 | Quality when saving output images, from 0 to 100 |
| prompt | string | - | Prompt for generated image |
| seed | integer | - | Random seed for reproducible generation |

## Examples

**Photorealistic landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "qwen-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A dramatic mountain landscape at golden hour, snow-capped peaks reflecting in a crystal clear alpine lake, photorealistic",
      "aspect_ratio": "16:9",
      "guidance": 3.5,
      "num_inference_steps": 50,
      "output_format": "png",
      "output_quality": 100
    }
  }'
```

**Portrait illustration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "qwen-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A fantasy warrior princess with braided silver hair, wearing ornate golden armor, digital art, highly detailed",
      "aspect_ratio": "3:4",
      "guidance": 5,
      "seed": 42
    }
  }'
```

## Related Models

- [Imagen 4 | Fast](../imagen-4-fast/) - Google's fast image generation
- [Seedream V3 | Text to Image](../seedream-v3-text-to-image/) - ByteDance text-to-image
- [Ideogram V3 | Turbo](../ideogram-v3-turbo/) - Ideogram image generation with text rendering

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
