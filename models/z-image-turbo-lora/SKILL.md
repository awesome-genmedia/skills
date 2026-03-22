---
name: z-image-turbo-lora
description: "Z Image | Turbo | Lora. Generate images with LoRA weights using the Z Image Turbo model. Triggers: text to image, lora, custom style, z image, ai art"
allowed-tools: Bash(curl *), WebFetch
---

# Z Image | Turbo | Lora

Generate images from text prompts using the Z Image Turbo model with LoRA weight support. Apply custom LoRA models for specific styles, characters, or concepts with configurable acceleration and prompt expansion.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "A fantasy warrior in ornate armor standing on a cliff edge, dramatic lighting",
      "loras": [{"path": "https://example.com/fantasy-style-lora.safetensors", "scale": 0.8}],
      "image_size": "landscape_4_3",
      "num_inference_steps": 8,
      "output_format": "png"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | none | The acceleration level to use. Options: `none`, `regular`, `high` |
| enable_prompt_expansion | boolean | false | Whether to enable prompt expansion. |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled. |
| image_size | string | landscape_4_3 | The size of the generated image. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9` |
| loras | array | - | List of LoRA weights to apply. |
| num_images | integer | 1 | The number of images to generate. |
| num_inference_steps | integer | 8 | The number of inference steps to perform. |
| output_format | string | png | The format of the generated image. Options: `jpeg`, `png`, `webp` |
| prompt | string | - | The prompt to generate an image from. |
| seed | integer | - | The same seed and prompt given to the same model version will output the same image. |

## Examples

**Basic LoRA generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "A portrait in the style of <lora_trigger_word>, vibrant colors",
      "loras": [{"path": "https://example.com/art-style.safetensors", "scale": 1.0}]
    }
  }'
```

**Multiple LoRAs with acceleration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "z-image-turbo-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "A cyberpunk cityscape at night, neon reflections on wet streets",
      "loras": [
        {"path": "https://example.com/cyberpunk-lora.safetensors", "scale": 0.7},
        {"path": "https://example.com/neon-lights-lora.safetensors", "scale": 0.5}
      ],
      "acceleration": "high",
      "num_images": 2,
      "enable_prompt_expansion": true,
      "image_size": "landscape_16_9",
      "seed": 42
    }
  }'
```

## Related Models

- [Z Image | Turbo | Image to Image | Lora](../z-image-turbo-image-to-image-lora/) - Image-to-image with LoRA
- [Z Image | Turbo | Controlnet | Lora](../z-image-turbo-controlnet-lora/) - ControlNet with LoRA
- [Z Image | Turbo | Text to Image](../z-image-turbo-text-to-image/) - Standard text to image without LoRA

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
