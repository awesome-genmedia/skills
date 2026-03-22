---
name: image-to-image
description: "Transform images based on reference and prompt using each::sense AI. Apply style transfers, convert sketches to finished art, change artistic styles, blend multiple references, and reimagine existing images in new ways. Supports photo-to-illustration, sketch-to-render, and cross-style transformations. Use for: style transfer, sketch to art, photo to illustration, image remix, art conversion, visual transformation, concept variation. Triggers: image to image, style transfer, transform image, img2img, convert image, sketch to art, photo to illustration, reimagine image, image remix, artistic conversion, visual transformation"
allowed-tools: Bash(curl *), WebFetch
---

# Image to Image

Transform images based on reference and prompt using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": [
              {"type": "text", "text": "Transform this photograph into a Studio Ghibli anime illustration. Keep the same composition, subjects, and scene but render everything in the warm, hand-painted anime art style with soft colors and gentle lighting."},
              {"type": "image_url", "image_url": {"url": "https://example.com/original-photo.jpg"}}
            ]
          }
    ],
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
        "content": "Transform this photograph into a Studio Ghibli anime illustration. Keep the same composition, subjects, and scene but render everything in the warm, hand-painted anime art style with soft colors and gentle lighting."
    }],
    # Images are included in the message content array above
)

print(response.choices[0].message.content)
```

### With Multiple Reference Images

Blend a content image with a style reference:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Take the composition and subject from the first image and apply the artistic style from the second image. Combine them into a cohesive artwork."},
              {"type": "image_url", "image_url": {"url": "https://example.com/content-image.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/style-reference.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Transformation Types

| Transformation | Description | Example |
|---------------|-------------|---------|
| **Style Transfer** | Apply an artistic style to a photo | Photo to oil painting |
| **Sketch to Art** | Render a rough sketch into finished artwork | Pencil sketch to digital illustration |
| **Medium Swap** | Change the artistic medium | Watercolor to 3D render |
| **Era Shift** | Reimagine in a different time period | Modern city as medieval village |
| **Genre Change** | Change the visual genre | Landscape photo to sci-fi scene |
| **Mood Shift** | Change the emotional tone | Bright daytime to moody noir |

## Examples

### Photo to Oil Painting

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Transform this landscape photo into a classical oil painting in the style of the Hudson River School. Rich earth tones, visible impasto brushstrokes, dramatic chiaroscuro lighting, golden varnish warmth. Keep the composition but make it feel like a 19th-century masterpiece."},
              {"type": "image_url", "image_url": {"url": "https://example.com/valley-landscape.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Sketch to Finished Art

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Turn this rough pencil sketch into a polished digital illustration. Add full color, clean lines, proper shading, and a detailed background. Fantasy art style with vibrant colors and dramatic lighting."},
              {"type": "image_url", "image_url": {"url": "https://example.com/character-sketch.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Photo to Cyberpunk

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Reimagine this city street as a cyberpunk scene set in 2099. Add neon signs in Japanese and English, holographic advertisements, flying vehicles in the background, wet reflective streets, and a perpetual night sky with a pink-purple haze. Keep the same buildings and street layout."},
              {"type": "image_url", "image_url": {"url": "https://example.com/city-street.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Day to Night Transformation

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Transform this daytime photo to a nighttime scene. Add a starry sky, moonlight casting blue-silver shadows, warm light glowing from windows, and street lamps illuminating the path. Keep all the structures and composition identical."},
              {"type": "image_url", "image_url": {"url": "https://example.com/daytime-house.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

## Controlling Transformation Strength

The wording of your prompt controls how much the output differs from the input:

- **Light transformation**: "Keep everything the same, just change the color palette to warm autumn tones"
- **Medium transformation**: "Transform this into a watercolor painting while preserving the composition"
- **Heavy transformation**: "Reimagine this entire scene as an alien planet with bizarre flora and bioluminescent lighting"

## Prompt Structure

```
Transform/Convert/Reimagine this [source description] into [target style/scene].
[What to keep from the original].
[What to change or add].
[Style, mood, and quality keywords].
```

## Related Skills

- [AI Image Editor](../ai-image-editor/SKILL.md) — Targeted edits to images
- [Text to Image](../text-to-image/SKILL.md) — Generate from scratch
- [AI Photo Enhancer](../ai-photo-enhancer/SKILL.md) — Improve quality
- [AI Avatar Generator](../ai-avatar-generator/SKILL.md) — Photo to avatar conversion

## Related Models

- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for image-to-image tasks
- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative artistic styles

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
