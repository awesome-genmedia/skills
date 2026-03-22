---
name: qwen-image-edit-2511-multiple-angles
description: "Qwen | Image Edit 2511 | Multiple Angles. Edit images with camera angle control using horizontal, vertical, and zoom adjustments. Triggers: camera angle, multiple angles, 3d rotation, image perspective, qwen edit"
allowed-tools: Bash(curl *), WebFetch
---

# Qwen | Image Edit 2511 | Multiple Angles

Edit images with precise camera angle control. Adjust horizontal rotation, vertical angle, and zoom level to view objects from different perspectives. Powered by Qwen with LoRA-based camera controls.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "qwen-image-edit-2511-multiple-angles",
    "version": "0.0.1",
    "input": {
      "image_urls": ["https://example.com/product-photo.jpg"],
      "horizontal_angle": 45,
      "vertical_angle": -15,
      "zoom": 5,
      "image_size": "square_hd",
      "num_inference_steps": 28,
      "output_format": "png"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | regular | Acceleration level for image generation. Options: `none`, `regular` |
| enable_safety_checker | boolean | true | Whether to enable the safety checker. |
| guidance_scale | number | 4.5 | The CFG (Classifier Free Guidance) scale. |
| horizontal_angle | number | 0 | Horizontal rotation angle around the object in degrees. 0=front view, 90=right side. |
| image_size | string | square_hd | The size of the generated image. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9` |
| image_urls | array | - | The URL of the image to adjust camera angle for. |
| lora_scale | number | 1 | The scale factor for the LoRA model. Controls the strength of the camera control. |
| negative_prompt | string | - | The negative prompt for the generation. |
| num_images | integer | 1 | Number of images to generate. |
| num_inference_steps | integer | 28 | The number of inference steps to perform. |
| output_format | string | png | The format of the output image. Options: `png`, `jpeg`, `webp` |
| seed | string | - | Random seed for reproducibility. |
| vertical_angle | number | 0 | Vertical camera angle in degrees. -30=low-angle shot (looking up), 0=eye-level. |
| zoom | number | 5 | Camera zoom/distance. 0=wide shot (far away), 5=medium shot (normal), 10=close-up. |

## Examples

**Rotate product view to the right:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "qwen-image-edit-2511-multiple-angles",
    "version": "0.0.1",
    "input": {
      "image_urls": ["https://example.com/sneaker.jpg"],
      "horizontal_angle": 90,
      "vertical_angle": 0,
      "zoom": 6
    }
  }'
```

**Low-angle dramatic shot:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "qwen-image-edit-2511-multiple-angles",
    "version": "0.0.1",
    "input": {
      "image_urls": ["https://example.com/building.jpg"],
      "horizontal_angle": 15,
      "vertical_angle": -30,
      "zoom": 3,
      "guidance_scale": 6,
      "lora_scale": 1.2,
      "negative_prompt": "blurry, distorted",
      "seed": "12345"
    }
  }'
```

**Close-up zoom:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "qwen-image-edit-2511-multiple-angles",
    "version": "0.0.1",
    "input": {
      "image_urls": ["https://example.com/figurine.jpg"],
      "horizontal_angle": 0,
      "vertical_angle": 10,
      "zoom": 9,
      "num_images": 2,
      "output_format": "jpeg"
    }
  }'
```

## Related Models

- [Qwen | Image Edit Plus](../qwen-image-edit-plus/) - General Qwen image editing
- [Qwen | AI Image Edit](../qwen-ai-image-edit/) - Standard Qwen image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
