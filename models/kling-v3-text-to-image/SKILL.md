---
name: kling-v3-text-to-image
description: "Kling | v3 | Text to Image. Generate images from text with face control elements, negative prompts, and up to 2K resolution. Triggers: text to image, kling, v3, generate image, t2i"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | v3 | Text to Image

Generate images from text descriptions using Kling v3 with support for face control elements, negative prompts, up to 9 images per request, and 2K resolution.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A futuristic robot standing in a neon-lit alley, photorealistic, cinematic lighting",
      "aspect_ratio": "16:9",
      "resolution": "2K",
      "num_images": 1
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio of generated images. enum: 16:9, 9:16, 1:1, 4:3, 3:4, 3:2, 2:3, 21:9 |
| elements | array | false | Optional elements (characters/objects) for face control. |
| negative_prompt | string | false | Negative text prompt to exclude unwanted content. |
| num_images | integer | 1 | Number of images to generate (1-9). |
| output_format | string | png | Output image format. enum: jpeg, png, webp |
| prompt | string | false | Text prompt for image generation. Max 2500 characters. |
| resolution | string | 1K | Image resolution. 1K: standard, 2K: high-res. enum: 1K, 2K |

## Examples

**High-resolution landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A breathtaking aurora borealis over a frozen lake in Iceland, photorealistic",
      "negative_prompt": "blurry, low quality, distorted",
      "aspect_ratio": "16:9",
      "resolution": "2K",
      "output_format": "png"
    }
  }'
```

**Multiple portrait images:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A stylish fashion model in a modern studio, soft lighting, magazine cover quality",
      "aspect_ratio": "3:4",
      "num_images": 4,
      "resolution": "2K",
      "output_format": "jpeg"
    }
  }'
```

**Square image with negative prompt:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A cute corgi wearing a tiny crown, sitting on a velvet cushion",
      "negative_prompt": "ugly, deformed, extra limbs",
      "aspect_ratio": "1:1",
      "resolution": "1K"
    }
  }'
```

## Related Models

- [kling-v3-image-to-image](../kling-v3-image-to-image/) - Kling v3 image to image
- [kling-v3-standard-text-to-video](../kling-v3-standard-text-to-video/) - Kling v3 text to video
- [xai-grok-imagine-text-to-image](../xai-grok-imagine-text-to-image/) - Grok text to image

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
