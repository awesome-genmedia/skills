---
name: ai-campaign-visuals
description: "Generate campaign visual assets across platforms using each::sense AI. Create coordinated imagery for multi-channel marketing campaigns spanning social media, email, web, and print. Use for: marketing campaigns, multi-platform visuals, social media campaigns, email graphics, promotional imagery. Triggers: campaign visuals, marketing campaign, multi-platform, campaign assets, social campaign, promotional visuals, campaign imagery, marketing visuals, cross-platform, campaign graphics"
allowed-tools: Bash(curl *), WebFetch
---

# AI Campaign Visuals Generator

Generate coordinated visual assets for multi-platform marketing campaigns using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create a campaign visual for a spring wellness product launch: a serene scene of botanical ingredients like lavender, eucalyptus, and chamomile arranged around a minimalist glass bottle on a stone surface, soft morning light, clean natural palette, editorial product photography"
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
        "content": "Create a campaign visual for a spring wellness product launch: a serene scene of botanical ingredients like lavender, eucalyptus, and chamomile arranged around a minimalist glass bottle on a stone surface, soft morning light, clean natural palette, editorial product photography"
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
        "content": "Using this product image as the centerpiece, create a campaign visual: place the product in a lifestyle context with complementary props, warm ambient lighting, social media ready composition, aspirational lifestyle mood"
      }
    ],
    "image_urls": ["https://example.com/product.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Campaign Visual Generation

- **Maintain visual consistency** — use the same color palette, lighting style, and mood across all prompts in a campaign.
- **Specify platform context** — mention "Instagram post," "email header," or "billboard" to influence composition.
- **Describe the campaign theme** — seasonal, product launch, awareness, or event-driven.
- **Include brand color cues** — "coral and navy palette," "earth tones," "monochrome" for cohesion.
- **Generate a hero visual first**, then create variations for each platform and touchpoint.

## Examples

### Social Media Campaign Post

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "An Instagram square post for a fitness app campaign: a dynamic action shot of a runner mid-stride on a city bridge at dawn, silhouetted against an orange and pink sky, motion blur on the background, energetic and motivational, high contrast photography"
      }
    ],
    "stream": false
  }'
```

### Email Campaign Header

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A wide email header image for a Black Friday sale campaign: elegant dark background with gold accents, scattered gift boxes and shopping bags in black and gold, subtle sparkle effects, luxurious and exclusive feel, landscape format with space for text overlay on the left"
      }
    ],
    "stream": false
  }'
```

### Event Promotion Visual

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A visual for a tech conference promotion: a futuristic auditorium filled with holographic displays and connected nodes of light, deep purple and cyan color scheme, sleek modern architecture, sci-fi atmosphere, wide angle perspective"
      }
    ],
    "stream": false
  }'
```

### Multi-Platform Batch

```bash
# Generate platform-specific variations for the same campaign
PLATFORMS=(
  "Instagram square post: a flat lay of organic coffee beans, a ceramic mug, and a French press on a dark wooden table, overhead view, moody warm lighting, artisan coffee campaign"
  "Facebook cover landscape: an artisan coffee roastery interior with warm industrial lighting, exposed brick walls, bags of coffee beans, cozy inviting atmosphere, wide panoramic shot"
  "Pinterest tall pin: a step-by-step visual of pour-over coffee being prepared, steam rising from a ceramic cup, close-up detail shot, warm amber tones, vertical composition"
)

for PLATFORM in "${PLATFORMS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"$PLATFORM\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Workflow: Multi-Channel Campaign

1. **Define campaign brief** — Theme, target audience, key message, brand colors.
2. **Generate hero image** — Create the primary visual that sets the campaign tone.
3. **Create platform variants** — Adapt the hero concept for each channel format.
4. **Generate lifestyle scenes** — Produce contextual images showing the product in use.
5. **Create video assets** — Animate key visuals for video placements.
6. **Review for consistency** — Verify that all assets feel cohesive across platforms.

## Related Skills

- [AI Ad Creative](../ai-ad-creative/SKILL.md) — Focused ad creative generation
- [AI Landing Page Hero](../ai-landing-page-hero/SKILL.md) — Hero images for campaign landing pages
- [Social Media Batch](../../workflows/social-media-batch/SKILL.md) — Automated multi-platform generation
- [AI Brand Kit](../ai-brand-kit/SKILL.md) — Brand identity for campaign consistency

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Premium commercial imagery
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative artistic direction
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Rapid concept exploration

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
