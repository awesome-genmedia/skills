---
name: ai-ad-creative
description: "Generate ad creatives for digital campaigns using each::sense AI. Create scroll-stopping banner ads, social media ad visuals, display ads, and promotional graphics optimized for platforms like Facebook, Instagram, Google Ads, and LinkedIn. Use for: digital advertising, social media ads, display banners, retargeting creatives, A/B test variations. Triggers: ad creative, banner ad, social ad, display ad, ad design, campaign creative, promotional graphic, ad visual, marketing ad, advertising image"
allowed-tools: Bash(curl *), WebFetch
---

# AI Ad Creative Generator

Generate high-converting ad creatives for digital campaigns using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create a vibrant Instagram ad image for a summer sale on athletic shoes, featuring a pair of sleek white running shoes on a sun-drenched track, warm golden light, energetic feel, clean commercial photography style"
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
        "content": "Create a vibrant Instagram ad image for a summer sale on athletic shoes, featuring a pair of sleek white running shoes on a sun-drenched track, warm golden light, energetic feel, clean commercial photography style"
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
        "content": "Create a Facebook ad visual based on this product image, place the product on a clean gradient background with soft shadows, professional commercial lighting, ad-ready composition"
      }
    ],
    "image_urls": ["https://example.com/product-photo.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Effective Ad Creatives

- **Specify the platform** (Instagram, Facebook, Google Display) to get the right composition and aspect ratio feel.
- **Describe the product clearly** — include color, material, and positioning.
- **Include mood keywords** like "energetic," "luxurious," "trustworthy," or "playful" to shape the visual tone.
- **Mention lighting style** — studio lighting for products, natural light for lifestyle, dramatic for premium.
- **Avoid requesting text overlays** — AI image generation does not reliably render text. Add copy in a design tool after.

## Examples

### E-commerce Product Ad

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A premium wireless noise-cancelling headphone floating against a deep navy background, soft spotlight from above, subtle reflections on the glossy surface, minimalist product photography for a Google Display ad"
      }
    ],
    "stream": false
  }'
```

### Lifestyle Campaign Visual

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A young professional woman working on a laptop in a sunlit coworking space, warm natural tones, modern interior design, shallow depth of field, lifestyle photography for a SaaS product ad campaign"
      }
    ],
    "stream": false
  }'
```

### Seasonal Promotion

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A cozy holiday scene for a winter sale ad: a steaming mug of hot cocoa surrounded by wrapped gifts and pine branches on a rustic wooden table, warm bokeh lights in the background, inviting festive atmosphere, commercial photography"
      }
    ],
    "stream": false
  }'
```

### A/B Test Variations

```bash
# Generate multiple creative variations for A/B testing
VARIATIONS=(
  "A sleek smartwatch on a marble surface, dramatic side lighting, dark premium background, luxury product photography"
  "A sleek smartwatch on a person's wrist during a morning jog, natural sunlight, active lifestyle photography"
  "A sleek smartwatch flat-lay with a coffee cup, notebook, and plant, top-down view, clean modern aesthetic"
)

for VARIANT in "${VARIATIONS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"$VARIANT\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Workflow: Campaign Creative Pipeline

1. **Generate hero visual** — Create the primary ad image with product focus.
2. **Create lifestyle variants** — Generate contextual scenes showing the product in use.
3. **Produce platform variants** — Adapt the concept for different ad placements.
4. **Run A/B variations** — Generate multiple angles and styles for testing.
5. **Add copy and CTA** — Layer text and call-to-action in your design tool.

## Related Skills

- [AI Campaign Visuals](../ai-campaign-visuals/SKILL.md) — Multi-platform campaign visual sets
- [AI Landing Page Hero](../ai-landing-page-hero/SKILL.md) — Hero images for landing pages
- [AI Brand Kit](../ai-brand-kit/SKILL.md) — Consistent brand identity assets
- [Social Media Batch](../../workflows/social-media-batch/SKILL.md) — Batch generate for multiple platforms

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — High-quality commercial imagery
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic visuals
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast creative iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
