---
name: face-swap-new
description: "Face Swap | AI Face Swapping. Swap faces between two images seamlessly. Triggers: face swap, swap face, face replacement, face transfer, swap faces"
allowed-tools: Bash(curl *), WebFetch
---

# Face Swap

Swap faces between two images seamlessly. Provide a target image and a swap image to transfer the face from the swap image onto the target.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "face-swap-new",
    "version": "0.0.1",
    "input": {
      "input_image": "https://example.com/target-photo.jpg",
      "swap_image": "https://example.com/face-source.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| input_image | string | - | Target image (the body/scene to keep) |
| swap_image | string | - | Swap image (the face to transfer) |

## Examples

**Swap face onto a portrait:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "face-swap-new",
    "version": "0.0.1",
    "input": {
      "input_image": "https://example.com/professional-headshot.jpg",
      "swap_image": "https://example.com/my-selfie.jpg"
    }
  }'
```

**Face swap onto a scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "face-swap-new",
    "version": "0.0.1",
    "input": {
      "input_image": "https://example.com/movie-still.jpg",
      "swap_image": "https://example.com/face-photo.jpg"
    }
  }'
```

## Related Models

- [become-image](../become-image/) - Style transfer with identity preservation
- [instant-id](../instant-id/) - Instant ID avatar generation
- [photomaker](../photomaker/) - Photo generation with identity preservation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
