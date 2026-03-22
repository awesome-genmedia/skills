---
name: ai-illustration
description: "Generate custom illustrations for textbooks, articles, and educational materials using each::sense AI. Create scientific illustrations, technical drawings, conceptual art, book illustrations, and editorial visuals in various artistic styles. Use for: textbook illustrations, article graphics, scientific illustrations, editorial art, book illustrations, educational visuals. Triggers: illustration, textbook illustration, editorial illustration, scientific illustration, book art, custom illustration, article illustration, concept illustration, technical illustration, educational art"
allowed-tools: Bash(curl *), WebFetch
---

# AI Illustration Generator

Generate custom illustrations for textbooks, articles, and educational content using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create a detailed botanical illustration of a sunflower showing the full plant from roots to flower head, with a cross-section of the stem and a magnified view of the seed arrangement in the center disc, scientific illustration style, fine line work, subtle watercolor coloring, white background"
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
        "content": "Create a detailed botanical illustration of a sunflower showing the full plant from roots to flower head, with a cross-section of the stem and a magnified view of the seed arrangement in the center disc, scientific illustration style, fine line work, subtle watercolor coloring, white background"
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
        "content": "Create an editorial illustration inspired by the style and subject of this reference image, adapt it for a magazine article, add more detail and depth, maintain the color palette, professional editorial illustration quality"
      }
    ],
    "image_urls": ["https://example.com/style-reference.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Illustration Generation

- **Specify the illustration style precisely** — botanical, technical, editorial, children's book, medical, architectural.
- **Describe composition details** — views, cross-sections, callouts, and detail insets.
- **Include medium references** — "watercolor," "pen and ink," "digital vector," "charcoal," or "gouache."
- **Mention the context** — "for a biology textbook," "for a magazine article," or "for a children's book" shapes the output.
- **Request consistent style** across multiple illustrations by reusing style keywords.

## Examples

### Scientific Illustration

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A scientific illustration of a jellyfish for a marine biology textbook: a moon jellyfish with translucent bell and trailing tentacles, showing internal radial canals and gonads visible through the transparent body, precise anatomical detail, colored pencil and ink scientific illustration style, off-white background"
      }
    ],
    "stream": false
  }'
```

### Children's Book Illustration

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A whimsical children's book illustration of a fox and a rabbit reading a book together under an old oak tree, autumn leaves falling around them, warm golden afternoon light, soft watercolor style with visible brushstrokes, gentle and inviting, storybook quality"
      }
    ],
    "stream": false
  }'
```

### Editorial Magazine Illustration

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "An editorial illustration for a New Yorker style article about remote work: a person sitting in a home office that morphs into a tropical beach on one side and a snowy mountain cabin on the other, surreal concept art, sophisticated limited color palette of teal and coral, flat graphic illustration style"
      }
    ],
    "stream": false
  }'
```

### Technical Illustration

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A technical cutaway illustration of a mechanical watch movement showing gears, mainspring, balance wheel, and escapement mechanism, exploded view with parts slightly separated to show assembly, precise mechanical drawing style, steel grey and brass tones, white background"
      }
    ],
    "stream": false
  }'
```

## Workflow: Illustration for Publications

1. **Define the subject and audience** — Academic, children's, editorial, or technical.
2. **Choose the artistic style** — Watercolor, vector, pen and ink, digital painting.
3. **Generate the illustration** — Provide detailed composition descriptions.
4. **Iterate on details** — Refine with follow-up prompts adjusting specific elements.
5. **Prepare for publication** — Upscale if needed and integrate into the layout.

## Related Skills

- [AI Diagram Generator](../ai-diagram-generator/SKILL.md) — Structured educational diagrams
- [AI Flashcard Generator](../ai-flashcard-generator/SKILL.md) — Illustrated study cards
- [AI Educational Video](../ai-educational-video/SKILL.md) — Animated educational content
- [Text to Image](../../image/text-to-image/SKILL.md) — General-purpose image generation

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — High-fidelity detailed illustrations
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Artistic and stylized outputs
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast concept sketches

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
