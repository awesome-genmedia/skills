---
name: ai-diagram-generator
description: "Generate educational diagrams and flowcharts using each::sense AI. Create process flows, mind maps, system diagrams, Venn diagrams, timelines, and organizational charts for teaching, presentations, and documentation. Use for: educational diagrams, flowcharts, process visualization, mind maps, infographics, technical diagrams. Triggers: diagram, flowchart, mind map, process flow, Venn diagram, timeline, org chart, educational diagram, chart, infographic, system diagram"
allowed-tools: Bash(curl *), WebFetch
---

# AI Diagram Generator

Generate clear, informative educational diagrams and flowcharts using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create a clean educational diagram showing the water cycle: evaporation from ocean, condensation forming clouds, precipitation as rain, collection in rivers and lakes flowing back to the ocean, arrows connecting each stage, labeled steps, blue and white color scheme, infographic style"
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
        "content": "Create a clean educational diagram showing the water cycle: evaporation from ocean, condensation forming clouds, precipitation as rain, collection in rivers and lakes flowing back to the ocean, arrows connecting each stage, labeled steps, blue and white color scheme, infographic style"
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
        "content": [
              {"type": "text", "text": "Based on this rough sketch, create a polished educational diagram with clean lines, consistent icons, color-coded sections, and clear directional arrows, professional infographic style"},
              {"type": "image_url", "image_url": {"url": "https://example.com/rough-sketch.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Diagram Generation

- **Be specific about diagram type** — flowchart, mind map, Venn diagram, timeline, hierarchy, cycle diagram.
- **Describe the structure** — number of nodes, levels, branches, and connections.
- **Specify visual style** — flat design, isometric, hand-drawn, minimalist, or corporate.
- **Limit text in prompts** — AI-generated text labels can be unreliable. Request shapes and structure, then add labels in a design tool.
- **Use color coding** — specify colors for different categories or process stages.

## Examples

### Process Flowchart

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A software development lifecycle flowchart: rectangular boxes connected by arrows in a circular flow, six stages from requirements through design, development, testing, deployment, and maintenance, each box a different color from blue to green spectrum, clean flat design, white background, professional technical diagram"
      }
    ],
    "stream": false
  }'
```

### Biology Cell Diagram

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A detailed cross-section diagram of an animal cell showing nucleus, mitochondria, endoplasmic reticulum, Golgi apparatus, ribosomes, and cell membrane, each organelle in a distinct color, clean scientific illustration style, labeled with pointer lines, educational biology diagram"
      }
    ],
    "stream": false
  }'
```

### Timeline Infographic

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A horizontal timeline infographic showing the history of space exploration with six milestone points along a line, each with a small icon representing the event, alternating above and below the timeline, gradient from dark blue to purple background, modern flat design, space-themed"
      }
    ],
    "stream": false
  }'
```

### Mind Map

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A mind map diagram about renewable energy sources: central node branching out to solar, wind, hydro, geothermal, and biomass, each branch in a different color with sub-branches showing advantages and applications, organic flowing connections, clean white background, educational infographic style"
      }
    ],
    "stream": false
  }'
```

## Workflow: Educational Diagram Creation

1. **Identify the concept** — What process, system, or relationship needs visualization.
2. **Choose diagram type** — Flowchart, mind map, cycle, timeline, hierarchy, or comparison.
3. **Generate the visual structure** — Create the layout with nodes, connections, and color coding.
4. **Add labels and annotations** — Overlay accurate text labels in a design or presentation tool.
5. **Refine for audience** — Adjust complexity for the target audience level.

## Related Skills

- [AI Flashcard Generator](../ai-flashcard-generator/SKILL.md) — Visual flashcards for learning
- [AI Illustration](../ai-illustration/SKILL.md) — Custom educational illustrations
- [AI Educational Video](../ai-educational-video/SKILL.md) — Animated educational content
- [Text to Image](../../image/text-to-image/SKILL.md) — General-purpose image generation

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Detailed, precise visual outputs
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Clean illustrative styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Quick concept drafts

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
