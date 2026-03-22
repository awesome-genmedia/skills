---
name: xai-grok-imagine-text-to-image
description: "XAI | Grok | Imagine | Text to Image. Generate images from text prompts using xAI Grok Imagine. Triggers: text to image, grok, xai, generate image, t2i"
allowed-tools: Bash(curl *), WebFetch
---

# XAI | Grok | Imagine | Text to Image

Generate images from text descriptions using xAI's Grok Imagine with configurable aspect ratios and output formats.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-imagine-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A photorealistic portrait of a space explorer on Mars with a red planet landscape behind them",
      "aspect_ratio": "16:9",
      "num_images": 1,
      "output_format": "jpeg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | Aspect ratio. enum: 1:1, 3:4, 4:3, 9:16, 16:9 |
| num_images | integer | 1 | Number of images to generate. |
| output_format | string | jpeg | Output format. enum: jpeg, png, webp |
| prompt | string | | Text description of the desired image. |

## Examples

**Widescreen landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-imagine-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "An enchanted forest with bioluminescent mushrooms and floating fireflies at twilight",
      "aspect_ratio": "16:9",
      "output_format": "png"
    }
  }'
```

**Multiple portrait images:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-imagine-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A steampunk inventor in their workshop surrounded by brass gears and copper pipes",
      "aspect_ratio": "3:4",
      "num_images": 3,
      "output_format": "jpeg"
    }
  }'
```

**Square product shot:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-imagine-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A minimalist product photo of a luxury watch on a marble surface with soft studio lighting",
      "aspect_ratio": "1:1",
      "output_format": "webp"
    }
  }'
```

## Related Models

- [xai-grok-imagine-image-edit](../xai-grok-imagine-image-edit/) - Grok image editing
- [xai-grok-imagine-text-to-video](../xai-grok-imagine-text-to-video/) - Grok text to video
- [kling-v3-text-to-image](../kling-v3-text-to-image/) - Kling v3 text to image

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
