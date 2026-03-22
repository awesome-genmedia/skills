---
name: background-removal
description: "Remove and replace image backgrounds using each::sense AI. Isolate subjects from photos, create transparent backgrounds, swap backgrounds for product photography, portraits, and marketing materials. Supports clean cutouts, background replacement, and environmental compositing. Use for: product photos, portrait backgrounds, e-commerce listings, social media, photo compositing, transparent PNGs. Triggers: remove background, background removal, background eraser, transparent background, cutout, background swap, replace background, isolate subject, bg remove, background changer, product background"
allowed-tools: Bash(curl *), WebFetch
---

# Background Removal

Remove and replace image backgrounds using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
              {"type": "text", "text": "Remove the background from this image and replace it with a clean white background"},
              {"type": "image_url", "image_url": {"url": "https://example.com/product-photo.jpg"}}
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
        "content": "Remove the background from this image and replace it with a clean white background"
    }],
    # Images are included in the message content array above
)

print(response.choices[0].message.content)
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Use Cases

| Use Case | Instruction | Result |
|----------|-------------|--------|
| **E-commerce** | "Remove background, replace with pure white" | Clean product listing |
| **Portrait** | "Replace background with soft gradient bokeh" | Professional headshot |
| **Composite** | "Place this product on a marble kitchen counter" | Lifestyle product shot |
| **Social Media** | "Remove background and add a vibrant gradient" | Attention-grabbing post |
| **Transparent** | "Remove the background completely" | Subject-only cutout |

## Examples

### E-commerce Product Cutout

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Remove the background from this product photo and replace it with a pure white (#FFFFFF) background. Keep the product shadow as a soft drop shadow for a floating effect."},
              {"type": "image_url", "image_url": {"url": "https://example.com/watch-on-table.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Portrait Background Swap

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Replace the background behind this person with a blurred modern office environment. Match the lighting direction of the original photo. Keep hair edges clean and natural."},
              {"type": "image_url", "image_url": {"url": "https://example.com/casual-portrait.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Creative Composite

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Place this person on a dramatic mountain cliff overlooking a misty valley at sunrise. Match the lighting and scale naturally, as if the photo was taken on location."},
              {"type": "image_url", "image_url": {"url": "https://example.com/standing-person.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Batch Product Backgrounds

```bash
PRODUCTS=(
  "https://example.com/product-1.jpg"
  "https://example.com/product-2.jpg"
  "https://example.com/product-3.jpg"
)

for URL in "${PRODUCTS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Remove the background and replace with a clean white background. Preserve realistic shadow.\"}],
      \"image_urls\": [\"$URL\"],
      \"stream\": false
    }"
  echo "---"
done
```

## Tips for Clean Results

- **Mention hair and edges**: "Keep hair edges clean and natural" prevents harsh cutout lines
- **Specify shadow handling**: "Keep a soft contact shadow" or "Remove all shadows"
- **Match lighting**: When compositing, say "Match the lighting direction of the original"
- **Simple subjects first**: Single subjects with clear edges produce the best results
- **Consistent style**: For batch processing, use the exact same prompt for all images

## Background Replacement Ideas

| Category | Background Options |
|----------|-------------------|
| **Solid Colors** | Pure white, light gray, brand color |
| **Gradients** | Soft gray gradient, warm sunset gradient |
| **Studio** | Seamless paper backdrop, fabric drape |
| **Environmental** | Office, coffee shop, outdoor park |
| **Abstract** | Geometric shapes, bokeh circles, texture |
| **Seasonal** | Autumn leaves, snow scene, spring flowers |

## Related Skills

- [AI Image Editor](../ai-image-editor/SKILL.md) — General image editing
- [Inpainting & Outpainting](../inpainting-outpainting/SKILL.md) — Fill or extend image areas
- [AI Photo Enhancer](../ai-photo-enhancer/SKILL.md) — Improve photo quality
- [AI Headshot Generator](../ai-headshot-generator/SKILL.md) — Professional headshots

## Related Models

- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for image editing tasks
- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
