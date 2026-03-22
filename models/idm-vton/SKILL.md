---
name: idm-vton
description: "IDM VTON | Virtual Try-On. Try on clothes virtually by combining a garment image with a person photo. Triggers: virtual try on, vton, clothing try on, garment fitting, try on clothes"
allowed-tools: Bash(curl *), WebFetch
---

# IDM VTON

Virtual try-on that combines a garment image with a person photo. Upload a model photo and a garment image to see how clothes look on the person, supporting upper body, lower body, and dresses.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "idm-vton",
    "version": "0.0.1",
    "input": {
      "human_img": "https://example.com/model-photo.jpg",
      "garm_img": "https://example.com/tshirt.jpg",
      "garment_des": "Short Sleeve Round Neck T-shirt",
      "category": "upper_body",
      "steps": 30
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| category | string | upper_body | Garment category. enum: upper_body, lover_body, dresses |
| crop | boolean | true | Crop the image if not 3:4 aspect ratio |
| force_dc | boolean | false | Use the DressCode version of IDM-VTON |
| garm_img | string | - | Garment image (product image or photo of clothing) |
| garment_des | string | - | Description of garment, e.g., "Short Sleeve Round Neck T-shirt" |
| human_img | string | - | Model/person photo (3:4 aspect ratio recommended) |
| mask_img | string | - | Mask image, optional but speeds up processing |
| mask_only | boolean | false | Return only the mask |
| seed | integer | 42 | Random seed |
| steps | integer | 30 | Number of generation steps |

## Examples

**Try on a dress:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "idm-vton",
    "version": "0.0.1",
    "input": {
      "human_img": "https://example.com/model-standing.jpg",
      "garm_img": "https://example.com/summer-dress.jpg",
      "garment_des": "Floral print summer dress with v-neck",
      "category": "dresses",
      "crop": true,
      "steps": 30,
      "seed": 42
    }
  }'
```

**Try on pants with mask:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "idm-vton",
    "version": "0.0.1",
    "input": {
      "human_img": "https://example.com/full-body-photo.jpg",
      "garm_img": "https://example.com/jeans.jpg",
      "garment_des": "Slim fit dark blue denim jeans",
      "category": "lover_body",
      "mask_img": "https://example.com/pants-mask.jpg",
      "steps": 30
    }
  }'
```

## Related Models

- [face-swap-new](../face-swap-new/) - Face swapping between images
- [become-image](../become-image/) - Style transfer with identity preservation
- [realistic-background](../realistic-background/) - Background replacement

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
