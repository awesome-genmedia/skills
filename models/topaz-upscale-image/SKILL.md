---
name: topaz-upscale-image
description: "Topaz | Image Upscale. Upscale and enhance images using Topaz AI with face enhancement and multiple model options. Triggers: topaz, upscale, image upscale, enhance image, super resolution"
allowed-tools: Bash(curl *), WebFetch
---

# Topaz | Image Upscale

Upscale and enhance images using Topaz AI. Supports multiple enhancement models, face enhancement with adjustable creativity and strength, configurable upscale factor, and subject detection modes.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "topaz-upscale-image",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/low-res-photo.jpg",
      "upscale_factor": 2,
      "model": "Standard V2",
      "face_enhancement": true,
      "output_format": "jpeg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| crop_to_fill | boolean | false | Whether to crop the image to fill the output dimensions |
| face_enhancement | boolean | true | Whether to apply face enhancement to the image |
| face_enhancement_creativity | number | 0 | Creativity level for face enhancement (0.0 to 1.0) |
| face_enhancement_strength | number | 0.8 | Strength of face enhancement (0.0 to 1.0) |
| image_url | string | | URL of the image to be upscaled |
| model | string | Standard V2 | Enhancement model. enum: Low Resolution V2, Standard V2, CGI, High Fidelity V2, Text Refine, Recovery, Redefine, Recovery V2 |
| output_format | string | jpeg | Output format. enum: jpeg, png |
| subject_detection | string | All | Subject detection mode. enum: All, Foreground, Background |
| upscale_factor | number | 2 | Factor to upscale the image by (e.g. 2.0 doubles width and height) |

## Examples

**High-fidelity portrait upscale with face enhancement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "topaz-upscale-image",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "upscale_factor": 4,
      "model": "High Fidelity V2",
      "face_enhancement": true,
      "face_enhancement_strength": 0.9,
      "face_enhancement_creativity": 0.2,
      "output_format": "png"
    }
  }'
```

**CGI render upscale without face enhancement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "topaz-upscale-image",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/3d-render.jpg",
      "upscale_factor": 2,
      "model": "CGI",
      "face_enhancement": false,
      "subject_detection": "Foreground",
      "output_format": "png"
    }
  }'
```

**Low resolution image recovery:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "topaz-upscale-image",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/old-photo.jpg",
      "upscale_factor": 4,
      "model": "Low Resolution V2",
      "face_enhancement": true,
      "face_enhancement_strength": 1.0,
      "face_enhancement_creativity": 0.5
    }
  }'
```

## Related Models

- [tencent-flux-srpo-image-to-image](../tencent-flux-srpo-image-to-image/) - AI-powered image enhancement and transformation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
