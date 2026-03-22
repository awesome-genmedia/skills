---
name: kling-v3-image-to-image
description: "Kling | v3 | Image to Image. Transform images with text prompts, face control elements, and up to 2K resolution. Triggers: image to image, kling, v3, transform, i2i"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | v3 | Image to Image

Transform existing images using text prompts with Kling v3. Supports face control elements, multiple aspect ratios, and up to 2K resolution output.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-image-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Transform this photo into a watercolor painting style",
      "image_url": "https://example.com/photo.jpg",
      "aspect_ratio": "16:9",
      "resolution": "1K"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio of generated images. enum: 16:9, 9:16, 1:1, 4:3, 3:4, 3:2, 2:3, 21:9 |
| elements | array | false | Optional elements (characters/objects) for face control. |
| image_url | string | false | Reference image for image-to-image generation. |
| num_images | integer | 1 | Number of images to generate (1-9). |
| output_format | string | png | Output image format. enum: jpeg, png, webp |
| prompt | string | false | Text prompt for image generation. Max 2500 characters. |
| resolution | string | 1K | Image resolution. 1K: standard, 2K: high-res. enum: 1K, 2K |

## Examples

**Style transfer:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-image-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Convert to anime style with vivid colors and detailed background",
      "image_url": "https://example.com/cityscape.jpg",
      "aspect_ratio": "16:9",
      "resolution": "2K",
      "output_format": "png"
    }
  }'
```

**Generate multiple variations:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-image-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Reimagine this scene as a fantasy landscape with dragons and castles",
      "image_url": "https://example.com/landscape.jpg",
      "num_images": 4,
      "resolution": "1K",
      "output_format": "jpeg"
    }
  }'
```

**Portrait transformation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-image-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Transform into a Renaissance oil painting portrait",
      "image_url": "https://example.com/portrait.jpg",
      "aspect_ratio": "3:4",
      "resolution": "2K"
    }
  }'
```

## Related Models

- [kling-v3-text-to-image](../kling-v3-text-to-image/) - Kling v3 text to image
- [kling-v3-standard-image-to-video](../kling-v3-standard-image-to-video/) - Kling v3 image to video
- [nano-banana-2-edit](../nano-banana-2-edit/) - Nano Banana 2 image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
