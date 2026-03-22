---
name: ai-caricature
description: "Generate caricature and cartoon versions of face photos using each::sense AI. Transform portraits into exaggerated, humorous, or stylized cartoon illustrations in various art styles including comic, manga, Disney, bobblehead, and editorial caricature. Use for: gifts, social media avatars, event entertainment, editorial illustration, profile pictures, merchandise. Triggers: caricature, cartoon face, cartoon portrait, funny portrait, exaggerated face, comic portrait, manga face, cartoon avatar, cartoon me, bobblehead, toon face, draw me as cartoon"
allowed-tools: Bash(curl *), WebFetch
---

# AI Caricature

Transform face photos into caricatures and cartoon portraits using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create a fun caricature of this person. Exaggerate their most prominent features in a friendly, humorous way. Colorful cartoon style with a white background."
      }
    ],
    "image_urls": ["https://example.com/headshot.jpg"],
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
        "content": "Create a fun caricature of this person. Exaggerate their most prominent features in a friendly, humorous way. Colorful cartoon style with a white background."
    }],
    extra_body={
        "image_urls": ["https://example.com/headshot.jpg"]
    }
)

print(response.choices[0].message.content)
```

### With Reference Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Turn this person into a caricature cartoon with exaggerated features, comic book style, vibrant colors"}],
    "image_urls": ["https://example.com/photo.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Caricature Styles

| Style | Description | Best For |
|---|---|---|
| **Classic Caricature** | Exaggerated features, hand-drawn look | Gifts, events, prints |
| **Comic Book** | Bold lines, halftone dots, superhero feel | Avatars, fun profiles |
| **Manga/Anime** | Big eyes, anime proportions, stylized hair | Social media, gaming |
| **Disney/Pixar** | 3D-rendered look, friendly, family-oriented | Profile pics, gifts |
| **Bobblehead** | Oversized head on tiny body | Humorous gifts, desk art |
| **Editorial** | Witty, political-cartoon style | Articles, commentary |
| **Chibi** | Ultra-cute, tiny body, huge head | Stickers, emotes |
| **Pop Art** | Bold colors, Warhol/Lichtenstein inspired | Wall art, merchandise |

## Prompt Engineering Tips

### Specify the Style Clearly

Different caricature styles produce very different results. Always name the style:

```
Create a [style] caricature of this person. [Feature emphasis]. [Color/background]. [Additional context].
```

### Feature Exaggeration

You can guide which features to exaggerate:

```
Exaggerate the big smile and dimples.
Emphasize the strong jawline and bushy eyebrows.
Make the eyes extra large and expressive.
```

### Context and Props

Adding context makes caricatures more fun:

```
Show them holding a laptop, wearing a chef hat, riding a skateboard,
playing guitar, in a superhero costume, sitting at a desk
```

## Examples

### Classic Party Caricature

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a classic hand-drawn style caricature of this person. Big exaggerated head on a small body, emphasize their smile and eyes. They are holding a paintbrush and standing next to an easel. Colorful, fun, white background."
      }
    ],
    "image_urls": ["https://example.com/friend-photo.jpg"],
    "stream": false
  }'
```

### Anime/Manga Style

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Transform this person into an anime character. Large expressive eyes, stylized spiky hair matching their hair color, manga shading, dynamic pose with sparkle effects. Keep their distinctive features recognizable in the anime style."
      }
    ],
    "image_urls": ["https://example.com/selfie.jpg"],
    "stream": false
  }'
```

### Pixar-Style 3D Character

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Turn this person into a Pixar-style 3D animated character. Slightly oversized head, big warm eyes, friendly expression, smooth stylized skin. Place them in front of a colorful background. Keep their hairstyle and clothing recognizable."
      }
    ],
    "image_urls": ["https://example.com/portrait.jpg"],
    "stream": false
  }'
```

### Pop Art Portrait

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a pop art portrait of this person in the style of Andy Warhol. Bold flat colors, high contrast, halftone dot pattern, four-panel grid with different color combinations: pink/yellow, blue/green, orange/purple, red/teal."
      }
    ],
    "image_urls": ["https://example.com/face-photo.jpg"],
    "stream": false
  }'
```

## Workflow: Custom Avatar Set

```bash
# Step 1: Generate the main caricature
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a clean cartoon avatar of this person. Flat vector illustration style, simplified features but recognizable, circular crop suitable for a profile picture, vibrant solid color background."
      }
    ],
    "image_urls": ["https://example.com/my-photo.jpg"],
    "stream": false
  }'

# Step 2: Generate variations for different platforms
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a cartoon avatar of this person in a professional style. Wearing a blazer, subtle smile, clean lines, minimal detail, dark blue background, suitable for a LinkedIn or business profile."
      }
    ],
    "image_urls": ["https://example.com/my-photo.jpg"],
    "stream": false
  }'

# Step 3: Fun version for gaming/social
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create an anime chibi version of this person. Oversized head, tiny body, big sparkly eyes, excited expression, wearing headphones and holding a game controller. Colorful pastel background with stars."
      }
    ],
    "image_urls": ["https://example.com/my-photo.jpg"],
    "stream": false
  }'
```

## Related Skills

- [AI Face Swap](../ai-face-swap/SKILL.md) — Swap faces between photos
- [AI Expression Editor](../ai-expression-editor/SKILL.md) — Change expressions before cartooning
- [AI Beauty Filter](../ai-beauty-filter/SKILL.md) — Enhance the source photo first
- [AI Aging Filter](../ai-aging-filter/SKILL.md) — Age effects on portraits

## Related Models

- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Style transformation with context
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic generation
- [flux-2-max](../../../models/flux-2-max/SKILL.md) — High-quality image generation
- [pulid-flux](../../../models/pulid-flux/SKILL.md) — Identity-preserving generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
