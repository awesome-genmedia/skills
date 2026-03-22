---
name: logo-design
description: "Generate professional logo designs using each::sense AI. Create wordmarks, icon logos, combination marks, monograms, mascots, emblems, and abstract logos for brands, startups, and businesses. Supports flat vector style, minimalist, vintage, 3D, and hand-drawn aesthetics. Use for: brand identity, startup logos, app icons, favicons, logo concepts, rebranding. Triggers: logo design, create logo, brand logo, logo generation, ai logo, logo maker, icon design, brand mark, logo concept, startup logo, app icon logo, monogram, emblem, mascot logo"
allowed-tools: Bash(curl *), WebFetch
---

# Logo Design

Generate professional logo concepts using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a flat vector logo for a coffee brand called Brewtiful. Minimalist style, single color, clean lines, white background."
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
        "content": "Generate a flat vector logo for a coffee brand called Brewtiful. Minimalist style, single color, clean lines, white background."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

You can send up to 4 images via `image_urls` for style reference, existing logo refinement, or inspiration:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Create a new logo inspired by this style but for a fintech company called PayFlow. Keep the minimalist aesthetic, use blue tones."},
              {"type": "image_url", "image_url": {"url": "https://example.com/reference-logo.png"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Logo Types

| Type | Description | Best For |
|------|-------------|----------|
| **Wordmark** | Styled company name | Short brand names (< 10 chars) |
| **Lettermark** | Initials only | Long company names |
| **Pictorial** | Recognizable icon/symbol | Universal brand recognition |
| **Abstract** | Geometric/non-literal shape | Tech companies, conceptual brands |
| **Mascot** | Character illustration | Friendly brands, food, sports |
| **Combination** | Icon + wordmark together | New brands needing both |
| **Emblem** | Text inside a symbol/badge | Traditional, authority brands |

## Prompt Engineering Tips

### Keywords That Work

```
flat vector logo, simple minimal icon, single color silhouette,
geometric logo mark, clean lines, negative space design,
line art logo, flat design icon, minimalist symbol, white background
```

### Keywords to Avoid

```
photorealistic logo — logos aren't photos
3D rendered logo — too complex, won't scale down
gradient logo — inconsistent results
logo with text "Company Name" — AI text rendering is unreliable
```

### Prompt Structure

```
flat vector logo of [subject], [style], [color constraint], [background], [additional detail]
```

## Examples

### Abstract Tech Logo

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a minimal abstract logo mark. Interconnected nodes forming a brain shape, line art style, single teal color, white background, tech startup aesthetic."
      }
    ],
    "stream": false
  }'
```

### Pictorial Nature Logo

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a flat vector logo of a fox head in profile. Geometric faceted style, orange and white, minimal clean lines, white background, negative space design."
      }
    ],
    "stream": false
  }'
```

### Mascot Logo

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a friendly cartoon owl mascot logo. Simple flat illustration, wearing graduation cap, purple and gold colors, white background, clean vector style."
      }
    ],
    "stream": false
  }'
```

## Important: AI Text Limitation

AI image generators cannot reliably render text in logos. Letters will be distorted or misspelled.

**Recommended workflow:**
1. Generate the **icon/symbol only** with each::sense
2. Add text/wordmark in a design tool (Figma, Canva, Illustrator)

## Scalability Checklist

A good logo must work at every size:

- Recognizable as a 16px favicon
- Works in single color (black on white)
- Works inverted (white on black)
- No tiny details that disappear at small sizes
- Clear silhouette without color

## Color Guidelines

- Maximum 2-3 colors for the primary logo
- Must work in single color
- Blue → trust, professional (finance, tech)
- Red → energy, urgency (food, retail)
- Green → growth, nature (health, sustainability)
- Black → premium, elegant (fashion, luxury)

## Iteration Workflow

```bash
# Step 1: Generate broad concepts
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a flat vector logo of a lighthouse, minimal geometric, single color, white background"
      }
    ],
    "stream": false
  }'

# Step 2: Refine the best concept (use the conversation to iterate)
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a flat vector logo of a lighthouse, minimal geometric, single color, white background"
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Make it more geometric with radiating light beams, navy blue single color"
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [Social Media Post](../social-media-post/SKILL.md) — Create branded social content
- [Business Card Design](../business-card-design/SKILL.md) — Apply your logo to cards
- [App Icon Design](../app-icon-design/SKILL.md) — Adapt logo for app stores
- [Banner Ad Design](../banner-ad-design/SKILL.md) — Use logo in ad creatives

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for text rendering in images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
