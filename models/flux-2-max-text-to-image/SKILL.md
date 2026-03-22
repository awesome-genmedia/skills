---
name: flux-2-max-text-to-image
description: "Flux 2 | Max | Text to Image. Generate highest quality images from text with Flux 2 Max. Triggers: text to image, flux max, high quality image, ai art generation"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2 | Max | Text to Image

Generate the highest quality images from text prompts using the Flux 2 Max model. Features built-in prompt expansion for enhanced results, configurable safety tolerance, and professional-grade output.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-max-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A photorealistic macro photograph of morning dew on a spider web, rainbow light refractions, shallow depth of field",
      "image_size": "landscape_4_3",
      "output_format": "jpeg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| enable_prompt_expansion | boolean | true | Whether to expand the prompt using the model's own knowledge. |
| enable_safety_checker | boolean | true | Whether to enable the safety checker. |
| image_size | string | landscape_4_3 | The size of the generated image. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9` |
| output_format | string | jpeg | The format of the generated image. Options: `jpeg`, `png` |
| prompt | string | - | The prompt to generate an image from. |
| safety_tolerance | string | 2 | The safety tolerance level. 1 is most strict, 5 is most permissive. Options: `1`, `2`, `3`, `4`, `5` |
| seed | integer | - | The seed to use for the generation. |

## Examples

**Simple high-quality generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-max-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A grand library with floor-to-ceiling bookshelves, warm reading lamps, and a spiral staircase"
    }
  }'
```

**Detailed generation with custom settings:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-max-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Architectural rendering of a futuristic eco-friendly skyscraper with vertical gardens",
      "enable_prompt_expansion": false,
      "image_size": "portrait_16_9",
      "output_format": "png",
      "safety_tolerance": "3",
      "seed": 2024
    }
  }'
```

## Related Models

- [Flux 2 | Max | Edit](../flux-2-max-edit/) - Edit images with Flux 2 Max quality
- [Flux 2 | Turbo | Text to Image](../flux-2-turbo-text-to-image/) - Faster generation with Flux 2 Turbo
- [Flux 2 | Flash | Text to Image](../flux-2-flash-text-to-image/) - Ultra-fast generation with Flux 2 Flash

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
