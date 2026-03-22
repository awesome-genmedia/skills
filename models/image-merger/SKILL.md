---
name: image-merger
description: "Image Merger | AI Image Blending. Merge and blend two images together with multiple merge modes and optional animation. Triggers: image merger, merge images, blend images, image blending, combine images"
allowed-tools: Bash(curl *), WebFetch
---

# Image Merger

Merge and blend two images together with multiple merge modes, optional ControlNet guidance, upscaling, and animation support. Create seamless composites from separate source images.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "image-merger",
    "version": "0.0.1",
    "input": {
      "image_1": "https://example.com/landscape.jpg",
      "image_2": "https://example.com/portrait.jpg",
      "prompt": "a person standing in a beautiful mountain landscape",
      "merge_mode": "full",
      "steps": 20
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| animate | boolean | false | Animate merging from one image to the other (returns video) |
| animate_frames | integer | 24 | Number of frames for the animation |
| control_image | string | - | Optional image to influence merging with ControlNet |
| height | integer | 768 | Output height |
| image_1 | string | - | First image |
| image_1_strength | number | 1 | Strength of the first image |
| image_2 | string | - | Second image |
| image_2_strength | number | 1 | Strength of the second image |
| merge_mode | string | full | Merge mode. enum: full, left_right, top_bottom |
| negative_prompt | string | ugly, broken, distorted | Things to avoid in the merged image |
| prompt | string | a photo | Prompt to guide image merging |
| return_temp_files | boolean | false | Return preprocessed controlnet images for debugging |
| seed | integer | - | Fix random seed for reproducibility |
| steps | integer | 20 | Number of steps |
| upscale_2x | boolean | false | Upscale output 2x |
| upscale_steps | integer | 20 | Steps per controlnet tile for upscaling |
| width | integer | 768 | Output width |

## Examples

**Split merge (left-right):**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "image-merger",
    "version": "0.0.1",
    "input": {
      "image_1": "https://example.com/summer-scene.jpg",
      "image_2": "https://example.com/winter-scene.jpg",
      "prompt": "a landscape transitioning from summer to winter, seamless blend",
      "merge_mode": "left_right",
      "image_1_strength": 1,
      "image_2_strength": 1,
      "steps": 25
    }
  }'
```

**Animated merge transition:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "image-merger",
    "version": "0.0.1",
    "input": {
      "image_1": "https://example.com/young-portrait.jpg",
      "image_2": "https://example.com/old-portrait.jpg",
      "prompt": "a portrait of a person aging gracefully",
      "animate": true,
      "animate_frames": 30,
      "steps": 20,
      "seed": 42
    }
  }'
```

## Related Models

- [become-image](../become-image/) - Transform a person into any style
- [face-swap-new](../face-swap-new/) - Face swapping between images
- [flux-fill-pro](../flux-fill-pro/) - Inpainting and image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
