---
name: "Post Processing Combine"
description: "Apply multiple post-processing effects to an image in one call. Trigger: Use when the user wants to apply combined effects, or requests 'post processing combine', 'multiple effects', 'apply all effects', or 'combined image processing'."
allowed-tools: ["Bash"]
---

# Post Proccessing | Combine

Apply multiple post-processing effects to an image in a single request. Enable individual effects and configure each one independently. Supports blur, chromatic aberration, color correction, desaturation, dissolve, dodge/burn, glow, grain, parabolize, sharpen, solarize, tint, and vignette.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "post-processing",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/photo.jpg",
      "enable_grain": true,
      "grain_style": "kodak",
      "grain_intensity": 0.3,
      "enable_vignette": true,
      "vignette_strength": 0.4,
      "enable_color_correction": true,
      "contrast": 0.1,
      "saturation": 0.05
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `blue_direction` | string | `horizontal` | Blue channel shift direction. Options: `horizontal`, `vertical` |
| `blue_shift` | integer | `0` | Blue channel shift amount |
| `blur_radius` | integer | `3` | Blur radius |
| `blur_sigma` | number | `1` | Sigma for Gaussian blur |
| `blur_type` | string | `gaussian` | Blur type. Options: `gaussian`, `kuwahara` |
| `brightness` | number | `0` | Brightness adjustment |
| `cas_amount` | number | `0.8` | CAS sharpening amount |
| `contrast` | number | `0` | Contrast adjustment |
| `desaturate_factor` | number | `1` | Desaturation factor |
| `desaturate_method` | string | `luminance (Rec.709)` | Desaturation method. Options: `luminance (Rec.709)`, `luminance (Rec.601)`, `average`, `lightness` |
| `dissolve_factor` | number | `0.5` | Dissolve blend factor |
| `dissolve_image_url` | string | (empty) | URL of second image for dissolve |
| `dodge_burn_intensity` | number | `0.5` | Dodge and burn intensity |
| `dodge_burn_mode` | string | `dodge` | Dodge/burn mode. Options: `dodge`, `burn`, `dodge_and_burn`, `burn_and_dodge`, `color_dodge`, `color_burn`, `linear_dodge`, `linear_burn` |
| `enable_blur` | boolean | `false` | Enable blur effect |
| `enable_chromatic` | boolean | `false` | Enable chromatic aberration |
| `enable_color_correction` | boolean | `false` | Enable color correction |
| `enable_desaturate` | boolean | `false` | Enable desaturation effect |
| `enable_dissolve` | boolean | `false` | Enable dissolve effect |
| `enable_dodge_burn` | boolean | `false` | Enable dodge and burn effect |
| `enable_glow` | boolean | `false` | Enable glow effect |
| `enable_grain` | boolean | `false` | Enable film grain effect |
| `enable_parabolize` | boolean | `false` | Enable parabolize effect |
| `enable_sharpen` | boolean | `false` | Enable sharpen effect |
| `enable_solarize` | boolean | `false` | Enable solarize effect |
| `enable_tint` | boolean | `false` | Enable color tint effect |
| `enable_vignette` | boolean | `false` | Enable vignette effect |
| `gamma` | number | `1` | Gamma adjustment |
| `glow_intensity` | number | `1` | Glow intensity |
| `glow_radius` | integer | `5` | Glow blur radius |
| `grain_intensity` | number | `0.4` | Film grain intensity |
| `grain_scale` | number | `10` | Film grain scale |
| `grain_style` | string | `modern` | Grain style. Options: `modern`, `analog`, `kodak`, `fuji`, `cinematic`, `newspaper` |
| `green_direction` | string | `horizontal` | Green channel shift direction. Options: `horizontal`, `vertical` |
| `green_shift` | integer | `0` | Green channel shift amount |
| `image_url` | string | (empty) | URL of image to process |
| `noise_radius` | integer | `7` | Noise radius for smart sharpen |
| `parabolize_coeff` | number | `1` | Parabolize coefficient |
| `preserve_edges` | number | `0.75` | Edge preservation factor |
| `red_direction` | string | `horizontal` | Red channel shift direction. Options: `horizontal`, `vertical` |
| `red_shift` | integer | `0` | Red channel shift amount |
| `saturation` | number | `0` | Saturation adjustment |
| `sharpen_alpha` | number | `1` | Sharpen strength (basic mode) |
| `sharpen_mode` | string | `basic` | Sharpening type. Options: `basic`, `smart`, `cas` |
| `sharpen_radius` | integer | `1` | Sharpen radius (basic mode) |
| `smart_sharpen_ratio` | number | `0.5` | Smart sharpen blend ratio |
| `smart_sharpen_strength` | number | `5` | Smart sharpen strength |
| `solarize_threshold` | number | `0.5` | Solarize threshold |
| `temperature` | number | `0` | Color temperature adjustment |
| `tint_mode` | string | `sepia` | Tint color. Options: `sepia`, `red`, `green`, `blue`, `cyan`, `magenta`, `yellow`, `purple`, `orange`, `warm`, `cool`, `lime`, `navy`, `vintage`, `rose`, `teal`, `maroon`, `peach`, `lavender`, `olive` |
| `tint_strength` | number | `1` | Tint strength |
| `vertex_x` | number | `0.5` | Vertex X position |
| `vertex_y` | number | `0.5` | Vertex Y position |
| `vignette_strength` | number | `0.5` | Vignette strength |

## Output

- **Type:** image

## Examples

### Vintage Film Look
```json
{
  "model": "post-processing",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/street-photo.jpg",
    "enable_grain": true,
    "grain_style": "kodak",
    "grain_intensity": 0.4,
    "enable_vignette": true,
    "vignette_strength": 0.5,
    "enable_tint": true,
    "tint_mode": "vintage",
    "tint_strength": 0.6,
    "enable_color_correction": true,
    "contrast": 0.15,
    "saturation": -0.1
  }
}
```

### Cinematic Grade
```json
{
  "model": "post-processing",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/scene.jpg",
    "enable_color_correction": true,
    "contrast": 0.2,
    "temperature": -0.1,
    "gamma": 0.95,
    "enable_sharpen": true,
    "sharpen_mode": "cas",
    "cas_amount": 0.7,
    "enable_glow": true,
    "glow_intensity": 0.3,
    "glow_radius": 8
  }
}
```

## Related Models

- [Post Processing Vignette](../post-processing-vignette/SKILL.md) - Vignette only
- [Post Processing Grain](../post-processing-grain/SKILL.md) - Grain only
- [Post Processing Color Correction](../post-processing-color-correction/SKILL.md) - Color correction only

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
