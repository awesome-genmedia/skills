---
name: vidu-q2-reference-to-image
description: "Vidu Q2 | Reference to Image. Generate images using reference images for consistent subject appearance. Triggers: reference to image, vidu, consistent character, image generation"
allowed-tools: Bash(curl *), WebFetch
---

# Vidu Q2 | Reference to Image

Generate images using reference images to maintain consistent subject appearance across generations. Combine text prompts with visual references for precise control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-q2-reference-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "the character standing in front of a castle, heroic pose",
      "reference_image_urls": ["https://example.com/character-ref.jpg"],
      "aspect_ratio": "16:9"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the output image. enum: 16:9, 9:16, 1:1 |
| prompt | string | | Text prompt for image generation, max 1500 characters. |
| reference_image_urls | array | | URLs of the reference images to use for consistent subject appearance. |
| seed | integer | | Random seed for generation. |

## Examples

**Character in new scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-q2-reference-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "the person sitting in a modern coffee shop, reading a book",
      "reference_image_urls": ["https://example.com/person-ref.jpg"],
      "aspect_ratio": "1:1",
      "seed": 42
    }
  }'
```

**Multiple references for consistency:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-q2-reference-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "the character wearing a spacesuit, walking on Mars surface",
      "reference_image_urls": ["https://example.com/char-front.jpg", "https://example.com/char-side.jpg"],
      "aspect_ratio": "16:9"
    }
  }'
```

## Related Models

- [Vidu Q2 | Text to Image](../vidu-q2-text-to-image/) - Generate images from text only
- [Kling O1](../kling-o1/) - Image generation with reference image support

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
