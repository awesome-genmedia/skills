---
name: social-media-batch
description: "Batch generate social media content for multiple platforms using each::sense AI. Create platform-optimized visuals for Instagram, Facebook, LinkedIn, Twitter/X, Pinterest, and TikTok from a single content concept. Produce posts, stories, covers, and thumbnails in appropriate formats. Use for: social media content, multi-platform posting, batch content creation, social media management, content calendar visuals. Triggers: social media batch, multi-platform, social content, batch generate, social media posts, content batch, platform content, social batch, cross-platform content, social media kit"
allowed-tools: Bash(curl *), WebFetch
---

# Social Media Batch Generator

Batch generate social media content for multiple platforms from a single concept using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Generate for Multiple Platforms

```bash
# Instagram Square Post
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "An Instagram square post for a sustainable fashion brand: a model wearing an oversized linen blazer standing in a sunlit wheat field, earth tones, warm golden hour light, minimal and elegant, fashion editorial photography, square composition"
      }
    ],
    "stream": false
  }'

# Instagram Story / TikTok (vertical)
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "An Instagram Story for a sustainable fashion brand: close-up of hands touching linen fabric, wheat field blurred in background, warm golden tones, vertical tall format, space at top and bottom for text overlay, fashion storytelling"
      }
    ],
    "stream": false
  }'

# LinkedIn / Facebook Cover (landscape)
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A LinkedIn cover banner for a sustainable fashion brand: a wide panoramic view of a linen garment workshop with natural materials, warm natural light, earth tones, artisanal craftsmanship visible, wide landscape format with space for company name on the left"
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

BRAND_CONTEXT = "sustainable fashion brand, earth tones, warm golden light, linen and natural materials"

platforms = {
    "instagram_post": f"Instagram square post: a model in an oversized linen blazer in a sunlit wheat field, {BRAND_CONTEXT}, fashion editorial, square composition",
    "instagram_story": f"Instagram Story vertical: close-up of hands on linen fabric, wheat field background, {BRAND_CONTEXT}, tall format, text space at top and bottom",
    "facebook_cover": f"Facebook cover: wide panoramic artisan workshop with natural materials, {BRAND_CONTEXT}, landscape format, text space on left",
    "linkedin_post": f"LinkedIn post: flat lay of sustainable garments with raw material samples, {BRAND_CONTEXT}, professional editorial, square format",
    "pinterest_pin": f"Pinterest tall pin: full outfit shot in a golden field, {BRAND_CONTEXT}, vertical composition, aspirational lifestyle",
    "twitter_header": f"Twitter/X header: minimal abstract pattern of wheat and linen textures, {BRAND_CONTEXT}, wide landscape format"
}

for platform, prompt in platforms.items():
    print(f"Generating {platform}...")
    response = client.chat.completions.create(
        model="eachsense/beta",
        messages=[{"role": "user", "content": prompt}]
    )
    print(f"  {platform}: {response.choices[0].message.content}")
    print("---")
```

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Social Media Batch Generation

- **Reuse a brand context string** — Include the same brand description, colors, and mood in every prompt.
- **Specify format per platform** — "square" for Instagram/LinkedIn posts, "vertical tall" for Stories/Reels/TikTok, "wide landscape" for covers.
- **Leave text space** — Indicate where text overlays will go so the image composition accommodates them.
- **Vary the composition** — Different crops and angles of the same concept for each platform.
- **Batch by content theme** — Generate a full week of content around one theme in a single session.

## Examples

### Product Launch Batch

```bash
PRODUCT="a new organic skincare serum in a minimalist glass bottle"
STYLE="soft pastel pink and sage green, clean minimal, natural beauty"

PROMPTS=(
  "Instagram square: $PRODUCT surrounded by fresh botanical ingredients, overhead flat lay, $STYLE"
  "Instagram Story vertical: $PRODUCT held in a hand against a soft blurred nature background, close-up, $STYLE, text space top and bottom"
  "Facebook post: $PRODUCT on a marble surface with morning light and a small plant, lifestyle, $STYLE"
  "Pinterest tall pin: step-by-step skincare routine flat lay with $PRODUCT as the hero, vertical, $STYLE"
)

for PROMPT in "${PROMPTS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"$PROMPT\"}],
      \"stream\": false
    }"
  echo "---"
done
```

### Weekly Content Calendar

```bash
# Monday motivation, Wednesday tips, Friday feature
DAYS=(
  "Monday motivation post: sunrise over a yoga mat on a balcony, inspiring morning energy, warm light, square format, wellness brand aesthetic"
  "Wednesday tips post: a clean organized desk with a planner, coffee, and a plant, productive workspace, overhead view, square format, wellness brand aesthetic"
  "Friday feature post: a group of friends laughing together in a park at golden hour, community and connection, candid lifestyle photography, square format, wellness brand aesthetic"
)

for DAY in "${DAYS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"$DAY\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Workflow: Social Media Content Pipeline

1. **Define the content theme** — Product launch, campaign, seasonal, or evergreen.
2. **Create the brand context string** — Colors, mood, and style keywords.
3. **Map platform requirements** — List each platform with format and composition needs.
4. **Batch generate** — Run all platform variants with consistent branding.
5. **Add copy and CTAs** — Overlay text, hashtags, and calls-to-action in a design tool.
6. **Schedule and publish** — Queue content in your social media management tool.

## Related Skills

- [AI Campaign Visuals](../../marketing/ai-campaign-visuals/SKILL.md) — Campaign visual assets
- [Brand Asset Pipeline](../brand-asset-pipeline/SKILL.md) — Complete brand asset generation
- [AI Ad Creative](../../marketing/ai-ad-creative/SKILL.md) — Paid ad creative visuals
- [Product Media Suite](../product-media-suite/SKILL.md) — Product-focused media generation

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — High-quality social media imagery
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative visual styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast batch processing

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
