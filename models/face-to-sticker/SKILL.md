---
name: face-to-sticker
description: "Face to Sticker | AI Sticker Generator. Turn face photos into fun sticker-style illustrations. Triggers: face sticker, sticker generator, face to sticker, sticker art, avatar sticker"
allowed-tools: Bash(curl *), WebFetch
---

# Face to Sticker

Turn face photos into fun sticker-style illustrations. Upload a face photo and generate stylized sticker art that preserves the person's identity with configurable prompt and style controls.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "face-to-sticker",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/selfie.jpg",
      "prompt": "a person as a cute cartoon sticker",
      "steps": 20,
      "width": 1024,
      "height": 1024
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| height | integer | 1024 | Height of the created image |
| image | string | - | Input face image |
| instant_id_strength | number | 1 | Controls intensity of identity preservation |
| ip_adapter_noise | number | 0.5 | Noise added when adapting image style |
| ip_adapter_weight | number | 0.2 | Influence of image-to-image transformation |
| negative_prompt | string | - | Aspects to avoid in the output |
| prompt | string | a person | Text prompt guiding content/style |
| prompt_strength | number | 7 | How strongly the prompt influences the output |
| seed | integer | - | Seed for reproducible results |
| steps | integer | 20 | Number of processing steps |
| upscale | boolean | false | Increase resolution of output |
| upscale_steps | integer | 10 | Steps for upscaling |
| width | integer | 1024 | Width of the created image |

## Examples

**Cute anime sticker:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "face-to-sticker",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/portrait.jpg",
      "prompt": "a person as a cute kawaii anime sticker with sparkles",
      "instant_id_strength": 0.9,
      "ip_adapter_weight": 0.3,
      "steps": 25,
      "seed": 42
    }
  }'
```

**Upscaled sticker with custom style:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "face-to-sticker",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/headshot.jpg",
      "prompt": "a person as a pop art sticker, bold outlines, bright colors",
      "negative_prompt": "blurry, low quality, distorted",
      "upscale": true,
      "upscale_steps": 15,
      "prompt_strength": 8,
      "steps": 20
    }
  }'
```

## Related Models

- [cartoonify](../cartoonify/) - Photo to cartoon transformation
- [instant-id-ip-adapter](../instant-id-ip-adapter/) - Anime and styled avatar generation
- [become-image](../become-image/) - Style transfer with identity preservation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
