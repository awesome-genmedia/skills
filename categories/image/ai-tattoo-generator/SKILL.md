---
name: ai-tattoo-generator
description: "Generate custom tattoo designs using each::sense AI. Create concept art for tattoos in styles including traditional, blackwork, watercolor, Japanese, geometric, minimalist, and neo-traditional. Generates print-ready design sheets for tattoo artists to reference. Use for: tattoo concepts, flash sheet designs, custom tattoo ideas, tattoo artist references, body art planning. Triggers: ai tattoo, tattoo design, tattoo generator, custom tattoo, tattoo concept, tattoo art, tattoo flash, tattoo idea, body art design, tattoo sketch, tattoo stencil"
allowed-tools: Bash(curl *), WebFetch
---

# AI Tattoo Generator

Generate custom tattoo design concepts using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Tattoo design: a geometric wolf head in dotwork style. The wolf face is composed of sacred geometry patterns — triangles, circles, and hexagons. Fine linework, black ink only, designed for forearm placement. White background, tattoo flash sheet style."
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
        "content": "Tattoo design: a geometric wolf head in dotwork style. The wolf face is composed of sacred geometry patterns — triangles, circles, and hexagons. Fine linework, black ink only, designed for forearm placement. White background, tattoo flash sheet style."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Use a reference for style matching or subject inspiration:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Create a tattoo design inspired by this image. Convert it to a blackwork tattoo style with bold outlines, stipple shading, and clean negative space. White background, designed for upper arm placement."},
              {"type": "image_url", "image_url": {"url": "https://example.com/inspiration-photo.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tattoo Styles

| Style | Description | Keywords |
|-------|-------------|----------|
| **Traditional (Old School)** | Bold outlines, limited palette, classic subjects | bold lines, sailor flash, Americana |
| **Neo-Traditional** | Traditional foundations with modern detail and color | illustrative, rich color, ornate |
| **Blackwork** | Solid black fills, bold graphic designs | black ink only, solid black, graphic |
| **Dotwork** | Patterns made of individual dots | stipple, pointillism, mandala |
| **Geometric** | Sacred geometry, clean shapes, mathematical | symmetrical, geometric pattern, linework |
| **Japanese (Irezumi)** | Koi, dragons, waves, cherry blossoms | Japanese traditional, ukiyo-e, full sleeve |
| **Watercolor** | Soft edges, color splashes, painterly | watercolor splashes, no outlines, fluid |
| **Minimalist** | Simple lines, small, subtle | fine line, single needle, delicate |
| **Realism** | Photographic detail, portraits | photorealistic, portrait tattoo, hyperdetail |
| **Tribal** | Bold black patterns, cultural motifs | Polynesian, Maori, bold black |

## Examples

### Japanese Full Sleeve Concept

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Japanese traditional tattoo design for a full sleeve. A koi fish swimming upstream through crashing waves, surrounded by cherry blossoms and maple leaves. Wind bars and cloud patterns fill the negative space. Traditional Irezumi color palette — red, black, gold, blue. White background, flat tattoo reference sheet."
      }
    ],
    "stream": false
  }'
```

### Minimalist Fine Line

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Minimalist fine line tattoo design: a continuous single-line drawing of a mountain range with a small sun rising between the peaks. Delicate, thin lines, no shading, no fill. Designed for inner wrist placement. White background."
      }
    ],
    "stream": false
  }'
```

### Watercolor Botanical

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Watercolor tattoo design: a peony flower in full bloom with loose watercolor splashes of pink, magenta, and soft purple bleeding outward. No hard outlines, soft edges, organic paint drips. Designed for shoulder blade placement. White background, tattoo flash style."
      }
    ],
    "stream": false
  }'
```

## Placement Considerations

| Body Area | Design Shape | Considerations |
|-----------|-------------|----------------|
| **Forearm** | Long, vertical or wrapping | Visible, medium detail |
| **Upper Arm** | Round or broad designs | Good for detail, concealable |
| **Wrist** | Small, horizontal | Fine line works best |
| **Back** | Large, horizontal or full | Maximum detail potential |
| **Ribs** | Tall, narrow | Painful area, vertical flow |
| **Calf** | Vertical or wrapping | Good canvas, medium-large |
| **Shoulder** | Round, fits the cap shape | Great for mandalas, portraits |

## Prompt Structure

```
Tattoo design: [subject] in [style] style.
[Detailed description of the design].
[Color/ink specification].
Designed for [placement].
White background, tattoo flash sheet style.
```

## Important Notes

- These designs are **concept references** — always work with a professional tattoo artist for the final design
- AI-generated designs may need adjustment for skin curvature and body placement
- Mention "white background" to get a clean reference sheet the artist can work from
- Specify "tattoo flash sheet style" for the most usable output format

## Related Skills

- [Text to Image](../text-to-image/SKILL.md) — General image generation
- [AI Pattern Generator](../ai-pattern-generator/SKILL.md) — Pattern and mandala designs
- [AI Coloring Page](../ai-coloring-page/SKILL.md) — Line art designs

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
