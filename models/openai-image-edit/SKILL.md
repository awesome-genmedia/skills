---
name: openai-image-edit
description: "GPT-1 | Image Edit. Edit images using AI with GPT-1 | Image Edit. Triggers: image editing, image generation, openai"
allowed-tools: Bash(curl *), WebFetch
---

# GPT-1 | Image Edit

Edit images using AI with GPT-1 | Image Edit. Supports quality control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "openai-image-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Add a fluffy cat sitting on the windowsill",
      "image_url": "https://example.com/room-photo.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `background` | string | auto | Options: `auto`, `transparent`, `opaque` |
| `image_size` | string | auto | Options: `auto`, `1024x1024`, `1536x1024`, `1024x1536` |
| `image_url_1` | string |  |  |
| `image_url_10` | string |  |  |
| `image_url_11` | string |  |  |
| `image_url_12` | string |  |  |
| `image_url_13` | string |  |  |
| `image_url_14` | string |  |  |
| `image_url_15` | string |  |  |
| `image_url_16` | string |  |  |
| `image_url_2` | string |  |  |
| `image_url_3` | string |  |  |
| `image_url_4` | string |  |  |
| `image_url_5` | string |  |  |
| `image_url_6` | string |  |  |
| `image_url_7` | string |  |  |
| `image_url_8` | string |  |  |
| `image_url_9` | string |  |  |
| `mask_url` | string |  |  |
| `number_of_images` | integer | 1 |  |
| `prompt` | string |  |  |
| `quality` | string | auto | Options: `auto`, `high`, `medium`, `low` |

## Examples

**Edit an image:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "openai-image-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Add a fluffy cat sitting on the windowsill",
      "image_url": "https://example.com/room-photo.jpg"
    }
  }'
```

**Advanced image editing:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "openai-image-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Replace the background with a tropical beach sunset",
      "image_url": "https://example.com/portrait.jpg"
    }
  }'
```

## Related Models

- [GPT-1 | Image Generation](../openai-image-generation/) - Generate images from text prompts using GPT-1 | Image Generation.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
