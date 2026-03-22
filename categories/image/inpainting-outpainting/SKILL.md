---
name: inpainting-outpainting
description: "Fill masked areas or extend image boundaries using each::sense AI. Inpaint to remove objects and fill seamlessly, outpaint to expand canvas and generate new content beyond the original frame. Supports context-aware fills, creative extensions, and object replacement. Use for: object removal, canvas extension, image repair, panorama creation, aspect ratio changes, creative compositing. Triggers: inpainting, outpainting, fill area, extend image, expand canvas, remove object, image fill, generative fill, uncrop, extend canvas, mask fill, content aware fill"
allowed-tools: Bash(curl *), WebFetch
---

# Inpainting & Outpainting

Fill masked areas or extend image boundaries using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Using curl — Inpainting (Fill/Replace)

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Remove the parked car in the center of this street photo and fill the area with the surrounding cobblestone road and a few fallen leaves to match the scene"},
              {"type": "image_url", "image_url": {"url": "https://example.com/street-with-car.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Using curl — Outpainting (Extend)

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Extend this landscape photo to the left and right to create a wider panoramic view. Continue the mountain range, sky, and meadow naturally."},
              {"type": "image_url", "image_url": {"url": "https://example.com/mountain-landscape.jpg"}}
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
        "content": "Extend this portrait photo downward to show the full outfit. Continue the style, fabric, and lighting naturally."
    }],
    # Images are included in the message content array above
)

print(response.choices[0].message.content)
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Inpainting Use Cases

| Task | Prompt Approach |
|------|----------------|
| **Object Removal** | "Remove [object] and fill with surrounding [surface/texture]" |
| **Object Replacement** | "Replace [object] with [new object], matching lighting and scale" |
| **Blemish Repair** | "Fix the scratches/damage and restore the original look" |
| **Watermark Removal** | "Remove the watermark and reconstruct the image behind it" |
| **Person Removal** | "Remove the person on the right, fill with the beach/park behind" |

## Outpainting Use Cases

| Task | Prompt Approach |
|------|----------------|
| **Widen Landscape** | "Extend left and right, continue the natural scene" |
| **Uncrop Portrait** | "Extend downward to show full body" |
| **Aspect Ratio Fix** | "Extend to 16:9 aspect ratio, fill new areas naturally" |
| **Environment Build** | "Extend upward to show more sky and clouds" |
| **Panorama Creation** | "Extend both sides to create a wide panoramic view" |

## Examples

### Replace Object In Scene

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Replace the empty vase on the table with a lush bouquet of sunflowers. Match the lighting and shadows of the surrounding scene."},
              {"type": "image_url", "image_url": {"url": "https://example.com/table-scene.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Extend for Social Media Ratio

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "This image is square (1:1). Extend it to a 16:9 landscape ratio by adding content to the left and right sides. Continue the environment seamlessly."},
              {"type": "image_url", "image_url": {"url": "https://example.com/square-photo.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Restore Damaged Photo

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "This old photo has tears and creases across the middle. Repair the damaged areas, reconstruct missing details, and make the photo look intact and natural."},
              {"type": "image_url", "image_url": {"url": "https://example.com/torn-old-photo.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

## Tips for Quality Results

- **Describe the fill content**: Do not just say "fill it in" — describe what should appear: "fill with grass and wildflowers"
- **Reference surroundings**: "Match the surrounding texture, lighting, and perspective"
- **Keep it contextual**: The AI uses the rest of the image as context, so more visible context means better fills
- **One area at a time**: Filling multiple disconnected regions in one pass can reduce quality
- **Outpainting direction**: Be explicit — "extend to the left" vs. "extend in all directions"

## Related Skills

- [AI Image Editor](../ai-image-editor/SKILL.md) — General image editing
- [Background Removal](../background-removal/SKILL.md) — Remove backgrounds
- [Image Upscaling](../image-upscaling/SKILL.md) — Enhance resolution
- [AI Photo Enhancer](../ai-photo-enhancer/SKILL.md) — Improve overall quality

## Related Models

- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for image editing tasks
- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
