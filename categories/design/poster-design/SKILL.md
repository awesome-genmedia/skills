---
name: poster-design
description: "Design event, movie, and promotional posters using each::sense AI. Generate striking poster artwork for concerts, film releases, theater productions, conferences, art exhibitions, and marketing campaigns with bold compositions and typographic layouts. Use for: movie posters, event posters, concert posters, promotional posters, theater posters, conference graphics, art prints. Triggers: poster design, movie poster, event poster, concert poster, promotional poster, print design, poster art, flyer design, theater poster, film poster, gig poster"
allowed-tools: Bash(curl *), WebFetch
---

# Poster Design

Design striking event, movie, and promotional posters using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Design a vintage-style jazz concert poster. A saxophone player silhouette against a smoky spotlight, art deco geometric borders, warm amber and deep brown tones, aged paper texture, classic 1940s jazz club aesthetic, portrait orientation."
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
        "content": "Design a vintage-style jazz concert poster. A saxophone player silhouette against a smoky spotlight, art deco geometric borders, warm amber and deep brown tones, aged paper texture, classic 1940s jazz club aesthetic, portrait orientation."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Supply a style reference or previous poster from the same series:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Create a new concert poster in the same visual style as this reference. Same color palette and layout structure, but change the subject to a guitarist with stage lights, keep the vintage screenprint texture."},
              {"type": "image_url", "image_url": {"url": "https://example.com/previous-poster.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Poster Types

| Type | Style | Best For |
|------|-------|----------|
| **Movie Poster** | Cinematic, dramatic | Film releases, trailers |
| **Concert/Gig** | Bold, energetic | Live music events |
| **Minimalist** | Clean, symbolic | Art exhibitions, film festivals |
| **Retro/Vintage** | Screenprint, aged | Indie events, collectibles |
| **Typography** | Text-dominant | Conferences, talks |
| **Illustrated** | Hand-drawn, artistic | Theater, festivals |

## Prompt Engineering Tips

### Keywords That Work

```
poster design, bold composition, dramatic focal point, high contrast,
striking visual hierarchy, strong silhouette, cinematic framing,
screenprint style, large central image, border framing, portrait orientation
```

### Keywords to Avoid

```
detailed small text — AI text rendering is unreliable
too many subjects — posters need a single focal point
landscape orientation — most posters are portrait
realistic photograph — illustrated styles work better for posters
```

### Prompt Structure

```
[style] poster for [event type], [subject/scene], [artistic technique], [color palette], [mood], portrait orientation
```

## Examples

### Movie Poster

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a sci-fi movie poster. A lone astronaut standing before an enormous alien monolith on a barren red planet, dramatic low-angle perspective, the monolith reflects a distorted Earth in its surface, cinematic lighting with lens flare, dark and mysterious, portrait orientation."
      }
    ],
    "stream": false
  }'
```

### Music Festival Poster

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a psychedelic music festival poster. Swirling liquid art patterns in electric pink, turquoise, and gold, a central eye surrounded by radiating waves of color, 1960s concert poster style, hand-drawn illustration feel, portrait orientation."
      }
    ],
    "stream": false
  }'
```

### Conference Event Poster

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a modern tech conference poster. Abstract network of connected nodes forming the shape of a lightbulb, clean white background, navy blue and teal accents, minimal geometric style, corporate yet creative, portrait orientation with generous space for event details."
      }
    ],
    "stream": false
  }'
```

### Theater Production Poster

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a dramatic theater poster for a Shakespeare production. A crown shattering into golden fragments against a deep crimson velvet background, single spotlight from above, theatrical and regal, painterly illustration style, portrait orientation."
      }
    ],
    "stream": false
  }'
```

## Design Principles for Posters

- **One dominant element** — the poster should communicate its message from across the room
- **High contrast** — must be readable from a distance and at small sizes online
- **Visual hierarchy** — the eye should flow naturally from the main image to supporting elements
- **Leave text zones** — reserve the top 20% and bottom 30% for title and event details
- **Print considerations** — design at 300 DPI for physical printing (standard sizes: 18x24in, 24x36in, A2, A3)

## Workflow

```bash
# Step 1: Generate the poster concept
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Minimalist film noir poster. A detective silhouette standing under a streetlamp in rain, long shadow stretching forward, black and white with one accent of red from a neon sign reflection, portrait orientation."
      }
    ],
    "stream": false
  }'

# Step 2: Refine the composition
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Minimalist film noir poster. A detective silhouette standing under a streetlamp in rain, long shadow stretching forward, black and white with one accent of red from a neon sign reflection, portrait orientation."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Add rain streaks catching the light, make the shadow more prominent, and add a faint city skyline in the background fog. Keep the minimalist black and white with red accent."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [Book Cover Design](../book-cover-design/SKILL.md) — Cover art for publications
- [Banner Ad Design](../banner-ad-design/SKILL.md) — Promotional display ads
- [Social Media Post](../social-media-post/SKILL.md) — Share poster art on social platforms
- [Infographic Design](../infographic-design/SKILL.md) — Data-driven informational posters

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for text rendering in images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
