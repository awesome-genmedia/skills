---
name: "Hunyuan 3D V2"
description: "Generate 3D models from images using Hunyuan 3D V2. Trigger: Use when the user wants to create a 3D model, or requests 'hunyuan 3d v2', '3d model from image', or 'generate 3d mesh'."
allowed-tools: ["Bash"]
---

# Hunyuan 3D V2

Generate 3D models from images using Hunyuan 3D V2. Create mesh objects with optional textures from a single input image.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "hunyuan-3d-v2",
    "version": "0.0.1",
    "input": {
      "input_image_url": "https://example.com/object.jpg",
      "guidance_scale": 7.5,
      "num_inference_steps": 50,
      "octree_resolution": 256,
      "textured_mesh": false
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `guidance_scale` | number | `7.5` | Guidance scale for the model |
| `input_image_url` | string | `false` | URL of image to generate the 3D model from |
| `num_inference_steps` | integer | `50` | Number of inference steps to perform |
| `octree_resolution` | integer | `256` | Octree resolution for the model |
| `seed` | integer | `false` | Random seed for reproducible generation |
| `textured_mesh` | boolean | `false` | If true, generate textured mesh (costs 3x more) |

## Output

- **Type:** object

## Examples

### Simple 3D Object
```json
{
  "model": "hunyuan-3d-v2",
  "version": "0.0.1",
  "input": {
    "input_image_url": "https://example.com/toy-car.jpg",
    "guidance_scale": 7.5,
    "num_inference_steps": 50,
    "octree_resolution": 256
  }
}
```

### High-Quality Textured Model
```json
{
  "model": "hunyuan-3d-v2",
  "version": "0.0.1",
  "input": {
    "input_image_url": "https://example.com/vase.jpg",
    "guidance_scale": 8.5,
    "num_inference_steps": 60,
    "octree_resolution": 256,
    "textured_mesh": true,
    "seed": 99
  }
}
```

## Related Models

- [Hunyuan 3D V2.1](../hunyuan-3d-v2-1/SKILL.md) - Newer version with improvements
- [Remove Background Enhance](../rembg-enhance/SKILL.md) - Clean up input images before 3D generation

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
