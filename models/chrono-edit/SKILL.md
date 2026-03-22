---
name: chrono-edit
description: "Chrono Edit. Edit images with optional temporal reasoning for context-aware modifications. Triggers: image editing, chrono, temporal reasoning, photo edit"
allowed-tools: Bash(curl *), WebFetch
---

# Chrono Edit

Edit images using text prompts with optional temporal reasoning for context-aware modifications. Temporal reasoning enables understanding of time-based changes in the editing process.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "chrono-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "change the season from summer to autumn with falling leaves",
      "image_url": "https://example.com/park-summer.jpg",
      "num_inference_steps": 8
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| enable_prompt_expansion | boolean | true | Whether to enable prompt expansion. |
| enable_safety_checker | boolean | true | Whether to enable the safety checker. |
| enable_temporal_reasoning | boolean | false | Whether to enable temporal reasoning. |
| image_url | string | | The image to edit. |
| num_inference_steps | integer | 8 | The number of inference steps to perform. |
| num_temporal_reasoning_steps | integer | 8 | The number of temporal reasoning steps to perform. |
| output_format | string | jpeg | The format of the output image. enum: jpeg, png, webp |
| prompt | string | | The prompt to edit the image. |
| seed | integer | | The seed for the inference. |

## Examples

**Temporal reasoning edit:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "chrono-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "age the building by 50 years, add weathering and ivy growth",
      "image_url": "https://example.com/building.jpg",
      "enable_temporal_reasoning": true,
      "num_temporal_reasoning_steps": 12,
      "output_format": "png"
    }
  }'
```

**Standard quick edit:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "chrono-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "add soft evening lighting and warm color grading",
      "image_url": "https://example.com/interior.jpg",
      "num_inference_steps": 10,
      "enable_prompt_expansion": false,
      "seed": 42
    }
  }'
```

## Related Models

- [Flux 2 | Edit](../flux-2-edit/) - Standard image editing
- [Reve | Fast | Edit](../reve-fast-edit/) - Fast image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
