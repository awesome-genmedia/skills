---
name: blip-2
description: "Blip 2 | Image Captioning and Visual Q&A. Generate captions and answer questions about images using BLIP-2. Triggers: blip, image caption, visual qa, image description, image question"
allowed-tools: Bash(curl *), WebFetch
---

# Blip 2

Generate captions and answer questions about images using BLIP-2. Supports image captioning, visual question answering, and context-aware image analysis.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "blip-2",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/photo.jpg",
      "question": "What is happening in this image?",
      "temperature": 0.5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| caption | boolean | false | Generate a descriptive caption for the image |
| context | string | - | Background information to help generate better responses |
| image | string | - | Image to analyze |
| question | string | - | Question to answer about the image |
| temperature | number | 0.5 | Controls creativity (higher = more creative, lower = more conservative) |
| use_nucleus_sampling | boolean | false | Use top-p sampling for more diverse responses |

## Examples

**Generate image caption:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "blip-2",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/landscape.jpg",
      "caption": true,
      "temperature": 0.7,
      "use_nucleus_sampling": true
    }
  }'
```

**Visual Q&A with context:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "blip-2",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/product-shelf.jpg",
      "question": "How many items are on the top shelf?",
      "context": "This is a retail store display",
      "temperature": 0.3
    }
  }'
```

## Related Models

- [nsfw-image-detection](../nsfw-image-detection/) - Content safety analysis
- [1019-face-analyzer](../1019-face-analyzer/) - Face analysis
- [rembg](../rembg/) - Background removal

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
