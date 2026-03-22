---
name: bria-v1-text-to-image-base
description: "Bria v1 | Text to Image | Base. Base commercially-safe image generation with image prompt guidance. Triggers: text to image, bria, base, image generation, content safe"
allowed-tools: Bash(curl *), WebFetch
---

# Bria v1 | Text to Image | Base

Generate commercially-safe images with Bria's base model. Features image prompt guidance, content moderation, IP detection, and full control over guidance and iteration parameters.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bria-v1-text-to-image-base",
    "version": "0.0.1",
    "input": {
      "prompt": "a modern kitchen interior, clean design, natural light",
      "aspect_ratio": "16:9",
      "num_results": 1,
      "steps_num": 30
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | The aspect ratio. enum: 1:1, 2:3, 3:2, 3:4, 4:3, 4:5, 5:4, 9:16, 16:9 |
| content_moderation | boolean | false | Apply content moderation to inputs and outputs. |
| enhance_image | boolean | false | Generate images with richer details and sharper textures. |
| image_prompt_mode | string | regular | Image prompt mode. enum: regular, style_only |
| image_prompt_scale | number | 1 | Impact of the provided image (0.0-1.0). |
| image_prompt_urls | array | | URLs of guidance images for style/content matching. |
| ip_signal | boolean | false | Flag prompts with potential IP content. |
| medium | string | | Medium for generated images. enum: photography, art |
| model_version | string | 2.3 | The model version. enum: 2.3, 3.2 |
| negative_prompt | string | | Elements to avoid in generation. |
| num_results | integer | 4 | Number of images to generate. |
| prompt | string | | The text prompt for image generation. |
| prompt_content_moderation | boolean | true | Scan prompt for NSFW/unethical content. |
| prompt_enhancement | boolean | false | Enhance the prompt with additional detail. |
| seed | integer | | Seed for reproducible results. |
| steps_num | integer | 30 | Number of refinement iterations. |
| text_guidance_scale | integer | 5 | How closely to follow the text description. |

## Examples

**Image-guided generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bria-v1-text-to-image-base",
    "version": "0.0.1",
    "input": {
      "prompt": "corporate headshot, professional lighting, neutral background",
      "image_prompt_urls": ["https://example.com/reference-portrait.jpg"],
      "image_prompt_mode": "regular",
      "image_prompt_scale": 0.6,
      "aspect_ratio": "3:4",
      "medium": "photography",
      "num_results": 4,
      "steps_num": 30,
      "text_guidance_scale": 7
    }
  }'
```

**v3.2 model with enhancement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bria-v1-text-to-image-base",
    "version": "0.0.1",
    "input": {
      "prompt": "abstract digital artwork, flowing neon shapes, dark background",
      "model_version": "3.2",
      "aspect_ratio": "1:1",
      "medium": "art",
      "enhance_image": true,
      "negative_prompt": "blurry, pixelated, low resolution",
      "seed": 42
    }
  }'
```

## Related Models

- [Bria v1 | Text to Image | HD](../bria-v1-text-to-image-hd/) - HD quality variant
- [Bria v1 | Text to Image | Fast](../bria-v1-text-to-image-fast/) - Faster generation variant

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
