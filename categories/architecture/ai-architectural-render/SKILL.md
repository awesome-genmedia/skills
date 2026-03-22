---
name: ai-architectural-render
description: "Generate photorealistic architectural renders using each::sense AI. Create presentation-quality exterior and interior renderings with accurate materials, global illumination, and environmental context. Produce V-Ray and Unreal Engine quality visualizations for client presentations and competitions. Use for: architectural rendering, photorealistic visualization, presentation renders, competition entries, real estate marketing. Triggers: architectural render, photorealistic render, archviz, V-Ray render, presentation render, 3D render architecture, building render, interior render, exterior render, architectural visualization"
allowed-tools: Bash(curl *), WebFetch
---

# AI Architectural Render

Generate photorealistic architectural renders for presentations and marketing using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "A photorealistic architectural render of a contemporary art museum: a dramatic angular facade clad in perforated weathering steel panels, a sweeping glass entrance canopy, reflecting pool at the base mirroring the building, visitors walking along the approach path, late afternoon golden light casting long shadows, V-Ray quality global illumination, ultra-detailed materials, professional archviz"
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
        "content": "A photorealistic architectural render of a contemporary art museum: a dramatic angular facade clad in perforated weathering steel panels, a sweeping glass entrance canopy, reflecting pool at the base mirroring the building, visitors walking along the approach path, late afternoon golden light casting long shadows, V-Ray quality global illumination, ultra-detailed materials, professional archviz"
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
        "content": "Transform this architectural sketch into a photorealistic render: interpret the massing and proportions from the drawing, apply concrete and glass materials, add realistic landscaping, people for scale, and dramatic sky, V-Ray render quality with accurate shadows and reflections"
      }
    ],
    "image_urls": ["https://example.com/architectural-sketch.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Architectural Renders

- **Describe materials in detail** — "brushed stainless steel mullions," "honed Carrara marble floors," "cedar battens at 50mm spacing."
- **Specify lighting precisely** — "3PM October sun at 40 degrees north latitude" or "overcast northern European light."
- **Include entourage** — people, vehicles, trees, and furniture for scale and life.
- **Reference render engines** — "V-Ray quality," "Unreal Engine photorealism," "Corona Renderer look" to guide the output.
- **Describe camera settings** — "24mm wide angle," "slight upward tilt," "eye-level perspective" for composition.

## Examples

### Luxury Residential Exterior

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A photorealistic render of a luxury hillside villa at dusk: cascading terraces with infinity pool, floor-to-ceiling glass walls revealing a warmly lit interior, natural stone and timber exterior materials, lush Mediterranean landscaping with olive trees and lavender, city lights visible in the distant valley, blue hour sky with warm interior glow contrast, professional architectural photography quality"
      }
    ],
    "stream": false
  }'
```

### Modern Office Interior

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A photorealistic interior render of a modern open-plan office: exposed concrete ceiling with visible ductwork, polished concrete floors, full-height glass partitions for meeting rooms, mid-century modern furniture, hanging pendant lights, indoor plants and biophilic design elements, natural light flooding in from large windows, people working at desks, warm and productive atmosphere, V-Ray interior render"
      }
    ],
    "stream": false
  }'
```

### Competition Render

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "An architectural competition render of a waterfront cultural center: a bold undulating timber roof structure spanning over open-air public galleries, the building sits at the waters edge with a series of stepped terraces descending to the waterline, kayakers on the river, crowds gathering for an outdoor event, dramatic cumulus clouds, warm afternoon light, hero competition render quality, atmospheric perspective"
      }
    ],
    "stream": false
  }'
```

## Workflow: Architectural Render Package

1. **Define the project** — Building type, materials, style, and site context.
2. **Generate hero exterior** — Create the primary presentation view.
3. **Render additional angles** — Corner view, aerial, street-level, and approach perspectives.
4. **Create interior views** — Key spaces like lobby, living areas, and feature rooms.
5. **Produce day and night variants** — Show the building at different times for full presentation.
6. **Add atmospheric renders** — Rainy, misty, or seasonal variants for competition entries.

## Related Skills

- [AI Building Visualization](../ai-building-visualization/SKILL.md) — Architectural concept visualization
- [AI Landscape Design](../ai-landscape-design/SKILL.md) — Surrounding landscape renders
- [Text to Image](../../image/text-to-image/SKILL.md) — General image generation
- [Image to Video Pipeline](../../workflows/image-to-video-pipeline/SKILL.md) — Animate renders into flythrough videos

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest photorealistic quality
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Atmospheric and creative renders
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast concept iteration

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
