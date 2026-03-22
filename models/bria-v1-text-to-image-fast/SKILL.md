---
name: bria-v1-text-to-image-fast
description: "Bria v1 | Text to Image | Fast. Fast commercially-safe image generation with image prompt guidance. Triggers: text to image, bria, fast, image generation, content safe"
allowed-tools: Bash(curl *), WebFetch
---

# Bria v1 | Text to Image | Fast

Generate images quickly with Bria's commercially-safe model. Features image prompt guidance for style/content matching, content moderation, and IP detection.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bria-v1-text-to-image-fast",
    "version": "0.0.1",
    "input": {
      "prompt": "a vibrant street market scene, fresh produce, colorful stalls",
      "aspect_ratio": "16:9",
      "num_results": 1,
      "steps_num": 8
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
| model_version | string | 2.3 | The model version. enum: 2.3 |
| num_results | integer | 4 | Number of images to generate. |
| prompt | string | | The text prompt for image generation. |
| prompt_content_moderation | boolean | true | Scan prompt for NSFW/unethical content. |
| prompt_enhancement | boolean | false | Enhance the prompt with additional detail. |
| seed | integer | | Seed for reproducible results. |
| steps_num | integer | 8 | Number of refinement iterations. |

## Examples

**Style-guided generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bria-v1-text-to-image-fast",
    "version": "0.0.1",
    "input": {
      "prompt": "cozy cabin in the snow, warm fireplace glow",
      "image_prompt_urls": ["https://example.com/style-reference.jpg"],
      "image_prompt_mode": "style_only",
      "image_prompt_scale": 0.7,
      "aspect_ratio": "4:3",
      "num_results": 2
    }
  }'
```

**Fast batch with enhancement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bria-v1-text-to-image-fast",
    "version": "0.0.1",
    "input": {
      "prompt": "minimalist logo design for a tech startup",
      "aspect_ratio": "1:1",
      "enhance_image": true,
      "prompt_enhancement": true,
      "num_results": 4,
      "medium": "art"
    }
  }'
```

## Related Models

- [Bria v1 | Text to Image | HD](../bria-v1-text-to-image-hd/) - HD quality variant
- [Bria v1 | Text to Image | Base](../bria-v1-text-to-image-base/) - Base model variant

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
