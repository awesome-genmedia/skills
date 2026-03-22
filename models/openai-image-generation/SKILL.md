---
name: openai-image-generation
description: "GPT-1 | Image Generation. Generate images from text prompts using GPT-1 | Image Generation. Triggers: image generation, openai"
allowed-tools: Bash(curl *), WebFetch
---

# GPT-1 | Image Generation

Generate images from text prompts using GPT-1 | Image Generation. Supports quality control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "openai-image-generation",
    "version": "0.0.1",
    "input": {
      "prompt": "A watercolor painting of a cozy bookshop on a rainy day"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `background` | string | auto | Options: `auto`, `transparent`, `opaque` |
| `image_size` | string | auto | Options: `auto`, `1024x1024`, `1536x1024`, `1024x1536` |
| `number_of_images` | integer | 1 |  |
| `output_compression` | integer |  |  |
| `output_format` | string | jpeg | Options: `png`, `jpeg`, `webp` |
| `prompt` | string |  |  |
| `quality` | string | auto | Options: `auto`, `high`, `medium`, `low` |

## Examples

**Generate a landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "openai-image-generation",
    "version": "0.0.1",
    "input": {
      "prompt": "A watercolor painting of a cozy bookshop on a rainy day"
    }
  }'
```

**Detailed scene with style:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "openai-image-generation",
    "version": "0.0.1",
    "input": {
      "prompt": "An isometric 3D render of a tiny Japanese garden with a koi pond",
      "image_size": "1536x1024",
      "quality": "high"
    }
  }'
```

## Related Models

- [GPT-1 | Image Edit](../openai-image-edit/) - Edit images using AI with GPT-1 | Image Edit.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
