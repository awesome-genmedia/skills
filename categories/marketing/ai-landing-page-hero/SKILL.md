---
name: ai-landing-page-hero
description: "Generate hero images for landing pages using each::sense AI. Create visually striking above-the-fold imagery for SaaS, e-commerce, agency, and startup landing pages. Supports photorealistic, illustrated, abstract, and gradient styles. Use for: landing page design, hero sections, website headers, above-the-fold visuals, web design assets. Triggers: hero image, landing page, website header, above the fold, hero section, web hero, page hero, landing visual, header image, website banner"
allowed-tools: Bash(curl *), WebFetch
---

# AI Landing Page Hero Generator

Generate compelling hero images for landing pages and website headers using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "A wide panoramic hero image for a fintech SaaS landing page: abstract flowing data streams in deep blue and electric teal forming a wave pattern, subtle grid overlay, dark background transitioning to lighter tones on the right side leaving space for headline text, modern and professional"
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
        "content": "A wide panoramic hero image for a fintech SaaS landing page: abstract flowing data streams in deep blue and electric teal forming a wave pattern, subtle grid overlay, dark background transitioning to lighter tones on the right side leaving space for headline text, modern and professional"
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
        "content": "Create a hero image inspired by this design: extend the visual style into a wide landscape composition suitable for a website header, maintain the color palette and mood, add negative space on the left for headline text overlay"
      }
    ],
    "image_urls": ["https://example.com/design-reference.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Hero Image Generation

- **Leave negative space** for text — specify "space for headline on the left/right" in your prompt.
- **Use wide landscape orientation cues** like "panoramic," "wide shot," or "landscape format."
- **Match your brand palette** — include specific color names or hex-inspired descriptions.
- **Consider dark vs. light modes** — generate variants for both backgrounds.
- **Abstract and gradient styles** work best for overlaying text without readability issues.

## Examples

### SaaS Product Hero

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A clean hero image for a project management SaaS: an isometric 3D illustration of interconnected floating workflow cards and checkmarks in purple and soft white, clean gradient background from light lavender to white, modern tech aesthetic, wide format with empty space on the right"
      }
    ],
    "stream": false
  }'
```

### E-commerce Store Header

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A lifestyle hero image for a premium outdoor gear e-commerce store: a hiker standing at the edge of a mountain ridge at golden hour, dramatic vista of layered mountains fading into mist, cinematic wide shot, warm natural lighting, aspirational adventure mood"
      }
    ],
    "stream": false
  }'
```

### Startup Landing Page

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "An abstract hero background for an AI startup landing page: neural network visualization with glowing interconnected nodes and pathways, deep midnight blue to indigo gradient, subtle particle effects, futuristic and sophisticated, wide landscape composition with darker left side for text overlay"
      }
    ],
    "stream": false
  }'
```

### Agency Portfolio Hero

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A bold creative agency hero image: an explosion of colorful paint splashes, geometric shapes, and design tools floating in mid-air against a crisp white background, vibrant coral, electric blue, and bright yellow accents, dynamic energy, wide panoramic composition"
      }
    ],
    "stream": false
  }'
```

## Workflow: Landing Page Hero Pipeline

1. **Define page purpose** — SaaS product, e-commerce, portfolio, or campaign.
2. **Choose visual style** — Abstract, photographic, illustrated, or 3D.
3. **Generate hero with text space** — Specify where headlines and CTAs will appear.
4. **Create dark/light variants** — Generate for both color schemes.
5. **Produce responsive versions** — Generate wider and taller crops for desktop and mobile.

## Related Skills

- [AI Ad Creative](../ai-ad-creative/SKILL.md) — Ad visuals for the same campaign
- [AI Brand Kit](../ai-brand-kit/SKILL.md) — Brand-consistent visual identity
- [Text to Image](../../image/text-to-image/SKILL.md) — General-purpose image generation
- [AI Campaign Visuals](../ai-campaign-visuals/SKILL.md) — Multi-platform campaign assets

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — High-fidelity, detailed hero images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative abstract styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Quick concept exploration

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
