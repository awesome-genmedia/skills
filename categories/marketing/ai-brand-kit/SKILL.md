---
name: ai-brand-kit
description: "Create brand identity kits using each::sense AI. Generate logos, color palettes, typography samples, brand patterns, and visual style guides. Produce cohesive brand elements for startups, rebrands, and creative projects. Use for: brand identity, logo concepts, color palette generation, typography exploration, brand style guide visuals. Triggers: brand kit, brand identity, logo design, color palette, typography, brand style, brand guide, visual identity, brand elements, branding"
allowed-tools: Bash(curl *), WebFetch
---

# AI Brand Kit Generator

Create cohesive brand identity elements and visual style kits using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a modern minimalist logo concept for a tech startup called Lumina Labs. The logo should be a geometric abstract mark combining the letter L with a lightbulb motif, clean lines, flat design, vector style, on a white background"
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
        "content": "Generate a modern minimalist logo concept for a tech startup called Lumina Labs. The logo should be a geometric abstract mark combining the letter L with a lightbulb motif, clean lines, flat design, vector style, on a white background"
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
        "content": "Using this existing logo as inspiration, create a brand pattern tile that repeats the geometric motifs from the logo in a subtle repeating pattern, muted brand colors, suitable for background textures"
      }
    ],
    "image_urls": ["https://example.com/current-logo.png"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Brand Kit Generation

- **Define personality first** — Use adjectives like "bold," "elegant," "playful," "corporate," or "earthy" to guide the visual direction.
- **Specify industry context** — A fintech brand looks different from a bakery. Include the business type.
- **Request one element at a time** for best results — logo mark, then color palette, then pattern, then mockups.
- **Use consistent style cues** across all prompts in a kit to maintain visual coherence.
- **Logo text is unreliable** — Generate the symbol/mark and add text in a vector editor.

## Examples

### Logo Mark Concept

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a logo symbol for an organic skincare brand called Verdana. An elegant leaf intertwined with a water drop, line art style, sage green and gold color scheme, luxury organic aesthetic, vector flat design, white background"
      }
    ],
    "stream": false
  }'
```

### Brand Color Palette Visualization

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a brand color palette board for a premium coffee roastery: five color swatches arranged in a row, deep espresso brown, warm cream, burnt sienna, charcoal, and copper accent, each swatch as a clean rectangle, graphic design style"
      }
    ],
    "stream": false
  }'
```

### Brand Pattern Design

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a seamless repeating pattern for a children's education brand, playful geometric shapes including circles, triangles, and stars in pastel blue, coral, yellow, and mint green, white background, clean and modern"
      }
    ],
    "stream": false
  }'
```

### Brand Mockup

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A brand identity mockup flat lay: business cards, letterhead, envelope, and a tote bag all featuring a minimalist geometric logo in navy and gold, arranged on a light grey marble surface, overhead photography, professional brand presentation"
      }
    ],
    "stream": false
  }'
```

## Workflow: Building a Complete Brand Kit

1. **Define brand attributes** — Describe personality, industry, and target audience.
2. **Generate logo mark** — Create the core symbol or abstract mark.
3. **Explore color palettes** — Generate palette boards that match the brand mood.
4. **Design brand patterns** — Create repeating patterns using brand motifs.
5. **Create mockups** — Visualize the brand on stationery, packaging, and digital touchpoints.
6. **Assemble the guide** — Combine all outputs into a brand style reference.

## Related Skills

- [Logo Design](../../design/logo-design/SKILL.md) — Focused logo generation
- [AI Campaign Visuals](../ai-campaign-visuals/SKILL.md) — Apply brand identity to campaign assets
- [Brand Asset Pipeline](../../workflows/brand-asset-pipeline/SKILL.md) — Automated multi-asset brand generation
- [AI Landing Page Hero](../ai-landing-page-hero/SKILL.md) — On-brand hero images

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Precise, high-quality design outputs
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative stylistic exploration
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Rapid concept iteration

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
