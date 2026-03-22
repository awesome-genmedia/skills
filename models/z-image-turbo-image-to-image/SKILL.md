---
name: z-image-turbo-image-to-image
description: "Z Image | Turbo | Image to Image. Transform existing images using text prompts with turbo speed. Triggers: image to image, img2img, transformation, turbo, style transfer"
allowed-tools: Bash(curl *), WebFetch
---

# Z Image | Turbo | Image to Image

Transform existing images using text prompts with turbo-speed inference. Control the transformation strength to balance between the original image and the new generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-image-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "transform into an oil painting style, vibrant colors",
      "image_url": "https://example.com/photo.jpg",
      "strength": 0.6,
      "image_size": "landscape_4_3"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | none | The acceleration level to use. enum: none, regular, high |
| enable_prompt_expansion | boolean | false | Whether to enable prompt expansion. Increases price by 0.0025. |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled. |
| image_size | string | auto | The size of the generated image. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9, auto |
| image_url | string | | URL of Image for Image-to-Image generation. |
| num_images | integer | 1 | The number of images to generate. |
| num_inference_steps | integer | 8 | The number of inference steps to perform. |
| output_format | string | png | The format of the generated image. enum: jpeg, png, webp |
| prompt | string | | The prompt to generate an image from. |
| seed | integer | | The same seed and prompt produce the same output. |
| strength | number | 0.6 | The strength of the image-to-image conditioning. |

## Examples

**Style transfer with moderate strength:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-image-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "anime style illustration, soft pastel colors",
      "image_url": "https://example.com/portrait.jpg",
      "strength": 0.5,
      "image_size": "portrait_4_3",
      "output_format": "png"
    }
  }'
```

**High-strength transformation with acceleration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-image-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "futuristic cyberpunk city at night, neon lights",
      "image_url": "https://example.com/cityscape.jpg",
      "strength": 0.8,
      "acceleration": "high",
      "num_images": 2,
      "image_size": "landscape_16_9"
    }
  }'
```

**Subtle enhancement with low strength:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-image-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "enhance lighting, add dramatic shadows",
      "image_url": "https://example.com/landscape.jpg",
      "strength": 0.3,
      "seed": 12345
    }
  }'
```

## Related Models

- [Z Image | Turbo | Text to Image](../z-image-turbo-text-to-image/) - Generate images from text prompts only
- [Z Image | Turbo | Controlnet](../z-image-turbo-controlnet/) - ControlNet-guided image generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
