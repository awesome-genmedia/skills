---
name: "Gemini 2.0 Flash Lite"
description: "Multimodal AI analysis using Gemini 2.0 Flash Lite. Trigger: Use when the user wants to analyze images with text, or requests 'gemini flash lite', 'analyze image with gemini', 'gemini multimodal', or 'describe image contents'."
allowed-tools: ["Bash"]
---

# Gemini | 2.0 | Flash Lite

Use Google's Gemini 2.0 Flash Lite for multimodal analysis. Process text prompts with optional image inputs for vision-language tasks.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gemini-2-0-flash-lite",
    "version": "0.0.1",
    "input": {
      "prompt": "Describe what you see in this image in detail",
      "image_urls": ["https://example.com/photo.jpg"]
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `image_urls` | array | `false` | URLs of images to analyze |
| `prompt` | string | `false` | Text prompt or question |

## Output

- **Type:** text

## Examples

### Image Description
```json
{
  "model": "gemini-2-0-flash-lite",
  "version": "0.0.1",
  "input": {
    "prompt": "What objects are in this image and what is happening?",
    "image_urls": ["https://example.com/scene.jpg"]
  }
}
```

### Text-Only Query
```json
{
  "model": "gemini-2-0-flash-lite",
  "version": "0.0.1",
  "input": {
    "prompt": "Write a short creative story about a robot learning to paint"
  }
}
```

### Multi-Image Comparison
```json
{
  "model": "gemini-2-0-flash-lite",
  "version": "0.0.1",
  "input": {
    "prompt": "Compare these two images and describe the differences",
    "image_urls": ["https://example.com/image-a.jpg", "https://example.com/image-b.jpg"]
  }
}
```

## Related Models

- [Video Analyzer](../video-analyzer/SKILL.md) - Analyze video content
- [Imagen 4 Preview](../imagen4-preview/SKILL.md) - Generate images from text

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
