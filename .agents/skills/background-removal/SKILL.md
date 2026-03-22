---
name: background-removal
description: "Remove backgrounds from images using each::sense AI. Isolate subjects with clean edges, create transparent PNGs, replace backgrounds, and generate cutouts for products, portraits, and composites. Powered by eachlabs-bg-remover-v1 for precise edge detection. Use for: e-commerce product photos, portrait backgrounds, social media, photo compositing, transparent assets, marketing materials. Triggers: remove background, background removal, transparent background, cutout, bg remove, background eraser, isolate subject, transparent png, background swap, remove bg, no background"
allowed-tools: Bash(curl *), WebFetch
---

# Background Removal

Remove backgrounds from images with pixel-perfect edge detection using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Using curl

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Remove the background from this image completely. Return the subject on a transparent background with clean edges."},
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
    messages=[{"role": "user", "content": "Remove the background from this image completely. Return the subject on a transparent background with clean edges."}],
    # Images are included in the message content array above
)

print(response.choices[0].message.content)
```

### With Reference Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Remove the background from the first image and place the subject onto the scene shown in the second image. Match lighting and scale naturally."},
              {"type": "image_url", "image_url": {"url": "https://example.com/person.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/new-background.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Available Models

| Model | Strengths | Best For |
|-------|-----------|----------|
| **eachlabs-bg-remover-v1** | Precise edge detection, hair/fur handling, transparent output | Clean cutouts, product photos, portraits |
| **flux-2-edit** | Background replacement with natural language | Swapping to specific new backgrounds |
| **flux-fill-pro** | Inpainting after removal | Filling background areas with new content |

> each::sense selects eachlabs-bg-remover-v1 for pure removal tasks and flux-2-edit when replacement is requested.

## Use Cases

| Use Case | Instruction | Output |
|----------|-------------|--------|
| **Transparent PNG** | "Remove the background completely" | Subject on transparent background |
| **White Background** | "Remove background, replace with pure white" | Clean e-commerce listing |
| **Solid Color** | "Replace background with brand blue (#2563EB)" | Branded marketing asset |
| **Gradient** | "Replace with a soft gray-to-white gradient" | Professional portrait |
| **Environment Swap** | "Place on a tropical beach at sunset" | Lifestyle composite |
| **Studio Backdrop** | "Replace with a seamless gray studio backdrop" | Professional product shot |

## Prompt Tips

### For Clean Removal

```
"Remove the background completely. Keep edges sharp and clean,
especially around hair and fine details. Transparent background."
```

### For Background Replacement

```
"Remove the current background and replace it with [description].
Match the lighting direction from the original photo.
Keep a natural contact shadow beneath the subject."
```

### Shadow Handling

Control how shadows are treated:

```
"Remove background but keep the natural shadow beneath the product"
"Remove background and all shadows for a clean cutout"
"Remove background, add a soft artificial drop shadow on white"
```

### Edge Quality

Request specific edge treatment:

```
"Ensure hair edges are soft and natural, not hard-cut"
"Keep crisp edges around the product with no background bleed"
"Apply a very slight feather on the edges for smooth compositing"
```

## Examples

### E-commerce Product Cutout

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Remove the background from this product photo and replace it with a pure white (#FFFFFF) background. Keep a soft, natural drop shadow beneath the product for a floating effect. Crisp edges with no background artifacts."},
              {"type": "image_url", "image_url": {"url": "https://example.com/sneaker-on-table.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Professional Portrait

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Remove the background from this portrait photo. Replace with a smooth, soft-focus dark gray gradient that is lighter in the center. Keep hair edges natural and wispy, not hard-cut. Professional headshot quality."},
              {"type": "image_url", "image_url": {"url": "https://example.com/office-portrait.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Transparent Asset for Design

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Remove the background from this image entirely. Output a transparent PNG with no background at all. Clean edges suitable for layering in a design tool like Figma or Photoshop. Remove all shadows."},
              {"type": "image_url", "image_url": {"url": "https://example.com/plant-photo.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Lifestyle Composite

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Remove the background and place this person on a sunlit rooftop terrace overlooking a Mediterranean coastal city. Match the warm afternoon lighting from the original photo. The person should look naturally placed in the scene with correct scale and perspective."},
              {"type": "image_url", "image_url": {"url": "https://example.com/standing-person.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Social Media Branded Post

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Remove the background from this photo and replace it with a bold coral-to-magenta gradient going from bottom-left to top-right. Keep the subject sharp with clean edges. This is for an Instagram post, so make it vibrant and eye-catching."},
              {"type": "image_url", "image_url": {"url": "https://example.com/influencer-photo.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

## Batch Processing

```bash
# Remove backgrounds from multiple product photos
PRODUCTS=(
  "https://example.com/product-1.jpg"
  "https://example.com/product-2.jpg"
  "https://example.com/product-3.jpg"
  "https://example.com/product-4.jpg"
)

for URL in "${PRODUCTS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Remove the background. Replace with pure white. Keep a soft natural shadow. Clean product cutout.\"}],
      \"image_urls\": [\"$URL\"],
      \"stream\": false
    }"
  echo "---"
done
```

## Subject Types and Tips

| Subject | Challenge | Tip |
|---------|-----------|-----|
| **People (hair)** | Fine hair strands | "Keep hair edges soft and natural" |
| **Pets (fur)** | Fluffy edges | "Preserve fur detail around edges" |
| **Products (hard edges)** | Reflections, shadows | "Crisp edges, handle reflections" |
| **Plants (leaves)** | Complex silhouettes | "Preserve leaf detail and gaps" |
| **Transparent objects** | Glass, bottles | "Handle transparent/translucent areas" |
| **Complex scenes** | Multiple subjects | "Isolate only the main subject in the center" |

## Common Pitfalls

- **Not specifying what to keep**: "Remove background" is good; "Remove the background but keep the table the product sits on" is better when needed.
- **Expecting color-matched composites automatically**: When replacing backgrounds, always mention "match the lighting" for natural results.
- **Ignoring hair/fur edges**: Default removal may hard-cut fine details. Explicitly request "soft, natural hair edges."
- **No shadow instructions**: The model may keep or remove shadows unpredictably. State your preference.
- **Very busy backgrounds** with colors similar to the subject are harder. Higher contrast between subject and background produces cleaner results.

## Related Skills

- [Image Editing](../image-editing/SKILL.md) — General edits after background removal
- [Image Upscaling](../image-upscaling/SKILL.md) — Enhance resolution of cutouts
- [Face Swap](../face-swap/SKILL.md) — Replace faces in composited images
- [Image Generation](../image-generation/SKILL.md) — Generate new backgrounds to composite onto

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
