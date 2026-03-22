---
name: kling-o1
description: "Kling O1. Generate images with reference image support and up to 2K resolution. Triggers: image generation, kling, o1, text to image, reference image"
allowed-tools: Bash(curl *), WebFetch
---

# Kling O1

Generate high-quality images with optional reference image support. Reference images in prompts using @Image1, @Image2, etc. Supports up to 2K resolution and multiple aspect ratios.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o1",
    "version": "0.0.1",
    "input": {
      "prompt": "a beautiful sunset over the ocean, photorealistic, vibrant colors",
      "aspect_ratio": "16:9",
      "resolution": "1K",
      "num_images": 1
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | auto | Aspect ratio of generated images. 'auto' determines based on input. enum: auto, 16:9, 9:16, 1:1, 4:3, 3:4, 3:2, 2:3, 21:9 |
| image_urls | array | | List of reference images. Reference in prompt using @Image1, @Image2, etc. |
| num_images | integer | 1 | Number of images to generate (1-9). |
| output_format | string | png | The format of the generated image. enum: jpeg, png, webp |
| prompt | string | | Text prompt for image generation. Reference images using @Image1, @Image2, etc. |
| resolution | string | 1K | Image generation resolution. enum: 1K, 2K |

## Examples

**High-res landscape with reference:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o1",
    "version": "0.0.1",
    "input": {
      "prompt": "redesign @Image1 as a futuristic cityscape, neon lights, cyberpunk style",
      "image_urls": ["https://example.com/city-reference.jpg"],
      "aspect_ratio": "21:9",
      "resolution": "2K",
      "output_format": "png"
    }
  }'
```

**Multiple image generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o1",
    "version": "0.0.1",
    "input": {
      "prompt": "a minimalist product shot of a perfume bottle, studio lighting, marble background",
      "aspect_ratio": "1:1",
      "resolution": "2K",
      "num_images": 4,
      "output_format": "jpeg"
    }
  }'
```

## Related Models

- [Kling O1 | Image to Video](../kling-o1-image-to-video/) - Animate images into video
- [Kling O1 | Reference Image to Video](../kling-o1-reference-image-to-video/) - Reference-guided video generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
