---
name: stable-diffusion-3-5-medium
description: "Stable Diffusion 3.5 Medium | AI Image Generation. Generate images from text with optional img2img mode. Triggers: stable diffusion 3.5, sd 3.5 medium, text to image, image generation, sd3"
allowed-tools: Bash(curl *), WebFetch
---

# Stable Diffusion 3.5 Medium

Generate images from text prompts using Stable Diffusion 3.5 Medium. Supports text-to-image and image-to-image modes with configurable aspect ratio, guidance, and quality settings.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "stable-diffusion-3-5-medium",
    "version": "0.0.1",
    "input": {
      "prompt": "a majestic eagle soaring over snow-capped mountains, photorealistic, golden hour lighting",
      "aspect_ratio": "16:9",
      "cfg": 5,
      "steps": 40,
      "output_format": "webp"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | Output aspect ratio. enum: 1:1, 16:9, 21:9, 3:2, 2:3, 4:5, 5:4, 3:4, 4:3, 9:16, 9:21 |
| cfg | number | 5 | Guidance scale - how similar the output should be to the prompt |
| image | string | - | Input image for image-to-image mode |
| output_format | string | webp | Output format. enum: webp, jpg, png |
| output_quality | integer | 90 | Quality of output images, from 0 to 100 |
| prompt | string | - | Text prompt for image generation |
| prompt_strength | number | 0.85 | Prompt strength when using image-to-image. 1.0 is full destruction of input |
| seed | integer | - | Set a seed for reproducibility. Random by default |
| steps | integer | 40 | Number of steps to run the sampler for |

## Examples

**Detailed character art:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "stable-diffusion-3-5-medium",
    "version": "0.0.1",
    "input": {
      "prompt": "a steampunk inventor in their workshop, intricate gears and brass instruments, warm candlelight, detailed illustration",
      "aspect_ratio": "4:5",
      "cfg": 6,
      "steps": 45,
      "output_format": "png",
      "output_quality": 100
    }
  }'
```

**Image-to-image transformation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "stable-diffusion-3-5-medium",
    "version": "0.0.1",
    "input": {
      "prompt": "a watercolor painting of a peaceful countryside village",
      "image": "https://example.com/village-photo.jpg",
      "prompt_strength": 0.7,
      "cfg": 5,
      "steps": 35,
      "seed": 42
    }
  }'
```

## Related Models

- [stable-diffusion-3-5-large](../stable-diffusion-3-5-large/) - Larger SD 3.5 model for higher quality
- [flux-dev](../flux-dev/) - Flux Dev image generation
- [sana](../sana/) - Nvidia Sana image generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
