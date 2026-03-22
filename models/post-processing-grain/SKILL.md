---
name: "Post Processing Grain"
description: "Add film grain effects to images. Trigger: Use when the user wants to add grain or film texture, or requests 'film grain', 'add grain', 'post processing grain', or 'analog film look'."
allowed-tools: ["Bash"]
---

# Post Proccessing | Grain

Add realistic film grain to images. Choose from multiple grain styles including modern, analog, Kodak, Fuji, cinematic, and newspaper.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "post-processing-grain",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/photo.jpg",
      "grain_style": "kodak",
      "grain_intensity": 0.4,
      "grain_scale": 10
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `grain_intensity` | number | `0.4` | Film grain intensity |
| `grain_scale` | number | `10` | Film grain scale |
| `grain_style` | string | `modern` | Grain style. Options: `modern`, `analog`, `kodak`, `fuji`, `cinematic`, `newspaper` |
| `image_url` | string | (empty) | URL of image to process |

## Output

- **Type:** image

## Examples

### Kodak Film Look
```json
{
  "model": "post-processing-grain",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/portrait.jpg",
    "grain_style": "kodak",
    "grain_intensity": 0.5,
    "grain_scale": 8
  }
}
```

### Cinematic Grain
```json
{
  "model": "post-processing-grain",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/scene.jpg",
    "grain_style": "cinematic",
    "grain_intensity": 0.3,
    "grain_scale": 12
  }
}
```

## Related Models

- [Post Processing Combine](../post-processing/SKILL.md) - Apply multiple effects at once
- [Post Processing Vignette](../post-processing-vignette/SKILL.md) - Add vignette effect
- [Post Processing Color Tint](../post-processing-color-tint/SKILL.md) - Apply color tints

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
