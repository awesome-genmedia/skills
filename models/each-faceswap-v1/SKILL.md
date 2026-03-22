---
name: each-faceswap-v1
description: "Eachlabs Face Swap. Swap faces in images using Eachlabs Face Swap. Triggers: eachlabs, face swap, image generation"
allowed-tools: Bash(curl *), WebFetch
---

# Eachlabs Face Swap

Swap faces in images using Eachlabs Face Swap.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "each-faceswap-v1",
    "version": "0.0.1",
    "input": {
      "source_image": "https://example.com/source-face.jpg",
      "target_image_gif_or_video": "https://example.com/target-image.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `source_image` | string |  | The image containing the face to be swapped. |
| `target_image_gif_or_video` | string |  | The image where the swapped face will be placed. |

## Examples

**Basic face swap:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "each-faceswap-v1",
    "version": "0.0.1",
    "input": {
      "source_image": "https://example.com/source-face.jpg",
      "target_image_gif_or_video": "https://example.com/target-image.jpg"
    }
  }'
```

**Portrait face swap:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "each-faceswap-v1",
    "version": "0.0.1",
    "input": {
      "source_image": "https://example.com/portrait.jpg",
      "target_image_gif_or_video": "https://example.com/group-photo.jpg"
    }
  }'
```

## Related Models

- [Eachlabs Image Generation](../eachlabs-image-generation/) - Generate images from text prompts using Eachlabs Image Generation.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
