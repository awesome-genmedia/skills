---
name: vidu-template
description: "Vidu Template. Generate videos from predefined templates using Vidu Template. Triggers: video generation, video template, vidu"
allowed-tools: Bash(curl *), WebFetch
---

# Vidu Template

Generate videos from predefined templates using Vidu Template. Supports multiple aspect ratios (16:9, 1:1, 9:16), reproducible results via seed.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-template",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/your-photo.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `area` | string | auto | The area of the generated video Default value: auto. Options: `auto`, `denmark`, `uk`, `africa`, `china`, `mexico`, `switzerland`, `russia`, `italy... |
| `aspect_ratio` | string |  | Options: `16:9`, `1:1`, `9:16` |
| `beast` | string | auto | The beast of the generated video Default value: auto. Options: `auto`, `bear`, `tiger`, `elk`, `snake`, `lion`, `wolf` |
| `bgm` | boolean |  | Whether to add background music to the generated video. |
| `image_url` | string |  |  |
| `image_url_2` | string |  |  |
| `image_url_3` | string |  |  |
| `seed` | integer |  |  |
| `template_name` | string | minecraft |  |

## Examples

**Generate from template:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-template",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/your-photo.jpg"
    }
  }'
```

**Dynamic template video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-template",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/your-image.jpg",
      "aspect_ratio": "9:16",
      "seed": 42
    }
  }'
```

## Related Models

- [Vidu Q1 | Start End to Video](../vidu-q-1-start-end-to-video/) - Generate videos from start and end frame images using Vidu Q1 | Start End to Video.
- [Vidu Q1 | Image to Video](../vidu-q-1-image-to-video/) - Generate videos from images using Vidu Q1 | Image to Video.
- [Vidu 1.5 | Image to Video](../vidu-1-5-image-to-video/) - Generate videos from images using Vidu 1.5 | Image to Video.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
