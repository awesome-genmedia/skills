---
name: presentation-slides
description: "Create slide deck visuals and backgrounds using each::sense AI. Generate professional presentation backgrounds, title slides, section dividers, and visual content slides for keynotes, pitch decks, webinars, and corporate presentations. Supports various styles from corporate to creative. Use for: presentation slides, keynote backgrounds, pitch deck visuals, slide design, webinar graphics, conference slides. Triggers: presentation slide, slide design, keynote visual, pitch deck, slide background, presentation graphic, powerpoint background, google slides, webinar slide, conference presentation, deck design"
allowed-tools: Bash(curl *), WebFetch
---

# Presentation Slides

Create professional slide deck visuals and backgrounds using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create a presentation title slide background. Smooth dark gradient from charcoal to midnight blue, subtle abstract wave pattern flowing across the bottom third, soft ambient light spots in the upper area, corporate and polished, 16:9 landscape format."
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
        "content": "Create a presentation title slide background. Smooth dark gradient from charcoal to midnight blue, subtle abstract wave pattern flowing across the bottom third, soft ambient light spots in the upper area, corporate and polished, 16:9 landscape format."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Match existing brand presentations or style guides:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a section divider slide background in the same visual style as this reference. Match the color palette and abstract elements, but create a variation suitable for a new section of the presentation, 16:9 landscape."
      }
    ],
    "image_urls": ["https://example.com/slide-reference.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Slide Types

| Type | Purpose | Layout Notes |
|------|---------|-------------|
| **Title Slide** | Opening/closing | Large central area for title, subtle background |
| **Section Divider** | Separate topics | Bold visual, minimal text area |
| **Content Slide** | Data and text | Clean background, max 60% visual |
| **Image Slide** | Full-bleed visual | Edge-to-edge image |
| **Quote Slide** | Feature a quotation | Atmospheric background with center focus |
| **Comparison** | Side-by-side | Split composition |

## Prompt Engineering Tips

### Keywords That Work

```
presentation slide background, clean and professional, subtle texture,
soft gradient, corporate aesthetic, large text area, 16:9 landscape,
minimal visual elements, consistent style, ambient lighting, polished
```

### Keywords to Avoid

```
busy patterns — text becomes unreadable
high contrast centers — conflicts with slide content
dark text areas — makes white text invisible
too many colors — distracting for audiences
```

### Prompt Structure

```
presentation [slide type] background for [context], [visual elements], [color palette], [mood], 16:9 landscape format
```

## Examples

### Startup Pitch Deck Title

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a startup pitch deck title slide. Bold gradient from deep violet to electric cyan, abstract ascending line graph made of glowing dots in the lower right, clean and futuristic, upper left area clear for company name, 16:9 landscape."
      }
    ],
    "stream": false
  }'
```

### Healthcare Conference Slide

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a healthcare presentation content slide background. Soft white to light teal gradient, faint DNA helix pattern along the right edge, clean and clinical aesthetic, professional medical feel, plenty of space for charts and bullet points, 16:9."
      }
    ],
    "stream": false
  }'
```

### Creative Agency Portfolio Slide

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a creative agency portfolio slide background. Matte black background with bold geometric color splashes in coral, turquoise, and gold concentrated in the upper right corner, modern and artistic, lower left reserved for project description text, 16:9."
      }
    ],
    "stream": false
  }'
```

### Annual Report Section Divider

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a corporate annual report section divider slide. Abstract cityscape made of rising bar charts transitioning into building silhouettes, navy blue and silver palette, professional and data-driven, centered composition with text space above and below, 16:9."
      }
    ],
    "stream": false
  }'
```

## Slide Design Best Practices

- **Consistency is king** — use the same background style throughout the deck
- **Left/right alignment** — place visuals on one side, leaving the other for text
- **Low-contrast backgrounds** — your text and data need to be the star, not the background
- **Dark backgrounds** with light text or **light backgrounds** with dark text, never mix
- **Generate a set** — create title, content, and divider variations in one session

## Workflow

```bash
# Step 1: Generate the title slide
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Presentation title slide background for an AI technology keynote. Deep space black with subtle neural network constellation pattern in soft blue, ethereal and intelligent, 16:9."
      }
    ],
    "stream": false
  }'

# Step 2: Generate a matching content slide
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Presentation title slide background for an AI technology keynote. Deep space black with subtle neural network constellation pattern in soft blue, ethereal and intelligent, 16:9."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Now create a matching content slide background. Same deep space black but with the neural network pattern faded to 20% opacity and pushed to the edges. Center should be very dark and clean for text and diagram overlays. Keep the same color scheme."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [Infographic Design](../infographic-design/SKILL.md) — Data visualizations for slides
- [Social Media Post](../social-media-post/SKILL.md) — Share slide content socially
- [OG Image Design](../og-image-design/SKILL.md) — Preview images for shared decks
- [Banner Ad Design](../banner-ad-design/SKILL.md) — Promotional banner graphics

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for text rendering in images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
