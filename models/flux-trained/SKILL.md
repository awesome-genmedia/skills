---
name: flux-trained
description: "Flux Img-to-Img | Face-Guided Image Generation. Generate images guided by a face/ID image with Flux. Triggers: flux img2img, face generation, id image, flux trained, face guided generation"
allowed-tools: Bash(curl *), WebFetch
---

# Flux Img-to-Img

Generate images guided by a face/ID image using Flux. Upload an ID image and provide a text prompt to generate portraits and images with identity preservation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-trained",
    "version": "0.0.1",
    "input": {
      "prompt": "portrait, color, cinematic",
      "main_face_image": "https://example.com/face-photo.jpg",
      "width": 896,
      "height": 1152,
      "num_steps": 20,
      "guidance_scale": 4
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| guidance_scale | number | 4 | Guidance scale for text prompt influence (1.0-10.0) |
| height | integer | 1152 | Height of generated image (256-1536 pixels) |
| id_weight | number | 1 | Weight of the ID image influence (0.0-3.0) |
| main_face_image | string | - | Upload an ID image for face generation |
| max_sequence_length | integer | 128 | Max sequence length for prompt (T5), smaller is faster (128-512) |
| negative_prompt | string | bad quality, worst quality, text, signature... | Negative prompt |
| num_outputs | integer | 1 | Number of images to generate (1-4) |
| num_steps | integer | 20 | Number of denoising steps (1-20) |
| output_format | string | webp | Output format. enum: png, webp |
| output_quality | integer | 80 | Quality of output image (1-100) |
| prompt | string | portrait, color, cinematic | Text prompt to guide generation |
| seed | integer | - | Random seed (leave blank or -1 for random) |
| start_step | integer | 1 | Timestep to start inserting ID (0-4 recommended, 0 for highest fidelity) |
| true_cfg | number | 1 | Classifier-Free Guidance scale. 1.0 uses standard CFG |
| width | integer | 896 | Width of generated image (256-1536 pixels) |

## Examples

**Cinematic portrait with high fidelity:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-trained",
    "version": "0.0.1",
    "input": {
      "prompt": "cinematic portrait, dramatic lighting, shallow depth of field, professional photography",
      "main_face_image": "https://example.com/headshot.jpg",
      "width": 896,
      "height": 1152,
      "id_weight": 1.5,
      "start_step": 0,
      "num_steps": 20,
      "guidance_scale": 5,
      "output_format": "png"
    }
  }'
```

**Multiple variations:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-trained",
    "version": "0.0.1",
    "input": {
      "prompt": "a person in a futuristic sci-fi setting, holographic displays, neon lighting",
      "main_face_image": "https://example.com/face.jpg",
      "num_outputs": 3,
      "width": 1024,
      "height": 1024,
      "id_weight": 1,
      "guidance_scale": 4,
      "seed": 42
    }
  }'
```

## Related Models

- [photomaker](../photomaker/) - Photo generation with identity preservation
- [instant-id](../instant-id/) - Instant ID avatar generation
- [flux-dev](../flux-dev/) - Standard Flux text-to-image

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
