---
name: reve-fast-remix
description: "Reve | Fast | Remix. Remix images using reference images and text prompts. Triggers: image remix, reve, fast, reference images, style remix"
allowed-tools: Bash(curl *), WebFetch
---

# Reve | Fast | Remix

Remix images using 1-4 reference images combined with text prompts. Use XML img tags to reference specific images in the prompt for precise control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "reve-fast-remix",
    "version": "0.0.1",
    "input": {
      "prompt": "combine the style of <img>0</img> with the composition of <img>1</img>",
      "image_urls": ["https://example.com/style-ref.jpg", "https://example.com/composition-ref.jpg"],
      "aspect_ratio": "16:9"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated image. enum: 16:9, 9:16, 3:2, 2:3, 4:3, 3:4, 1:1 |
| image_urls | array | | List of URLs of reference images. 1 to 4 images. |
| num_images | integer | 1 | Number of images to generate. |
| output_format | string | png | Output format. enum: png, jpeg, webp |
| prompt | string | | Text description. May include XML img tags like \<img\>0\</img\> to reference images. |

## Examples

**Style remix from two references:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "reve-fast-remix",
    "version": "0.0.1",
    "input": {
      "prompt": "create a new artwork combining the color palette from <img>0</img> with the subject from <img>1</img>",
      "image_urls": ["https://example.com/color-ref.jpg", "https://example.com/subject.jpg"],
      "aspect_ratio": "1:1",
      "output_format": "png",
      "num_images": 2
    }
  }'
```

**Multi-image composition:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "reve-fast-remix",
    "version": "0.0.1",
    "input": {
      "prompt": "blend all reference images into a harmonious landscape scene",
      "image_urls": ["https://example.com/sky.jpg", "https://example.com/mountains.jpg", "https://example.com/lake.jpg"],
      "aspect_ratio": "16:9",
      "output_format": "jpeg"
    }
  }'
```

## Related Models

- [Reve | Fast | Edit](../reve-fast-edit/) - Fast image editing
- [Flux 2 | Edit](../flux-2-edit/) - Alternative image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
