---
name: cartoonify
description: "Cartoonify Cartoon Generator | Turn Photos into Cartoons. Transform photos into cartoon-style illustrations. Triggers: cartoonify, cartoon, cartoon generator, photo to cartoon, cartoon filter"
allowed-tools: Bash(curl *), WebFetch
---

# Cartoonify Cartoon Generator

Transform any photo into a cartoon-style illustration. Simply provide an image and Cartoonify will generate a cartoon version with optional seed control for reproducibility.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "cartoonify",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/portrait-photo.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| image | string | - | Input image |
| seed | integer | - | Random seed. Leave blank to randomize |

## Examples

**Cartoonify a portrait:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "cartoonify",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/selfie.jpg",
      "seed": 42
    }
  }'
```

**Cartoonify a group photo:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "cartoonify",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/group-photo.jpg"
    }
  }'
```

## Related Models

- [face-to-sticker](../face-to-sticker/) - Turn faces into sticker art
- [instant-id-ip-adapter](../instant-id-ip-adapter/) - Anime and stylized avatar generation
- [become-image](../become-image/) - Transform a person into any style

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
