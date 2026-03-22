---
name: ai-landscape-design
description: "Generate landscape and garden design visualizations using each::sense AI. Create residential garden plans, public park designs, commercial landscaping, rooftop gardens, and outdoor living spaces with realistic plants, hardscaping, and lighting. Use for: landscape design, garden visualization, outdoor spaces, park design, hardscaping plans. Triggers: landscape design, garden design, landscaping, outdoor space, garden visualization, park design, backyard design, patio design, green space, planting design"
allowed-tools: Bash(curl *), WebFetch
---

# AI Landscape Design

Generate landscape and garden design visualizations using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "A landscape design visualization for a modern residential backyard: a rectangular lap pool with blue mosaic tiles, surrounded by a timber deck, ornamental grasses and lavender plantings along the borders, a pergola with climbing jasmine over a dining area, string lights, warm evening atmosphere, photorealistic landscape architecture render"
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
        "content": "A landscape design visualization for a modern residential backyard: a rectangular lap pool with blue mosaic tiles, surrounded by a timber deck, ornamental grasses and lavender plantings along the borders, a pergola with climbing jasmine over a dining area, string lights, warm evening atmosphere, photorealistic landscape architecture render"
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
        "content": "Redesign this existing backyard space: replace the lawn with drought-tolerant native plantings, add a gravel pathway with stepping stones, include a fire pit seating area, maintain the existing mature tree, add low-voltage landscape lighting, photorealistic landscape design render"
      }
    ],
    "image_urls": ["https://example.com/current-backyard.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Landscape Design

- **Name specific plants** — "Japanese maple," "blue fescue grass," "hydrangea" rather than generic "plants."
- **Describe hardscaping materials** — "flagstone pavers," "decomposed granite," "reclaimed brick."
- **Specify the viewing angle** — "bird's eye plan view," "eye-level perspective from the patio," or "elevated angle."
- **Include water features** — fountains, ponds, streams, and pools add visual interest.
- **Mention the climate zone** — "Mediterranean climate garden," "English cottage garden," "desert xeriscape."

## Examples

### Japanese Zen Garden

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A Japanese zen garden landscape design: raked white gravel forming concentric circles around three carefully placed natural boulders, a single pruned black pine, a tsukubai stone water basin, moss-covered stepping stones leading to a simple wooden gate, bamboo fence boundary, tranquil and meditative atmosphere, soft overcast light, landscape architecture visualization"
      }
    ],
    "stream": false
  }'
```

### Public Park Design

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "An aerial view landscape design for a public urban park: a central oval lawn surrounded by curving walking paths, clusters of deciduous trees providing shade, a children's playground area, a small amphitheater with terraced seating, a community garden section, bike paths connecting to city streets, summer afternoon light, landscape master plan render"
      }
    ],
    "stream": false
  }'
```

### Rooftop Garden

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A rooftop garden design for a modern apartment building: raised planter beds with herbs and vegetables, a sedum green roof section, a lounge area with weather-resistant outdoor sofas, a wooden pergola with shade sails, city skyline visible in the background, golden hour warm light, urban landscape design visualization"
      }
    ],
    "stream": false
  }'
```

## Workflow: Landscape Design Presentation

1. **Assess the site** — Provide or describe the existing space and constraints.
2. **Generate plan view** — Create a bird's eye layout showing the overall design.
3. **Render perspective views** — Visualize the garden from key viewpoints.
4. **Show seasonal variations** — Generate spring bloom, summer lush, and autumn color versions.
5. **Create detail vignettes** — Close-up renders of feature areas (water feature, seating, planting beds).
6. **Compile the package** — Assemble views into a client presentation.

## Related Skills

- [AI Building Visualization](../ai-building-visualization/SKILL.md) — Architectural building renders
- [AI Architectural Render](../ai-architectural-render/SKILL.md) — Photorealistic structure renders
- [Text to Image](../../image/text-to-image/SKILL.md) — General image generation
- [AI Stock Photo](../../photography/ai-stock-photo/SKILL.md) — Nature and garden photography

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Photorealistic landscape renders
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Lush natural environments
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Quick concept sketches

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
