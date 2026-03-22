---
name: nano-banana-2-text-to-image
description: "Nano Banana 2 | Text to Image. Generate images from text prompts at up to 4K resolution with multiple aspect ratios. Triggers: text to image, nano banana, generate image, t2i"
allowed-tools: Bash(curl *), WebFetch
---

# Nano Banana 2 | Text to Image

Generate images from text descriptions with support for resolutions up to 4K, multiple aspect ratios, and various output formats.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "nano-banana-2-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A majestic castle on a cliff overlooking the ocean at sunset",
      "aspect_ratio": "16:9",
      "resolution": "2K"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | Aspect ratio. enum: 1:1, 3:2, 2:3, 3:4, 4:3, 4:5, 5:4, 9:16, 16:9, 21:9 |
| limit_generations | boolean | true | Experimental parameter to limit generations from each processing round. |
| num_images | integer | 1 | Number of images to generate. |
| output_format | string | png | Output image format. enum: jpeg, png, webp |
| prompt | string | | The text prompt to generate an image from. |
| resolution | string | 1K | Resolution of the generated image. enum: 1K, 2K, 4K |

## Examples

**High-resolution landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "nano-banana-2-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A serene Japanese zen garden with cherry blossoms and a koi pond",
      "aspect_ratio": "16:9",
      "resolution": "4K",
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
    "model": "nano-banana-2-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A fantasy elf warrior in enchanted forest, detailed armor, cinematic lighting",
      "aspect_ratio": "9:16",
      "num_images": 3,
      "resolution": "2K",
      "output_format": "jpeg"
    }
  }'
```

**Ultrawide cinematic shot:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "nano-banana-2-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A futuristic megacity skyline at night with flying vehicles and holographic billboards",
      "aspect_ratio": "21:9",
      "resolution": "2K"
    }
  }'
```

## Related Models

- [nano-banana-2-edit](../nano-banana-2-edit/) - Nano Banana 2 image editing
- [kling-v3-text-to-image](../kling-v3-text-to-image/) - Kling v3 text to image
- [xai-grok-imagine-text-to-image](../xai-grok-imagine-text-to-image/) - Grok text to image

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
