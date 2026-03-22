---
name: brand-asset-pipeline
description: "Generate complete brand assets in a pipeline using each::sense AI. Create a cohesive brand package including logo concept, social media profile images, cover banners, business card mockups, and branded patterns from a single brand brief. Use for: brand asset generation, complete branding, brand package, visual identity pipeline, startup branding. Triggers: brand asset pipeline, brand package, complete branding, brand assets, visual identity, brand generation, startup branding, brand pipeline, identity package, brand suite"
allowed-tools: Bash(curl *), WebFetch
---

# Brand Asset Pipeline

Generate a complete set of brand assets from a single brief using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

This workflow generates multiple brand assets sequentially, using consistent style keywords to maintain visual cohesion.

### Step 1: Logo Concept

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a logo symbol for a premium tea brand called Zenith Tea: an elegant minimal line drawing of a tea leaf merging with a mountain peak, single continuous line style, works in deep forest green on white and white on dark backgrounds, modern luxury aesthetic, vector flat design, centered on white background"
      }
    ],
    "stream": false
  }'
```

### Step 2: Social Media Profile Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A social media profile picture for Zenith Tea brand: the tea leaf and mountain logo symbol centered on a deep forest green circular background, minimalist, clean edges suitable for a small circular avatar, luxury tea brand aesthetic"
      }
    ],
    "stream": false
  }'
```

### Step 3: Social Media Cover Banner

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A wide social media cover banner for Zenith Tea: misty mountain landscape at dawn with rolling tea plantations in the foreground, deep forest green and soft gold color palette, atmospheric depth, space on the left for text overlay, premium tea brand photography, panoramic landscape format"
      }
    ],
    "stream": false
  }'
```

### Full Pipeline in Python

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_EACHLABS_API_KEY",
    base_url="https://eachsense-agent.core.eachlabs.run/v1"
)

BRAND = "Zenith Tea"
STYLE = "deep forest green and gold, luxury minimalist, elegant"

assets = {
    "logo": f"Logo symbol for {BRAND}: a tea leaf merging with a mountain peak, minimal line art, {STYLE}, vector flat design, white background",
    "profile": f"Social media avatar for {BRAND}: logo symbol on deep forest green circle, clean minimal, {STYLE}, square format",
    "cover": f"Social media cover banner for {BRAND}: misty mountain tea plantations at dawn, {STYLE}, panoramic wide format with text space on left",
    "pattern": f"Brand pattern tile for {BRAND}: subtle repeating tea leaf and mountain motifs, {STYLE}, seamless repeating pattern, muted tones",
    "card": f"Business card mockup for {BRAND}: minimalist card on dark surface, {STYLE}, logo centered, clean typography areas, professional presentation"
}

for asset_name, prompt in assets.items():
    print(f"Generating {asset_name}...")
    response = client.chat.completions.create(
        model="eachsense/beta",
        messages=[{"role": "user", "content": prompt}]
    )
    print(f"  {asset_name}: {response.choices[0].message.content}")
    print("---")
```

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Brand Asset Pipelines

- **Define a style string** — Create a reusable style description (colors, adjectives, aesthetic) and include it in every prompt.
- **Generate the logo first** — It sets the visual direction for all other assets.
- **Maintain color consistency** — Name the exact same colors in every prompt.
- **Specify format per asset** — Square for avatars, wide for banners, vertical for stories.
- **Generate mockups last** — Use the established brand elements in context mockups.

## Examples

### Tech Startup Brand Package

```bash
# Define consistent brand style
BRAND_STYLE="electric blue and white, clean geometric, modern tech"

# Logo
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d "{
    \"messages\": [{\"role\": \"user\", \"content\": \"Logo for a SaaS startup called DataFlow: abstract flowing data stream forming the letter D, $BRAND_STYLE, vector flat design, white background\"}],
    \"stream\": false
  }"

# Social profile
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d "{
    \"messages\": [{\"role\": \"user\", \"content\": \"Social media profile picture for DataFlow: logo mark on dark navy background, circular format, $BRAND_STYLE\"}],
    \"stream\": false
  }"

# Cover banner
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d "{
    \"messages\": [{\"role\": \"user\", \"content\": \"LinkedIn cover banner for DataFlow: abstract data visualization with flowing connected nodes and lines, $BRAND_STYLE, wide panoramic format, dark background with glowing elements, space for tagline on the right\"}],
    \"stream\": false
  }"
```

## Workflow: Complete Brand Asset Pipeline

1. **Write the brand brief** — Name, personality, colors, industry, and target audience.
2. **Create the style string** — A reusable description of the brand's visual language.
3. **Generate the logo** — The foundation for all other assets.
4. **Create social media assets** — Profile, cover, and story templates.
5. **Design brand pattern** — A repeating pattern for backgrounds and textures.
6. **Generate mockups** — Business cards, letterheads, signage, and packaging.
7. **Compile the brand guide** — Assemble all assets with usage guidelines.

## Related Skills

- [AI Brand Kit](../../marketing/ai-brand-kit/SKILL.md) — Brand identity element generation
- [Social Media Batch](../social-media-batch/SKILL.md) — Multi-platform content generation
- [Logo Design](../../design/logo-design/SKILL.md) — Focused logo generation
- [AI Campaign Visuals](../../marketing/ai-campaign-visuals/SKILL.md) — Campaign asset creation

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Precise brand asset quality
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative brand exploration
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Rapid iteration

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
