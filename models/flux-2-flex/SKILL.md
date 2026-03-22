---
name: flux-2-flex
description: "Flux 2 | Flex. Flexible text-to-image generation with guidance scale control. Triggers: text to image, flux, flex, image generation"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2 | Flex

Generate images from text prompts with flexible control over guidance scale, inference steps, and prompt expansion. Balances quality and creative freedom.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-flex",
    "version": "0.0.1",
    "input": {
      "prompt": "a serene zen garden with raked sand patterns and moss-covered stones",
      "image_size": "landscape_4_3",
      "guidance_scale": 3.5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| enable_prompt_expansion | boolean | true | Whether to expand the prompt using the model's own knowledge. |
| enable_safety_checker | boolean | true | Whether to enable the safety checker. |
| guidance_scale | number | 3.5 | The guidance scale to use for the generation. |
| image_size | string | landscape_4_3 | The size of the generated image. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9 |
| num_inference_steps | integer | 28 | The number of inference steps to perform. |
| output_format | string | jpeg | The format of the generated image. enum: jpeg, png |
| prompt | string | | The prompt to generate an image from. |
| safety_tolerance | string | 2 | The safety tolerance level. 1 is most strict, 5 is most permissive. enum: 1, 2, 3, 4, 5 |
| seed | integer | | The seed to use for the generation. |

## Examples

**High guidance landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-flex",
    "version": "0.0.1",
    "input": {
      "prompt": "aerial view of terraced rice paddies at sunrise, golden light, mist",
      "image_size": "landscape_16_9",
      "guidance_scale": 5.0,
      "num_inference_steps": 35,
      "output_format": "png"
    }
  }'
```

**Creative portrait with low guidance:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-flex",
    "version": "0.0.1",
    "input": {
      "prompt": "abstract portrait, double exposure, forest and face merging",
      "image_size": "portrait_4_3",
      "guidance_scale": 2.0,
      "enable_prompt_expansion": false,
      "seed": 42
    }
  }'
```

## Related Models

- [Flux 2 | Flex | Edit](../flux-2-flex-edit/) - Image editing with Flex
- [Flux 2 Pro](../flux-2-pro/) - Pro-quality generation
- [Flux 2](../flux-2/) - Standard Flux 2 generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
