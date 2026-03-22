---
name: "Post Processing Blur"
description: "Apply blur effects to images. Trigger: Use when the user wants to blur an image, or requests 'blur image', 'gaussian blur', 'soften image', or 'post processing blur'."
allowed-tools: ["Bash"]
---

# Post Processing | Blur

Apply blur effects to images using Gaussian or Kuwahara blur modes. Adjustable radius and sigma for fine control.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "post-processing-blur",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/photo.jpg",
      "blur_type": "gaussian",
      "blur_radius": 3,
      "blur_sigma": 1
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `blur_radius` | integer | `3` | Blur radius |
| `blur_sigma` | number | `1` | Sigma for Gaussian blur |
| `blur_type` | string | `gaussian` | Blur type. Options: `gaussian`, `kuwahara` |
| `image_url` | string | (empty) | URL of image to process |

## Output

- **Type:** image

## Examples

### Soft Gaussian Blur
```json
{
  "model": "post-processing-blur",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/background.jpg",
    "blur_type": "gaussian",
    "blur_radius": 5,
    "blur_sigma": 2
  }
}
```

### Kuwahara Painterly Effect
```json
{
  "model": "post-processing-blur",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/landscape.jpg",
    "blur_type": "kuwahara",
    "blur_radius": 4
  }
}
```

## Related Models

- [Post Processing Combine](../post-processing/SKILL.md) - Apply multiple effects at once
- [Post Processing Sharpen](../post-processing-sharpen/SKILL.md) - Sharpen images
- [Post Processing Chromatic Aberration](../post-processing-chromatic-aberration/SKILL.md) - Chromatic effects

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
