---
name: book-cover-design
description: "Design professional book and ebook covers using each::sense AI. Generate compelling cover art for novels, non-fiction, self-published books, audiobook covers, and digital publications across all genres including thriller, romance, sci-fi, fantasy, business, and memoir. Use for: book covers, ebook covers, audiobook art, kindle covers, novel artwork, self-publishing graphics. Triggers: book cover, ebook cover, novel cover, book design, cover art, kindle cover, audiobook cover, book jacket, book artwork, self-publishing cover, paperback cover"
allowed-tools: Bash(curl *), WebFetch
---

# Book Cover Design

Design professional book and ebook covers across every genre using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Design a book cover for a psychological thriller novel. A lone figure standing at the end of a foggy pier at night, dark moody atmosphere, desaturated blue-green tones, cinematic lighting from a single distant lamppost, ominous and suspenseful, portrait orientation."
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
        "content": "Design a book cover for a psychological thriller novel. A lone figure standing at the end of a foggy pier at night, dark moody atmosphere, desaturated blue-green tones, cinematic lighting from a single distant lamppost, ominous and suspenseful, portrait orientation."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide genre references or mood boards to guide the style:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a book cover in a similar artistic style to this reference but for a fantasy epic. Replace the subject with a towering crystal castle surrounded by floating islands, keep the painterly quality and dramatic sky."
      }
    ],
    "image_urls": ["https://example.com/style-reference.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Genre Style Guide

| Genre | Visual Style | Colors | Mood |
|-------|-------------|--------|------|
| **Thriller/Mystery** | Dark, high contrast | Deep blues, blacks, reds | Tension, suspense |
| **Romance** | Soft, warm, intimate | Pinks, golds, warm tones | Passion, longing |
| **Sci-Fi** | Futuristic, dramatic | Neon blues, purples, silvers | Wonder, technology |
| **Fantasy** | Epic, painterly | Rich jewel tones | Magic, adventure |
| **Literary Fiction** | Minimalist, symbolic | Muted, sophisticated | Contemplation |
| **Business/Self-Help** | Clean, bold | Strong single color + white | Authority, clarity |
| **Horror** | Gritty, unsettling | Dark reds, blacks, sickly greens | Dread, fear |
| **Children's** | Bright, whimsical | Primary colors, pastels | Joy, wonder |

## Prompt Engineering Tips

### Keywords That Work

```
book cover art, portrait orientation, cinematic composition, dramatic lighting,
painterly illustration, atmospheric mood, symbolic imagery, single focal point,
genre-appropriate, space for title text at top, author name area at bottom
```

### Keywords to Avoid

```
text on the cover — add title and author in design software
landscape orientation — books are portrait
cluttered composition — covers need visual hierarchy
photorealistic people — uncanny valley risk
```

### Prompt Structure

```
book cover for [genre] [type], [scene/subject description], [artistic style], [color palette], [mood/atmosphere], portrait orientation
```

## Examples

### Science Fiction Novel

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a sci-fi book cover. An astronaut floating in the rings of Saturn, seen from behind, tiny against the massive planet, stars and cosmic dust swirling around, deep space blues and warm amber planet light, epic and solitary, portrait orientation."
      }
    ],
    "stream": false
  }'
```

### Literary Fiction

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a minimalist literary fiction book cover. A single red door standing alone in an endless white desert, long shadow stretching toward the viewer, surreal and contemplative, muted earth tones with one pop of deep red, portrait orientation."
      }
    ],
    "stream": false
  }'
```

### Business Book

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a business book cover. Abstract geometric mountain peak made of interconnected data nodes and lines, navy blue background fading to white at the top, clean and professional, corporate yet inspiring, portrait orientation with ample space for a large title."
      }
    ],
    "stream": false
  }'
```

## Important: Text on Covers

AI image generators cannot reliably render text. Always plan to add title, subtitle, and author name in post-production.

**Recommended workflow:**
1. Generate the **cover artwork only** with each::sense
2. Add typography in a design tool (Canva, InDesign, Photoshop)
3. Use the upper third for the title and lower area for the author name

## Standard Cover Dimensions

| Format | Size |
|--------|------|
| Amazon Kindle | 1600 x 2560 px |
| Print Paperback (6x9) | 1800 x 2700 px |
| Audiobook | 3200 x 3200 px |
| Apple Books | 1400 x 1873 px |

## Workflow

```bash
# Step 1: Generate concept art
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Book cover for a fantasy novel. An ancient tree with roots made of glowing runes, mystical forest background, ethereal green and gold light filtering through mist, portrait orientation."
      }
    ],
    "stream": false
  }'

# Step 2: Refine the artwork
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Book cover for a fantasy novel. An ancient tree with roots made of glowing runes, mystical forest background, ethereal green and gold light filtering through mist, portrait orientation."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Darken the upper third of the image to create space for a light-colored title. Make the rune glow brighter and add fireflies in the mist."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [Poster Design](../poster-design/SKILL.md) — Promotional posters and prints
- [Packaging Design](../packaging-design/SKILL.md) — Physical product packaging
- [Social Media Post](../social-media-post/SKILL.md) — Book launch promo graphics
- [OG Image Design](../og-image-design/SKILL.md) — Link previews for book pages

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for text rendering in images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
