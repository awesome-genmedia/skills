---
name: "Flux Lora Portrait Trainer"
description: "Train a custom LoRA model from portrait images. Trigger: Use when the user wants to train a custom LoRA, or requests 'train lora', 'flux portrait trainer', 'custom lora training', or 'train model on my photos'."
allowed-tools: ["Bash"]
---

# Flux Lora | Portrait Trainer

Train a custom LoRA model from a set of portrait images. Upload a ZIP archive of images and configure training parameters to create a personalized LoRA weight file.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-lora-portrait-trainer",
    "version": "0.0.1",
    "input": {
      "images_data_url": "https://example.com/portrait-images.zip",
      "trigger_phrase": "photo of sks person",
      "steps": 1000,
      "learning_rate": 0.00009,
      "create_masks": true,
      "subject_crop": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `create_masks` | boolean | `false` | If True, masks will be created for the subject |
| `data_archive_format` | string | (empty) | The format of the archive. If not specified, inferred from the file |
| `images_data_url` | string | (empty) | ZIP archive URL containing at least 10 images of a subject |
| `learning_rate` | number | `0.00009` | Learning rate for training |
| `multiresolution_training` | boolean | `true` | If True, multiresolution training will be used |
| `resume_from_checkpoint` | string | (empty) | URL to a checkpoint to resume training from |
| `steps` | integer | `1000` | Number of training steps |
| `subject_crop` | boolean | `true` | If True, the subject will be cropped from the image |
| `trigger_phrase` | string | (empty) | Trigger phrase to use in captions. If None, no trigger word is used |

## Output

- **Type:** code

## Examples

### Basic Portrait LoRA Training
```json
{
  "model": "flux-lora-portrait-trainer",
  "version": "0.0.1",
  "input": {
    "images_data_url": "https://example.com/my-portraits.zip",
    "trigger_phrase": "photo of johndoe person",
    "steps": 1200,
    "learning_rate": 0.00009,
    "create_masks": true,
    "subject_crop": true,
    "multiresolution_training": true
  }
}
```

### Resume Training from Checkpoint
```json
{
  "model": "flux-lora-portrait-trainer",
  "version": "0.0.1",
  "input": {
    "images_data_url": "https://example.com/more-portraits.zip",
    "trigger_phrase": "photo of johndoe person",
    "steps": 500,
    "resume_from_checkpoint": "https://example.com/checkpoint-1000.safetensors"
  }
}
```

## Related Models

- [Juggernaut Flux Lora](../juggernaut-flux-lora/SKILL.md) - Use trained LoRA for image generation
- [Flux Kontext Lora Text to Image](../flux-kontext-lora-text-to-image/SKILL.md) - Text-to-image with LoRA
- [Flux Krea Lora Image to Image](../flux-krea-lora-image-to-image/SKILL.md) - Image-to-image with LoRA

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
