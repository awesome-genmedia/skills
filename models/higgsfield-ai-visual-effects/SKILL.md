---
name: higgsfield-ai-visual-effects
description: "Higgsfield AI Visual Effects. Create videos with visual effects and motion from images using Higgsfield AI. Triggers: higgsfield, visual effects, vfx, video effects, motion video, higgsfield vfx"
allowed-tools: Bash(curl *), WebFetch
---

# Higgsfield AI Visual Effects

Create videos with visual effects and motion from images using Higgsfield AI. Supports multiple model tiers (lite, preview, turbo), custom motions, and end-frame control for precise video creation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "higgsfield-ai-visual-effects",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "prompt": "Person turns head with a dramatic hair flip, cinematic slow motion",
      "model": "dop-preview"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| end_input_images | array | | Images for the end frame of the video |
| enhance_prompt | boolean | false | Whether to enhance the prompt for better results |
| image_url | string | | URL of the input image |
| model | string | | Model tier. enum: dop-lite, dop-preview, dop-turbo |
| motions | array | | Motion directives for the video |
| prompt | string | | Text prompt describing the desired visual effect |
| seed | integer | | Random seed for reproducibility |

## Examples

**Turbo model with prompt enhancement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "higgsfield-ai-visual-effects",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/action-hero.jpg",
      "prompt": "Explosion in the background as the character walks forward confidently",
      "model": "dop-turbo",
      "enhance_prompt": true,
      "seed": 42
    }
  }'
```

**Lite model for quick preview:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "higgsfield-ai-visual-effects",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/landscape.jpg",
      "prompt": "Leaves swirl up from the ground in a gentle whirlwind",
      "model": "dop-lite"
    }
  }'
```

## Related Models

- [higgsfield-ai-soul](../higgsfield-ai-soul/) - Stylized image generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
