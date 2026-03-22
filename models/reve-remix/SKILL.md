---
name: reve-remix
description: "Reve | Remix. Remix and transform reference images using the Reve model with text prompts. Triggers: reve, remix, image remix, transform image, reve remix"
allowed-tools: Bash(curl *), WebFetch
---

# Reve | Remix

Remix and transform reference images using the Reve model. Provide 1-4 reference images and a text prompt to create new variations. Supports XML img tags for multi-image referencing.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "reve-remix",
    "version": "0.0.1",
    "input": {
      "prompt": "Transform this landscape into a cyberpunk version with neon lights and futuristic buildings",
      "image_urls": ["https://example.com/landscape.jpg"],
      "aspect_ratio": "16:9",
      "num_images": 1,
      "output_format": "png"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The desired aspect ratio. enum: 16:9, 9:16, 3:2, 2:3, 4:3, 3:4, 1:1 |
| image_urls | array | | List of URLs of reference images (1-4 images) |
| num_images | integer | 1 | Number of images to generate |
| output_format | string | png | Output format. enum: png, jpeg, webp |
| prompt | string | | Text description of the desired image. May include XML img tags like `<img>0</img>` to reference specific images |

## Examples

**Single image remix:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "reve-remix",
    "version": "0.0.1",
    "input": {
      "prompt": "Reimagine this photo as an oil painting in the style of impressionism",
      "image_urls": ["https://example.com/park-scene.jpg"],
      "aspect_ratio": "4:3",
      "output_format": "png"
    }
  }'
```

**Multi-image reference remix:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "reve-remix",
    "version": "0.0.1",
    "input": {
      "prompt": "Combine the architecture of <img>0</img> with the color palette of <img>1</img> to create a new building design",
      "image_urls": ["https://example.com/modern-building.jpg", "https://example.com/sunset-palette.jpg"],
      "aspect_ratio": "16:9",
      "num_images": 2,
      "output_format": "jpeg"
    }
  }'
```

## Related Models

- [reve-text-to-image](../reve-text-to-image/) - Generate images from text
- [reve-edit](../reve-edit/) - Edit images with text prompts

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
