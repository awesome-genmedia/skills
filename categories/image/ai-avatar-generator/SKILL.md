---
name: ai-avatar-generator
description: "Generate custom AI avatars using each::sense AI. Create stylized profile pictures, gaming avatars, cartoon versions, pixel art characters, and fantasy personas from photos or text descriptions. Supports anime, 3D render, cartoon, pixel art, and painterly styles. Use for: profile pictures, gaming avatars, social media, Discord, Twitch, virtual identity, character design. Triggers: ai avatar, avatar generator, profile picture, create avatar, cartoon avatar, anime avatar, gaming avatar, discord avatar, twitch avatar, virtual persona, character avatar, custom avatar"
allowed-tools: Bash(curl *), WebFetch
---

# AI Avatar Generator

Create custom stylized avatars from photos or text descriptions using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create a stylized avatar: a warrior elf with silver hair and glowing blue eyes, wearing ornate golden armor, fantasy art style, bust portrait, vibrant colors, detailed, circular crop friendly"
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
        "content": "Create a stylized avatar: a warrior elf with silver hair and glowing blue eyes, wearing ornate golden armor, fantasy art style, bust portrait, vibrant colors, detailed, circular crop friendly"
    }]
)

print(response.choices[0].message.content)
```

### From a Reference Photo

Turn a real photo into a stylized avatar:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Transform this photo into a Pixar-style 3D cartoon avatar. Keep the likeness, exaggerate features slightly, big expressive eyes, smooth render, colorful background, friendly expression"
      }
    ],
    "image_urls": ["https://example.com/my-photo.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Avatar Styles

| Style | Keywords | Best For |
|-------|----------|----------|
| **Anime** | anime style, manga, cel shading, large eyes | Discord, social media |
| **3D Cartoon** | Pixar style, 3D render, smooth, stylized | Professional profiles |
| **Pixel Art** | pixel art, 8-bit, retro, sprite | Gaming, retro communities |
| **Flat Vector** | flat design, minimal, geometric | Business, apps |
| **Fantasy Art** | digital painting, RPG character, detailed | Gaming, D&D, communities |
| **Chibi** | chibi, super deformed, cute, oversized head | Stickers, fun profiles |
| **Watercolor** | watercolor portrait, soft edges, painterly | Artistic profiles |

## Examples

### Anime Avatar

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Anime style avatar of a young woman with cherry blossom pink hair in twin tails, violet eyes, wearing a school uniform with a red ribbon, soft pastel background, shoujo manga style, bust portrait"
      }
    ],
    "stream": false
  }'
```

### Gaming / RPG Avatar

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "RPG character avatar: a dwarven blacksmith with a long braided red beard, soot-covered leather apron, holding a glowing hammer, forge fire in the background, fantasy digital painting, portrait composition"
      }
    ],
    "stream": false
  }'
```

### Pixel Art Avatar

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "32x32 pixel art avatar of a cyberpunk hacker, neon green hair, dark sunglasses, black hoodie, retro 16-bit style, clean pixels, dark purple background"
      }
    ],
    "stream": false
  }'
```

### Photo to Cartoon

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Convert this person into a Disney-style cartoon character. Keep their hairstyle and facial features recognizable, add big expressive eyes, smooth skin, vibrant colors, simple clean background"
      }
    ],
    "image_urls": ["https://example.com/portrait.jpg"],
    "stream": false
  }'
```

## Prompt Tips

- **Specify "bust portrait" or "head and shoulders"** to get proper avatar framing
- **Add "circular crop friendly"** so the composition works in round profile picture frames
- **Include background color** to avoid busy backgrounds that distract at small sizes
- **Keep it centered** — avatars work best with the subject centered in frame
- **Mention "symmetrical face"** for a cleaner, more polished look

## Related Skills

- [AI Headshot Generator](../ai-headshot-generator/SKILL.md) — Professional headshots
- [AI Portrait Photo](../ai-portrait-photo/SKILL.md) — Studio-quality portraits
- [Text to Image](../text-to-image/SKILL.md) — General image generation
- [AI Image Editor](../ai-image-editor/SKILL.md) — Edit and refine avatars

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for photo-to-avatar conversion
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
