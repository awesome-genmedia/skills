---
name: image-upscaling
description: "Enhance image resolution with AI upscaling using each::sense AI. Upscale low-resolution images to high resolution while preserving detail, sharpness, and natural texture. Supports 2x and 4x scaling for photos, artwork, screenshots, and legacy media. Use for: photo enlargement, print preparation, low-res recovery, thumbnail upscaling, legacy photo restoration, digital art upscaling. Triggers: image upscaling, upscale image, enhance resolution, super resolution, enlarge image, increase resolution, ai upscale, image enhancer, 4k upscale, photo upscale, high resolution, sharpen image"
allowed-tools: Bash(curl *), WebFetch
---

# Image Upscaling

Enhance image resolution with AI-powered upscaling using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Using curl

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Upscale this image to 4x resolution. Enhance sharpness and detail while keeping the original look natural. Remove any compression artifacts."
      }
    ],
    "image_urls": ["https://example.com/low-res-photo.jpg"],
    "stream": false
  }'
```

### Using Python (OpenAI SDK)

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_EACHLABS_API_KEY",
    base_url="https://eachsense-agent.core.eachlabs.run/v1"
)

response = client.chat.completions.create(
    model="eachsense/beta",
    messages=[{
        "role": "user",
        "content": "Upscale this image to 4x resolution. Enhance sharpness and detail while keeping the original look natural. Remove any compression artifacts."
    }],
    extra_body={
        "image_urls": ["https://example.com/low-res-photo.jpg"]
    }
)

print(response.choices[0].message.content)
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Upscaling Scenarios

| Scenario | Prompt Focus | Expected Improvement |
|----------|-------------|---------------------|
| **Photo Enlargement** | Preserve natural skin texture, avoid over-sharpening | Print-ready from web-size |
| **Artwork Upscaling** | Maintain brush strokes, color fidelity | Gallery print from digital |
| **Screenshot Enhancement** | Clean edges, readable text, sharp UI elements | Presentation-ready captures |
| **Legacy Photo Recovery** | Reduce grain, restore detail, fix color | Modern quality from old scans |
| **Thumbnail Expansion** | Reconstruct facial features, add detail | Usable image from tiny source |

## Examples

### Photo for Print

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Upscale this photograph for large-format printing. Increase resolution while preserving natural skin textures, fine hair detail, and fabric weave. Do not over-sharpen or add artificial detail."
      }
    ],
    "image_urls": ["https://example.com/portrait-web.jpg"],
    "stream": false
  }'
```

### Digital Art Upscaling

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Upscale this digital illustration to high resolution. Preserve the clean line art, flat color areas, and intentional brush strokes. Keep the artistic style intact without adding photorealistic detail."
      }
    ],
    "image_urls": ["https://example.com/illustration-small.png"],
    "stream": false
  }'
```

### Old Photo Restoration + Upscale

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Upscale and restore this old scanned photograph. Remove film grain and scanning artifacts. Enhance facial details and sharpness. Correct faded colors to look natural. Output at 4x the original resolution."
      }
    ],
    "image_urls": ["https://example.com/old-family-photo-scan.jpg"],
    "stream": false
  }'
```

## Prompt Tips

- **Specify the goal**: "for printing," "for web," or "for a presentation" helps the model optimize
- **Mention artifact handling**: "Remove JPEG compression artifacts" for heavily compressed sources
- **Preserve style intent**: For artwork, say "Keep the artistic style" to prevent unwanted photorealism
- **Control sharpening**: "Do not over-sharpen" prevents artificial haloing effects
- **Face priority**: "Focus on facial detail" when portraits are the main subject

## Resolution Guide

| Source Size | 2x Upscale | 4x Upscale | Best For |
|-------------|-----------|-----------|----------|
| 256x256 | 512x512 | 1024x1024 | Thumbnails, icons |
| 512x512 | 1024x1024 | 2048x2048 | Social media |
| 1024x1024 | 2048x2048 | 4096x4096 | Web, presentations |
| 1920x1080 | 3840x2160 | 7680x4320 | 4K/8K display |

## Related Skills

- [AI Photo Enhancer](../ai-photo-enhancer/SKILL.md) — Improve quality beyond resolution
- [AI Image Editor](../ai-image-editor/SKILL.md) — Edit images with natural language
- [Text to Image](../text-to-image/SKILL.md) — Generate new high-resolution images

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for reference-based tasks

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
