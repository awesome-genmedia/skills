---
name: bria-v1-text-to-image-hd
description: "Bria v1 | Text to Image | HD. Generate HD images with content moderation and IP protection. Triggers: text to image, bria, hd, image generation, content safe"
allowed-tools: Bash(curl *), WebFetch
---

# Bria v1 | Text to Image | HD

Generate HD images with Bria's commercially-safe model. Features built-in content moderation, IP content detection, and medium selection for photography or art styles.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bria-v1-text-to-image-hd",
    "version": "0.0.1",
    "input": {
      "prompt": "professional product photography of a luxury watch on marble",
      "aspect_ratio": "1:1",
      "medium": "photography",
      "num_results": 1,
      "steps_num": 30
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | The aspect ratio. enum: 1:1, 2:3, 3:2, 3:4, 4:3, 4:5, 5:4, 9:16, 16:9 |
| content_moderation | boolean | false | Apply content moderation to generated outputs. |
| enhance_image | boolean | false | Generate images with richer details and sharper textures. |
| ip_signal | boolean | false | Flag prompts with potential IP content. |
| medium | string | | Medium for generated images. enum: photography, art |
| model_version | string | 2.2 | The model version. enum: 2.2 |
| negative_prompt | string | | Elements to avoid in generation. |
| num_results | integer | 4 | Number of images to generate. |
| prompt | string | | The text prompt for image generation. |
| prompt_enhancement | boolean | false | Enhance the prompt with additional detail. |
| seed | integer | | Seed for reproducible results. |
| steps_num | integer | 30 | Number of refinement iterations. |
| text_guidance_scale | integer | 5 | How closely to follow the text description. |

## Examples

**Art medium with enhancement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bria-v1-text-to-image-hd",
    "version": "0.0.1",
    "input": {
      "prompt": "impressionist painting of a Parisian cafe at dusk, warm lamplight",
      "aspect_ratio": "4:3",
      "medium": "art",
      "enhance_image": true,
      "num_results": 2,
      "steps_num": 35,
      "text_guidance_scale": 7
    }
  }'
```

**Commercial-safe photography:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bria-v1-text-to-image-hd",
    "version": "0.0.1",
    "input": {
      "prompt": "modern office workspace with plants and natural light",
      "aspect_ratio": "16:9",
      "medium": "photography",
      "content_moderation": true,
      "ip_signal": true,
      "negative_prompt": "blurry, low quality, cluttered",
      "seed": 42
    }
  }'
```

## Related Models

- [Bria v1 | Text to Image | Fast](../bria-v1-text-to-image-fast/) - Faster generation variant
- [Bria v1 | Text to Image | Base](../bria-v1-text-to-image-base/) - Base model variant

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
