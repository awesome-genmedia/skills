---
name: aifaceswap-face-swap
description: "AI Face Swap V1. Swap faces between two images using AI. Triggers: face swap, face replace, deepfake, face transfer"
allowed-tools: Bash(curl *), WebFetch
---

# AI Face Swap V1

Swap faces between two images using AI. Provide a face image (the face to use) and a source image (the image where the face will be placed) for seamless face replacement.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "aifaceswap-face-swap",
    "version": "0.0.1",
    "input": {
      "face_image": "https://example.com/face-to-swap.jpg",
      "source_image": "https://example.com/target-photo.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| face_image | string | - | URL of the face image to use as the replacement face. |
| source_image | string | - | URL of the source image where the face will be placed. |

## Examples

**Basic face swap:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "aifaceswap-face-swap",
    "version": "0.0.1",
    "input": {
      "face_image": "https://example.com/my-face.jpg",
      "source_image": "https://example.com/movie-poster.jpg"
    }
  }'
```

**Face swap on group photo:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "aifaceswap-face-swap",
    "version": "0.0.1",
    "input": {
      "face_image": "https://example.com/portrait.jpg",
      "source_image": "https://example.com/group-photo.jpg"
    }
  }'
```

## Related Models

- [Each Faceswap v1](../each-faceswap-v1/) - Each Labs face swap solution
- [Face Swap New](../face-swap-new/) - Updated face swap model
- [Faceswap Video](../faceswap-video/) - Face swap for videos

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
