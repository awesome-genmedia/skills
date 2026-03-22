---
name: ccsr
description: "CCSR Upscaler. Upscale and enhance images using the CCSR model with advanced tiling and color correction. Triggers: ccsr upscaler, image upscale, super resolution, enhance image, upscale image, image enhancement, ccsr"
allowed-tools: Bash(curl *), WebFetch
---

# CCSR Upscaler

Upscale and enhance images using the CCSR (Content Consistent Super-Resolution) model. Supports configurable scale factors, color correction methods, tile-based processing for large images, and fine-grained control over the diffusion process.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ccsr",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/low-res-photo.jpg",
      "scale": 2,
      "steps": 50
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| color_fix_type | string | adain | Color correction method. Options: `none`, `wavelet`, `adain` |
| image_url | string | - | URL of the image to upscale |
| scale | number | 2 | Upscale factor |
| seed | integer | - | Random seed for reproducible results |
| steps | integer | 50 | Number of inference steps. Higher values produce better quality but take longer |
| t_max | number | 0.6667 | Maximum timestep for the diffusion process |
| t_min | number | 0.3333 | Minimum timestep for the diffusion process |
| tile_diffusion | string | none | Tile diffusion mode. Options: `none`, `mix`, `gaussian` |
| tile_diffusion_size | integer | 1024 | Size of tiles for tile diffusion |
| tile_diffusion_stride | integer | - | Stride for tile diffusion |
| tile_vae | boolean | false | Enable tile-based VAE processing for large images |
| tile_vae_decoder_size | integer | 226 | Size of tiles for VAE decoder |
| tile_vae_encoder_size | integer | 1024 | Size of tiles for VAE encoder |

## Examples

**Basic 2x upscale:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ccsr",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/small-portrait.jpg",
      "scale": 2,
      "steps": 50,
      "color_fix_type": "adain"
    }
  }'
```

**High-quality upscale with tiling for large images:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ccsr",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/landscape.jpg",
      "scale": 4,
      "steps": 60,
      "tile_diffusion": "gaussian",
      "tile_diffusion_size": 1024,
      "tile_vae": true,
      "color_fix_type": "wavelet"
    }
  }'
```

## Related Models

- [Eachlabs Image Upscaler | Pro | v1](../eachlabs-image-upscaler-pro-v1/) - Simple one-click upscaling
- [Qwen Image](../qwen-image/) - AI image generation
- [Cartoonify V2](../cartoonify-v2/) - Convert images to cartoon style

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
