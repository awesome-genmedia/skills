---
name: "Post Processing Dodge Burn"
description: "Apply dodge and burn effects to images. Trigger: Use when the user wants to dodge or burn an image, or requests 'dodge and burn', 'lighten shadows', 'darken highlights', or 'post processing dodge burn'."
allowed-tools: ["Bash"]
---

# Post Proccessing | Dodge Burn

Apply dodge and burn effects to images for tonal adjustments. Choose from multiple modes including dodge, burn, and combination modes.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "post-processing-dodge-burn",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/photo.jpg",
      "dodge_burn_mode": "dodge_and_burn",
      "dodge_burn_intensity": 0.5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `dodge_burn_intensity` | number | `0.5` | Dodge and burn intensity |
| `dodge_burn_mode` | string | `dodge` | Mode. Options: `dodge`, `burn`, `dodge_and_burn`, `burn_and_dodge`, `linear_dodge`, `linear_burn` |
| `image_url` | string | (empty) | URL of image to process |

## Output

- **Type:** image

## Examples

### Dodge to Lighten Shadows
```json
{
  "model": "post-processing-dodge-burn",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/dark-photo.jpg",
    "dodge_burn_mode": "dodge",
    "dodge_burn_intensity": 0.6
  }
}
```

### Burn for Dramatic Darks
```json
{
  "model": "post-processing-dodge-burn",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/landscape.jpg",
    "dodge_burn_mode": "burn",
    "dodge_burn_intensity": 0.4
  }
}
```

## Related Models

- [Post Processing Combine](../post-processing/SKILL.md) - Apply multiple effects at once
- [Post Processing Color Correction](../post-processing-color-correction/SKILL.md) - Brightness and contrast adjustments
- [Post Processing Parabolize](../post-processing-parabolize/SKILL.md) - Parabolic tonal curves

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
