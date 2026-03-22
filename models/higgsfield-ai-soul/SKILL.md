---
name: higgsfield-ai-soul
description: "Higgsfield AI Soul. Generate stylized images from prompts and reference photos using Higgsfield AI Soul with 70+ creative styles. Triggers: higgsfield, soul, stylized image, ai portrait, photo style, higgsfield soul"
allowed-tools: Bash(curl *), WebFetch
---

# Higgsfield AI Soul

Generate stylized images from prompts and reference photos using Higgsfield AI Soul. Choose from 70+ creative styles including Realistic, Anime, Vintage, Fashion, and more. Supports custom references and batch generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "higgsfield-ai-soul",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/selfie.jpg",
      "prompt": "A stunning portrait in a modern setting",
      "quality": "1080p",
      "aspect_ratio": "1536x2048"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | | Output dimensions. enum: 1152x2048, 2048x1152, 2048x1536, 1536x2048, 1344x2016, 2016x1344, 960x1696, 1536x1536, 1536x1152, 1696x960, 1152x1536, 1088x1632, 1632x1088 |
| batch_size | integer | 1 | Number of images to generate |
| custom_reference_id | string | | Custom reference ID for consistent styling |
| custom_reference_strength | number | | Strength of custom reference influence |
| image_url | string | | URL of the input reference image |
| prompt | string | | Text prompt describing the desired image |
| quality | string | 720p | Output quality. enum: 720p, 1080p |
| seed | integer | | Random seed for reproducibility |
| style_id | string | | Style preset ID (choose from 70+ styles like Realistic, Creatures, Medieval, etc.) |
| style_strength | number | | Strength of the style influence |

## Examples

**Stylized portrait with preset:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "higgsfield-ai-soul",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/profile-photo.jpg",
      "prompt": "Professional headshot with dramatic lighting",
      "style_id": "1cb4b936-77bf-4f9a-9039-f3d349a4cdbe",
      "quality": "1080p",
      "aspect_ratio": "1536x2048",
      "batch_size": 1
    }
  }'
```

**Batch generation with seed:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "higgsfield-ai-soul",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/photo.jpg",
      "prompt": "Creative fashion editorial in a futuristic city",
      "quality": "720p",
      "aspect_ratio": "2048x1152",
      "batch_size": 4,
      "seed": 42
    }
  }'
```

## Related Models

- [higgsfield-ai-visual-effects](../higgsfield-ai-visual-effects/) - Visual effects and video generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
