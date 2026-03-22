---
name: ai-vehicle-wrap
description: "Generate vehicle wrap and livery designs using each::sense AI. Create custom vinyl wrap concepts, racing liveries, commercial fleet graphics, and promotional vehicle branding. Visualize wraps on cars, vans, trucks, and buses before production. Use for: vehicle wraps, livery design, fleet branding, car graphics, promotional vehicles, racing liveries. Triggers: vehicle wrap, car wrap, livery, fleet graphics, van wrap, truck wrap, car decal, racing livery, vehicle branding, wrap design"
allowed-tools: Bash(curl *), WebFetch
---

# AI Vehicle Wrap Designer

Generate custom vehicle wrap and livery designs using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "A sports car with a custom vinyl wrap design: matte black base with aggressive geometric shapes in electric blue and neon green flowing from the front fenders across the doors to the rear quarter panels, sharp angular lines, modern street racing aesthetic, three-quarter front view, studio lighting on a dark background"
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
        "content": "A sports car with a custom vinyl wrap design: matte black base with aggressive geometric shapes in electric blue and neon green flowing from the front fenders across the doors to the rear quarter panels, sharp angular lines, modern street racing aesthetic, three-quarter front view, studio lighting on a dark background"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Apply a wrap design to this vehicle: a bold commercial livery with the company colors orange and white, large graphic swooshes along the sides, clean professional look suitable for a delivery fleet, maintain the vehicle shape and angle from the reference"
      }
    ],
    "image_urls": ["https://example.com/plain-van.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Vehicle Wrap Design

- **Describe the flow direction** — how the design moves across the vehicle panels.
- **Specify the base color** — matte black, satin white, gloss grey as the foundation.
- **Include design style** — geometric, organic, camo, gradient, tribal, or corporate.
- **Mention the vehicle type** — coupe, sedan, van, truck, or bus for accurate proportions.
- **Avoid detailed text** — include graphic elements and shapes; add logos and text in a design tool.

## Examples

### Racing Livery

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A GT racing car with a professional motorsport livery: white base with red and black accents, number panel on the door, aerodynamic splitter and wing in carbon fiber, sponsor placement areas visible as colored blocks on the hood and sides, racing photography angle on a race track, motion blur background"
      }
    ],
    "stream": false
  }'
```

### Commercial Fleet Van

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A cargo van with a professional fleet wrap design: clean white upper half transitioning to a deep teal lower half with a dynamic diagonal dividing line, subtle wave pattern in the teal section, large flat areas left for company branding, side view parked on a clean urban street, overcast even lighting, commercial vehicle photography"
      }
    ],
    "stream": false
  }'
```

### Artistic Wrap Concept

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A luxury coupe with an art car wrap: the entire body covered in a flowing abstract oil painting design with rich blues, golds, and deep purples, painterly brushstroke texture wrapping around the contours of the car, parked in front of an art gallery, dramatic lighting, artistic automotive photography"
      }
    ],
    "stream": false
  }'
```

## Workflow: Vehicle Wrap Design Process

1. **Choose the vehicle** — Specify the make, model, and body style.
2. **Define the design concept** — Racing, commercial, artistic, or promotional.
3. **Generate wrap concepts** — Create initial design directions.
4. **Refine the chosen direction** — Adjust colors, patterns, and layout.
5. **Visualize from multiple angles** — Generate front, side, rear, and three-quarter views.
6. **Export for production** — Use as a reference for the vinyl wrap installer.

## Related Skills

- [AI Car Configurator](../ai-car-configurator/SKILL.md) — Vehicle customization visualization
- [AI Auto Ad](../ai-auto-ad/SKILL.md) — Automotive advertising imagery
- [AI Brand Kit](../../marketing/ai-brand-kit/SKILL.md) — Brand identity for fleet graphics
- [Text to Image](../../image/text-to-image/SKILL.md) — General image generation

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Detailed vehicle rendering
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative wrap concepts
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast design iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
