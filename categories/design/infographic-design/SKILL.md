---
name: infographic-design
description: "Create data visualization infographics using each::sense AI. Generate visually compelling infographic backgrounds, layouts, and visual elements for statistical data, process flows, timelines, comparisons, and educational content. Supports flat design, illustrated, corporate, and editorial styles. Use for: infographics, data visualization, process diagrams, timeline graphics, statistical illustrations, comparison charts. Triggers: infographic, data visualization, infographic design, process flow, timeline graphic, data illustration, statistical graphic, comparison infographic, visual data, info graphic, chart design"
allowed-tools: Bash(curl *), WebFetch
---

# Infographic Design

Create visually compelling infographic layouts and data visualization graphics using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create an infographic background and visual layout for a sustainability report. Vertical scrolling format, clean white background, sections separated by flowing green wave dividers, flat vector icons of trees and wind turbines as decorative elements, earth tones and forest green palette, modern and professional."
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
        "content": "Create an infographic background and visual layout for a sustainability report. Vertical scrolling format, clean white background, sections separated by flowing green wave dividers, flat vector icons of trees and wind turbines as decorative elements, earth tones and forest green palette, modern and professional."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide a data sketch or existing infographic for style matching:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Create a new infographic visual in the same style as this reference. Match the color scheme and illustration style, but create a layout for a 5-step process flow with numbered circular icons connected by dotted lines, vertical format."},
              {"type": "image_url", "image_url": {"url": "https://example.com/infographic-reference.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Infographic Types

| Type | Layout | Best For |
|------|--------|----------|
| **Statistical** | Charts, graphs, numbers | Reports, surveys, research |
| **Process/How-to** | Numbered steps, flow | Tutorials, workflows |
| **Timeline** | Chronological sequence | History, project milestones |
| **Comparison** | Side-by-side columns | Product comparisons, pros/cons |
| **Geographic** | Map-based visuals | Regional data, logistics |
| **Hierarchical** | Pyramid or tree | Organizational, priority data |
| **List** | Numbered or icon list | Tips, features, facts |

## Prompt Engineering Tips

### Keywords That Work

```
infographic layout, flat vector illustration, clean data visualization,
icon-based design, section dividers, numbered steps, color-coded sections,
vertical scrolling format, consistent icon style, white space between sections
```

### Keywords to Avoid

```
actual data and numbers — add real data in design software
tiny detailed charts — too complex for AI generation
3D rendered elements — flat vector works best for infographics
photorealistic style — illustrated/flat design is standard
```

### Prompt Structure

```
infographic [type] for [topic], [layout description], [visual elements], [color palette], [style], vertical/horizontal format
```

## Examples

### Technology Process Flow

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a technology process infographic layout. Four connected stages flowing left to right, each stage is a rounded rectangle with a flat vector icon placeholder inside (gear, cloud, shield, rocket), connected by animated-looking arrows, dark background with neon blue and purple accents, futuristic and clean."
      }
    ],
    "stream": false
  }'
```

### Health and Wellness Infographic

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a health infographic visual layout about daily nutrition. Vertical format, soft pastel background, a central illustrated human body silhouette with color-coded arrows pointing to different body parts, each arrow ends in a circular icon area for food groups, warm and friendly illustration style."
      }
    ],
    "stream": false
  }'
```

### Business Statistics Layout

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a corporate statistics infographic template. Clean white background, four equal sections stacked vertically separated by thin gray lines, each section has a large circular chart placeholder on the left and a text area on the right, navy blue and gold accent colors, professional and data-driven."
      }
    ],
    "stream": false
  }'
```

## Infographic Design Principles

- **Visual hierarchy** — guide the eye from top to bottom in a logical flow
- **One color per category** — use consistent color coding throughout
- **Icons over text** — visual elements communicate faster than words
- **White space** — generous spacing between sections prevents visual overwhelm
- **Consistent style** — all icons and illustrations should use the same visual language
- **Standard width** — 800-1200px wide for web, taller as needed for content

## Workflow

```bash
# Step 1: Generate the infographic layout
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Infographic layout for a startup funding timeline. Vertical format, road or path metaphor winding from bottom to top, five milestone markers along the path, each marker is a distinct colored circle, light gray background, flat modern illustration style."
      }
    ],
    "stream": false
  }'

# Step 2: Refine specific sections
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Infographic layout for a startup funding timeline. Vertical format, road or path metaphor winding from bottom to top, five milestone markers along the path, each marker is a distinct colored circle, light gray background, flat modern illustration style."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Add small flat vector illustrations next to each milestone: a lightbulb for ideation, a handshake for seed round, a sprouting plant for growth, a building for scaling, and a flag on top for IPO. Keep the same color scheme."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [Presentation Slides](../presentation-slides/SKILL.md) — Slide deck backgrounds
- [Social Media Post](../social-media-post/SKILL.md) — Share infographics on social
- [Pinterest Pins](../../social-media/pinterest-pins/SKILL.md) — Pin-optimized infographics
- [Poster Design](../poster-design/SKILL.md) — Print-ready informational posters

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for text rendering in images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
