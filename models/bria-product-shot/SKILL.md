---
name: "Bria Product Shot"
description: "Generate lifestyle product shots by placing products in new scenes. Trigger: Use when the user wants to create product photography, or requests 'bria product shot', 'product lifestyle photo', or 'place product in scene'."
allowed-tools: ["Bash"]
---

# Bria | Product Shot

Generate professional lifestyle product shots by placing a product into a new scene or background. Supports automatic and manual product placement, reference images for scene style, and configurable output sizes.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bria-product-shot",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/product.png",
      "scene_description": "Elegant marble countertop with soft natural lighting and green plants in the background",
      "placement_type": "automatic",
      "num_results": 1
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `fast` | boolean | `true` | Whether to use the fast model |
| `image_url` | string | (empty) | The URL of the product shot to be placed in a lifestyle shot |
| `manual_placement_selection` | string | `bottom_center` | Placement position for `manual_placement` type. Options: `upper_left`, `upper_right`, `bottom_left`, `bottom_right`, `right_center`, `left_center`, `upper_center`, `bottom_center`, `center_vertical`, `center_horizontal` |
| `num_results` | integer | `1` | Number of lifestyle product shots to generate |
| `optimize_description` | boolean | `true` | Whether to optimize the scene description |
| `original_quality` | boolean | `false` | When `placement_type=original`, if true the output matches original quality |
| `padding_values` | string | (empty) | Desired padding in pixels around the product for `manual_padding` |
| `placement_type` | string | `manual_placement` | Product positioning. Options: `original`, `automatic`, `manual_placement`, `manual_padding` |
| `ref_image_url` | string | (empty) | URL of a reference image for the new scene or background |
| `scene_description` | string | (empty) | Text description of the new scene or background |
| `shot_size` | array | `[1000, 1000]` | Desired size of the final product shot in pixels |

## Output

- **Type:** image

## Examples

### Automatic Placement on Kitchen Counter
```json
{
  "model": "bria-product-shot",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/coffee-mug.png",
    "scene_description": "A cozy kitchen countertop with morning sunlight streaming through a window",
    "placement_type": "automatic",
    "num_results": 2,
    "shot_size": [1200, 800]
  }
}
```

### Manual Placement with Reference
```json
{
  "model": "bria-product-shot",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/perfume-bottle.png",
    "ref_image_url": "https://example.com/luxury-setting-reference.jpg",
    "scene_description": "Luxurious vanity table with soft bokeh lighting",
    "placement_type": "manual_placement",
    "manual_placement_selection": "center_horizontal",
    "num_results": 1
  }
}
```

## Related Models

- [Remove Background Enhance](../rembg-enhance/SKILL.md) - Remove backgrounds before product shot generation
- [Seedream V4 Edit](../seedream-v4-edit/SKILL.md) - General-purpose image editing
- [Flux Krea Image to Image](../flux-krea-image-to-image/SKILL.md) - Image transformation

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
