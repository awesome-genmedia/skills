---
name: ai-building-visualization
description: "Generate architectural visualization renders of buildings using each::sense AI. Create exterior and interior views of residential, commercial, and public buildings with realistic materials, lighting, and environments. Supports concept design through to presentation-quality renders. Use for: building visualization, architectural concept, exterior render, interior render, building design. Triggers: building visualization, architecture render, building render, exterior view, interior view, architectural visualization, building concept, structure design, building design, archviz"
allowed-tools: Bash(curl *), WebFetch
---

# AI Building Visualization

Generate architectural visualization renders of buildings and structures using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "An architectural visualization of a modern three-story residential house: floor-to-ceiling glass facades, cantilevered upper floor, white concrete and natural wood cladding, flat green roof with a rooftop terrace, surrounded by mature landscaping, golden hour lighting with warm reflections in the glass, photorealistic architectural render"
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
        "content": "An architectural visualization of a modern three-story residential house: floor-to-ceiling glass facades, cantilevered upper floor, white concrete and natural wood cladding, flat green roof with a rooftop terrace, surrounded by mature landscaping, golden hour lighting with warm reflections in the glass, photorealistic architectural render"
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
        "content": "Create an architectural visualization based on this floor plan sketch: render the building as a photorealistic exterior view from the street, add contextual landscaping, parked cars, pedestrians, and realistic sky, modern materials with glass and steel, late afternoon lighting"
      }
    ],
    "image_urls": ["https://example.com/floor-plan-sketch.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Building Visualization

- **Specify materials precisely** — "exposed concrete," "Corten steel," "cedar cladding," "full-height glass curtain wall."
- **Define the viewing angle** — "street-level perspective," "aerial view," "corner view," or "courtyard interior."
- **Include context elements** — people, vehicles, vegetation, and surrounding buildings for scale.
- **Describe lighting conditions** — time of day, weather, and interior illumination for mood.
- **Mention the architectural style** — modernist, brutalist, deconstructivist, sustainable, minimalist, or vernacular.

## Examples

### Commercial Office Building

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Architectural visualization of a 12-story commercial office tower: glass curtain wall facade with vertical aluminum fins for sun shading, a double-height lobby at ground level, a landscaped public plaza at the base with seating and water features, surrounding urban context, clear blue sky, photorealistic archviz quality"
      }
    ],
    "stream": false
  }'
```

### Interior Living Space

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "An interior architectural visualization of a luxury penthouse living room: double-height ceiling with a mezzanine, floor-to-ceiling windows overlooking a city skyline at dusk, polished concrete floors, a floating staircase in steel and glass, modern furniture in neutral tones, warm ambient lighting from recessed fixtures, V-Ray quality render"
      }
    ],
    "stream": false
  }'
```

### Sustainable Building Concept

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A sustainable community center building visualization: organic curved forms in cross-laminated timber, living green walls covering portions of the facade, integrated solar panels on the undulating roof, rainwater collection channels visible as design features, native wildflower meadow surrounding the building, overcast diffused light, ecological architecture render"
      }
    ],
    "stream": false
  }'
```

## Workflow: Architectural Presentation Pipeline

1. **Define the brief** — Building type, style, materials, and context.
2. **Generate concept views** — Create exterior perspectives from key viewing angles.
3. **Render interior spaces** — Visualize lobby, living areas, and feature rooms.
4. **Create context scenes** — Show the building in its urban or natural environment.
5. **Produce time-of-day variants** — Day, dusk, and night renders for presentation variety.
6. **Compile the presentation** — Assemble renders into a client presentation.

## Related Skills

- [AI Landscape Design](../ai-landscape-design/SKILL.md) — Landscape and garden visualization
- [AI Architectural Render](../ai-architectural-render/SKILL.md) — Photorealistic architectural renders
- [Text to Image](../../image/text-to-image/SKILL.md) — General image generation
- [AI Stock Photo](../../photography/ai-stock-photo/SKILL.md) — Context and lifestyle photography

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Photorealistic rendering quality
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative architectural concepts
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Quick concept sketches

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
