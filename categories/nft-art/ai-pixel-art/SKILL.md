---
name: ai-pixel-art
description: "Generate pixel art for games and NFTs using each::sense AI. Create retro-style pixel characters, environments, items, and sprites in various resolutions from 8-bit to 32-bit styles. Use for: pixel art, game sprites, retro art, 8-bit art, 16-bit art, pixel characters, game assets, NFT pixel art. Triggers: pixel art, 8-bit, 16-bit, retro pixel, game sprite, pixel character, pixel NFT, retro game art, pixel art generator, sprite art"
allowed-tools: Bash(curl *), WebFetch
---

# AI Pixel Art Generator

Generate pixel art for games, NFTs, and retro-style projects using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create pixel art of a medieval knight character standing idle with a sword and shield, 32x32 sprite style, limited color palette, clean pixel edges, retro RPG game aesthetic, transparent background feel, 16-bit era style"
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
        "content": "Create pixel art of a medieval knight character standing idle with a sword and shield, 32x32 sprite style, limited color palette, clean pixel edges, retro RPG game aesthetic, transparent background feel, 16-bit era style"
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
        "content": [
              {"type": "text", "text": "Convert this character design into pixel art: match the colors and proportions but render in a clean 16-bit pixel art style with visible pixel grid, game sprite aesthetic"},
              {"type": "image_url", "image_url": {"url": "https://example.com/character-concept.png"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Pixel Art Generation

- **Specify the pixel resolution** — "8-bit," "16-bit," "32x32," "64x64" to control the fidelity level.
- **Limit the color palette** — mention "limited palette," "NES palette," or "SNES colors" for authentic retro feel.
- **Describe clean edges** — use "sharp pixel edges," "no anti-aliasing," "crisp pixels" to avoid blurriness.
- **Mention the context** — "game sprite," "tile set," "pixel art portrait," or "scene diorama."
- **Use isometric cues** for environment pieces — "isometric pixel art," "top-down tileset."

## Examples

### Game Environment Tile

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Pixel art of a fantasy forest scene: tall pine trees, a winding dirt path, a small stream with stepping stones, mushrooms growing near the path, warm dappled sunlight, 16-bit SNES RPG environment style, rich greens and earth tones, top-down perspective"
      }
    ],
    "stream": false
  }'
```

### NFT Pixel Character

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A pixel art PFP for an NFT collection: a punk rock penguin with a green mohawk, gold chain necklace, and leather vest, solid magenta background, 24x24 CryptoPunks inspired style, minimal detail, iconic and recognizable, square format"
      }
    ],
    "stream": false
  }'
```

### Pixel Art Item Set

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A pixel art item sheet showing RPG inventory items arranged in a grid: a potion bottle, a golden key, a magic wand, a leather boot, a shield, and a gemstone, each item in its own cell, 16-bit style, clean pixel rendering, dark background grid"
      }
    ],
    "stream": false
  }'
```

### Pixel Art Scene Diorama

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "An isometric pixel art diorama of a tiny sushi restaurant: detailed interior with a sushi bar, chef preparing food, two customers sitting on stools, hanging lanterns, sliding door entrance, warm interior lighting, cozy Japanese aesthetic, 32-bit pixel art style"
      }
    ],
    "stream": false
  }'
```

## Workflow: Pixel Art Asset Pipeline

1. **Define the style guide** — Choose resolution, color palette, and visual era (8-bit, 16-bit, 32-bit).
2. **Generate character sprites** — Create the main characters in idle poses.
3. **Create environment tiles** — Produce terrain, buildings, and background elements.
4. **Design item and UI elements** — Generate inventory items, icons, and interface components.
5. **Assemble sprite sheets** — Arrange individual assets into organized sheets for game engines.

## Related Skills

- [AI NFT Collection](../ai-nft-collection/SKILL.md) — Full NFT collection generation
- [AI Generative Art](../ai-generative-art/SKILL.md) — Algorithmic art styles
- [AI Abstract Art](../ai-abstract-art/SKILL.md) — Abstract digital pieces
- [Text to Image](../../image/text-to-image/SKILL.md) — General image generation

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Detailed pixel art rendering
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative retro styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Quick sprite iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
