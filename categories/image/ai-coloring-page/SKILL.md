---
name: ai-coloring-page
description: "Generate printable coloring pages using each::sense AI. Create line art illustrations perfect for coloring books, children's activities, adult relaxation coloring, educational worksheets, and therapeutic art. Supports simple children's designs, detailed mandala patterns, and complex adult coloring pages. Use for: coloring books, children's activities, art therapy, educational materials, printable worksheets, mandala coloring, adult coloring. Triggers: coloring page, coloring book, line art, printable coloring, kids coloring, adult coloring, mandala coloring, coloring sheet, color page, black and white line art, coloring activity"
allowed-tools: Bash(curl *), WebFetch
---

# AI Coloring Page Generator

Generate printable coloring pages and line art illustrations using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a coloring page: a friendly dragon sitting in a garden surrounded by flowers and butterflies. Black and white line art, clean outlines, no shading or filled areas, suitable for children ages 5-8 to color in. White background."
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
        "content": "Generate a coloring page: a friendly dragon sitting in a garden surrounded by flowers and butterflies. Black and white line art, clean outlines, no shading or filled areas, suitable for children ages 5-8 to color in. White background."
    }]
)

print(response.choices[0].message.content)
```

### From Reference Image

Convert a photo or artwork into a coloring page:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Convert this image into a coloring page. Extract the main outlines and shapes, remove all color and shading, create clean black line art on a white background suitable for coloring with crayons or colored pencils."
      }
    ],
    "image_urls": ["https://example.com/colorful-scene.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Complexity Levels

| Level | Age Group | Characteristics |
|-------|-----------|-----------------|
| **Simple** | Ages 2-4 | Large shapes, thick outlines, few details, big open areas |
| **Easy** | Ages 5-7 | Medium shapes, clear outlines, some detail, recognizable subjects |
| **Medium** | Ages 8-12 | More detail, smaller areas, varied line weights |
| **Detailed** | Teens/Adults | Fine details, intricate patterns, many small sections |
| **Complex** | Adults | Mandala-level intricacy, tiny sections, pattern fills |

## Examples

### Children's Animal Page

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Coloring page for young children: a cute cartoon cat wearing a party hat, sitting next to a birthday cake with candles. Simple shapes, thick black outlines, large areas to color, minimal small details. Black and white line art on white background."
      }
    ],
    "stream": false
  }'
```

### Adult Mandala

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Intricate mandala coloring page for adults. Circular symmetrical design with layers of floral petals, geometric shapes, and ornate filigree patterns radiating from the center. Fine detailed line art, many small sections to color, black lines on white background. Meditative and complex."
      }
    ],
    "stream": false
  }'
```

### Educational Scene

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Educational coloring page: the solar system with the sun in the center and all eight planets in their orbits. Each planet should be recognizable by its features — Saturn with rings, Jupiter with bands, Earth with continents. Labels space for planet names. Black and white line art, suitable for elementary school students."
      }
    ],
    "stream": false
  }'
```

### Coloring Book Series

```bash
THEMES=(
  "Coloring page: an underwater coral reef scene with tropical fish, a sea turtle, an octopus, and seaweed"
  "Coloring page: a medieval castle with a knight on horseback, a drawbridge, and flags on turrets"
  "Coloring page: a space station orbiting Earth with an astronaut floating outside, stars, and a shuttle approaching"
  "Coloring page: a dense jungle scene with a toucan, a monkey, a tree frog, vines, and large tropical leaves"
)

for THEME in "${THEMES[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"$THEME. Black and white line art, clean outlines, no shading, white background, suitable for ages 6-10.\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Prompt Tips

- **Always specify "black and white line art"** — without this, the model may add color or shading
- **Say "no shading, no filled areas, no gray tones"** to get clean colorable outlines
- **Mention the age group** to calibrate complexity
- **White background** ensures clean printing
- **"Clean outlines"** prevents sketchy or fuzzy lines
- **Avoid "realistic"** — coloring pages work best with stylized or cartoon-like art

## Print Specifications

- Best printed at standard paper sizes (Letter 8.5x11", A4)
- Request images with generous margins for easy coloring at the edges
- Thick outlines (specify "bold outlines") are easier for young children
- Fine outlines work better for adult coloring with colored pencils

## Related Skills

- [Text to Image](../text-to-image/SKILL.md) — General image generation
- [AI Pattern Generator](../ai-pattern-generator/SKILL.md) — Mandala and pattern designs
- [AI Tattoo Generator](../ai-tattoo-generator/SKILL.md) — Line art style designs

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
