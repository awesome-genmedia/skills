---
name: reve-fast-edit
description: "Reve | Fast | Edit. Fast image editing with text prompts. Triggers: image editing, reve, fast, photo edit"
allowed-tools: Bash(curl *), WebFetch
---

# Reve | Fast | Edit

Quickly edit images using text descriptions with Reve's fast editing model. Streamlined parameters for rapid iterations.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "reve-fast-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "change the hair color to blonde",
      "image_url": "https://example.com/portrait.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| image_url | string | | URL of the reference image to edit. Must be publicly accessible or base64 data URL. |
| num_images | integer | 1 | Number of images to generate. |
| output_format | string | png | Output format. enum: png, jpeg, webp |
| prompt | string | | The text description of how to edit the provided image. |

## Examples

**Background change:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "reve-fast-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "replace the background with a sunny beach, keep the subject unchanged",
      "image_url": "https://example.com/person.jpg",
      "output_format": "jpeg",
      "num_images": 2
    }
  }'
```

**Object modification:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "reve-fast-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "change the car color from red to blue, keep everything else the same",
      "image_url": "https://example.com/car.jpg",
      "output_format": "png"
    }
  }'
```

## Related Models

- [Reve | Fast | Remix](../reve-fast-remix/) - Remix images with references
- [Flux 2 | Edit](../flux-2-edit/) - Alternative image editing model

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
