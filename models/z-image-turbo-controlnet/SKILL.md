---
name: z-image-turbo-controlnet
description: "Z Image | Turbo | Controlnet. Generate images using ControlNet conditioning with turbo speed. Triggers: controlnet, image generation, turbo, guided generation, canny, depth, pose"
allowed-tools: Bash(curl *), WebFetch
---

# Z Image | Turbo | Controlnet

Generate images guided by ControlNet conditioning using turbo-speed inference. Supports canny edge, depth, and pose preprocessing modes with configurable control strength and timing.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-controlnet",
    "version": "0.0.1",
    "input": {
      "prompt": "a futuristic cityscape at sunset, cyberpunk style",
      "image_url": "https://example.com/reference.jpg",
      "preprocess": "canny",
      "control_scale": 0.9,
      "image_size": "landscape_16_9",
      "num_inference_steps": 8
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | none | The acceleration level to use. enum: none, regular, high |
| control_end | number | 0.4 | The end of the controlnet conditioning. |
| control_scale | number | 0.9 | The scale of the controlnet conditioning. |
| control_start | number | 0 | The start of the controlnet conditioning. |
| enable_prompt_expansion | boolean | false | Whether to enable prompt expansion. Increases price by 0.0025. |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled. |
| image_size | string | auto | The size of the generated image. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9, auto |
| image_url | string | | URL of Image for ControlNet generation. |
| num_images | integer | 1 | The number of images to generate. |
| num_inference_steps | integer | 8 | The number of inference steps to perform. |
| output_format | string | png | The format of the generated image. enum: jpeg, png, webp |
| preprocess | string | none | What kind of preprocessing to apply to the image. enum: none, canny, depth, pose |
| prompt | string | | The prompt to generate an image from. |
| seed | integer | | The same seed and prompt produce the same output. |

## Examples

**Canny edge-guided generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-controlnet",
    "version": "0.0.1",
    "input": {
      "prompt": "elegant watercolor painting of a garden",
      "image_url": "https://example.com/garden-photo.jpg",
      "preprocess": "canny",
      "control_scale": 0.8,
      "control_start": 0,
      "control_end": 0.5,
      "image_size": "square_hd",
      "output_format": "png"
    }
  }'
```

**Depth-guided generation with acceleration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-controlnet",
    "version": "0.0.1",
    "input": {
      "prompt": "a snowy mountain village, highly detailed",
      "image_url": "https://example.com/village.jpg",
      "preprocess": "depth",
      "acceleration": "high",
      "control_scale": 0.7,
      "num_images": 2,
      "image_size": "landscape_4_3"
    }
  }'
```

**Pose-guided generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-controlnet",
    "version": "0.0.1",
    "input": {
      "prompt": "professional dancer in a flowing red dress, studio lighting",
      "image_url": "https://example.com/pose-reference.jpg",
      "preprocess": "pose",
      "control_scale": 0.9,
      "image_size": "portrait_4_3",
      "seed": 42
    }
  }'
```

## Related Models

- [Z Image | Turbo | Text to Image](../z-image-turbo-text-to-image/) - Text-only image generation without ControlNet
- [Z Image | Turbo | Image to Image](../z-image-turbo-image-to-image/) - Image-to-image transformation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
