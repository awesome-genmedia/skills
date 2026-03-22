---
name: ai-image-editor
description: "Edit images with natural language instructions using each::sense AI. Change objects, swap backgrounds, adjust colors, add or remove elements, apply style transfers, and retouch photos without manual tools. Supports both targeted edits and full-image transformations. Use for: photo retouching, object removal, background swapping, color grading, style transfer, image correction, creative edits. Triggers: ai image editor, edit image, photo editor, change image, modify image, image editing, remove object, swap background, retouch photo, ai edit, image manipulation, photo editing"
allowed-tools: Bash(curl *), WebFetch
---

# AI Image Editor

Edit images using natural language instructions using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Change the sky to a dramatic sunset with orange and purple clouds. Keep everything else the same."
      }
    ],
    "image_urls": ["https://example.com/landscape-photo.jpg"],
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
        "content": "Change the sky to a dramatic sunset with orange and purple clouds. Keep everything else the same."
    }],
    extra_body={
        "image_urls": ["https://example.com/landscape-photo.jpg"]
    }
)

print(response.choices[0].message.content)
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Edit Types

| Edit Type | Example Instruction | Use Case |
|-----------|-------------------|----------|
| **Object Removal** | "Remove the person standing on the left" | Clean up photos |
| **Object Addition** | "Add a red sports car parked on the street" | Compositing |
| **Background Swap** | "Replace the background with a tropical beach" | Product, portrait edits |
| **Color Change** | "Change the dress from blue to red" | Fashion, product variants |
| **Style Transfer** | "Make this photo look like a watercolor painting" | Artistic effects |
| **Weather Change** | "Add snow falling and frost on the ground" | Seasonal edits |
| **Time of Day** | "Change the scene from daytime to night" | Lighting changes |
| **Text Addition** | "Add a neon sign that says OPEN on the wall" | Signage, mockups |

## Examples

### Object Removal

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Remove the trash can from the right side of the image and fill the area naturally with the surrounding pavement and grass"
      }
    ],
    "image_urls": ["https://example.com/park-photo.jpg"],
    "stream": false
  }'
```

### Product Color Variant

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Change the sneaker color from white to forest green. Keep the sole white. Maintain the same material texture and lighting."
      }
    ],
    "image_urls": ["https://example.com/white-sneaker.jpg"],
    "stream": false
  }'
```

### Style Transfer

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Transform this city street photo into a Studio Ghibli anime style illustration. Keep the same composition and elements, but render everything in the warm, hand-painted anime aesthetic"
      }
    ],
    "image_urls": ["https://example.com/tokyo-street.jpg"],
    "stream": false
  }'
```

### Seasonal Change

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Transform this summer garden photo to autumn. Change the green leaves to red, orange, and gold. Add fallen leaves on the ground. Keep the same composition and structures."
      }
    ],
    "image_urls": ["https://example.com/summer-garden.jpg"],
    "stream": false
  }'
```

## Prompt Tips for Better Edits

- **Be specific** about what to change and what to preserve: "Change X but keep Y the same"
- **Reference locations** in the image: "the object on the left," "the background," "the foreground"
- **Describe the desired result**, not the process: "Make the sky blue" not "Use the color picker to select blue"
- **One edit at a time** produces better results than requesting multiple changes in one prompt
- **Mention lighting consistency**: "Match the lighting of the new element to the existing scene"

## Multi-Step Editing Workflow

```bash
# Step 1: Remove unwanted object
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Remove the power lines from this landscape photo"
      }
    ],
    "image_urls": ["https://example.com/original.jpg"],
    "stream": false
  }'

# Step 2: Use the result URL from step 1 for the next edit
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Enhance the colors, boost saturation slightly, and add a warm golden hour glow"
      }
    ],
    "image_urls": ["<URL_FROM_STEP_1>"],
    "stream": false
  }'
```

## Related Skills

- [Background Removal](../background-removal/SKILL.md) — Remove or replace backgrounds
- [Inpainting & Outpainting](../inpainting-outpainting/SKILL.md) — Fill or extend image areas
- [AI Photo Enhancer](../ai-photo-enhancer/SKILL.md) — Improve overall photo quality
- [Image to Image](../image-to-image/SKILL.md) — Full image transformation

## Related Models

- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for image editing tasks
- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
