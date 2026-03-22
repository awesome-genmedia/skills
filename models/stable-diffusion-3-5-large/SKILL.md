---
name: stable-diffusion-3-5-large
description: "Stable Diffusion 3.5 Large | AI Image Generation. Generate high-quality images from text with the large SD 3.5 model. Triggers: stable diffusion 3.5 large, sd 3.5, text to image, image generation, sd3 large"
allowed-tools: Bash(curl *), WebFetch
---

# Stable Diffusion 3.5 Large

Generate high-quality images from text prompts using the Stable Diffusion 3.5 Large model. Supports text-to-image and image-to-image modes with configurable guidance, steps, and output settings.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "stable-diffusion-3-5-large",
    "version": "0.0.1",
    "input": {
      "prompt": "a photorealistic underwater scene with colorful coral reef and tropical fish, sunlight filtering through water",
      "aspect_ratio": "16:9",
      "cfg": 3.5,
      "steps": 35,
      "output_format": "webp"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | Output aspect ratio. enum: 1:1, 16:9, 21:9, 3:2, 2:3, 4:5, 5:4, 3:4, 4:3, 9:16, 9:21 |
| cfg | number | 3.5 | Guidance scale - how similar the output should be to the prompt |
| image | string | - | Input image for image-to-image mode |
| output_format | string | webp | Output format. enum: webp, jpg, png |
| output_quality | integer | 90 | Quality of output images, from 0 to 100 |
| prompt | string | - | Text prompt for image generation |
| prompt_strength | number | 0.85 | Prompt strength when using image-to-image. 1.0 is full destruction of input |
| seed | integer | - | Set a seed for reproducibility. Random by default |
| steps | integer | 35 | Number of steps to run the sampler for |

## Examples

**Cinematic landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "stable-diffusion-3-5-large",
    "version": "0.0.1",
    "input": {
      "prompt": "epic mountain landscape at sunset with dramatic clouds, golden light, cinematic composition, 8k resolution",
      "aspect_ratio": "21:9",
      "cfg": 4,
      "steps": 40,
      "output_format": "png",
      "output_quality": 100
    }
  }'
```

**Image-to-image style transfer:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "stable-diffusion-3-5-large",
    "version": "0.0.1",
    "input": {
      "prompt": "anime style illustration, vibrant colors, Studio Ghibli inspired",
      "image": "https://example.com/landscape-photo.jpg",
      "prompt_strength": 0.75,
      "cfg": 4,
      "steps": 35,
      "seed": 42
    }
  }'
```

## Related Models

- [stable-diffusion-3-5-medium](../stable-diffusion-3-5-medium/) - Lighter SD 3.5 model for faster generation
- [flux-dev](../flux-dev/) - Flux Dev image generation
- [flux-1-1-pro-ultra](../flux-1-1-pro-ultra/) - Ultra quality Flux generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
