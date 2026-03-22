---
name: wan-2-5-preview-image-to-image
description: "Wan | 2.5 | Preview | Image to Image. Edit and transform images using the Wan 2.5 Preview model with single or multi-reference support. Triggers: wan, image to image, image edit, wan 2.5, image transform"
allowed-tools: Bash(curl *), WebFetch
---

# Wan | 2.5 | Preview | Image to Image

Edit and transform images using the Wan 2.5 Preview model. Supports single-image editing and multi-reference input for style transfer, with configurable negative prompts and batch output.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-2-5-preview-image-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Transform this photo into a watercolor painting style",
      "image_urls": ["https://example.com/landscape.jpg"],
      "image_size": "landscape_16_9",
      "num_images": 1
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| image_size | string | square_hd | The size of the generated image. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9 |
| image_urls | array | | URLs of images to edit. Single URL for editing, multiple for multi-reference |
| negative_prompt | string | | Negative prompt to describe content to avoid (max 500 chars) |
| num_images | integer | 1 | Number of images to generate (1-4) |
| prompt | string | | Text prompt describing how to edit the image (max 2000 chars) |
| seed | integer | | Random seed for reproducibility |

## Examples

**Style transfer with negative prompt:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-2-5-preview-image-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Convert this photograph into an oil painting in the style of Van Gogh with bold brushstrokes",
      "image_urls": ["https://example.com/starry-night-photo.jpg"],
      "image_size": "landscape_4_3",
      "negative_prompt": "blurry, low quality, text, watermark",
      "num_images": 2,
      "seed": 42
    }
  }'
```

**Multi-reference image editing:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-2-5-preview-image-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Combine the subject from the first image with the background from the second image",
      "image_urls": ["https://example.com/subject.jpg", "https://example.com/background.jpg"],
      "image_size": "square_hd",
      "num_images": 1
    }
  }'
```

## Related Models

- [wan-2-5-preview-text-to-image](../wan-2-5-preview-text-to-image/) - Text to image generation
- [wan-2-5-preview-image-to-video](../wan-2-5-preview-image-to-video/) - Image to video
- [wan-2-5-preview-text-to-video](../wan-2-5-preview-text-to-video/) - Text to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
